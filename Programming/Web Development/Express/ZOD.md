- A request schema validation tool
- Found at https://zod.dev/

## Schemas

- Can be used to validate incoming request objects when used in [[Custom Middleware]]
- If the incoming request does not match the fields needed or the types of those fields it will be rejected

```typescript
export const CafeDbSchema = z.object({
  id: z.coerce.number(),
  name: z.string().min(3),
  description: z.string().min(1),
  longitude: z.coerce.number().min(-180).max(180),
  latitude: z.coerce.number().min(-90).max(90),
});
```

- You can extend and create new schemas from existing ones in a similar way to how you do it in typescript

```typescript
export const CreateCafeRequestSchema = z.object({
  body: CafeDbSchema.omit({ id: true }),
});
```

- To use this you must create a [[Custom Middleware]] function like the one below 

```typescript
const validate =
  (schema) => (req: Request, res: Response, next: NextFunction) => {
    try {
      console.log(req.body);
      const parsed = schema.parse({
        body: req.body,
        query: req.query,
        params: req.params,
      });
      console.log(parsed);
      next();
    } catch (error) {
      return res.status(400).json({
        status: "fail",
        errors: JSON.parse(error.message).map((err) => ({
          path: err.path,
          message: err.message,
        })),
      });
    }
  };
```

- Which you will then use as a [[Custom Middleware]] function in your routes either before or after your [[Controllers]]

```typescript
cafeRouter.post("/addCafe", validate(CreateCafeRequestSchema), addNewCafe);
```

- Doing this prevents you having to write validation functions for each service

## Type Inference
- When using ZOD with typescript, you can easily generate usable [[Custom Types and Interfaces]] from the schema so you don't have to have to update your types in multiple places

```typescript
export const CafeDbSchema = z.object({
  id: z.coerce.number(),
  name: z.string().min(3),
  description: z.string().min(1),
  longitude: z.coerce.number().min(-180).max(180),
  latitude: z.coerce.number().min(-90).max(90),
});

export type Cafe = z.infer<typeof CafeDbSchema>;
```