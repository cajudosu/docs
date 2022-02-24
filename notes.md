Notes
=====

**Dependency Injection (DI) / Inversion of Control (IoC)**

- Good article: https://martinfowler.com/articles/injection.html
- General idea:
  - Express dependencies only to interfaces (NOT to explicit classes)
  - Make implementations of these interfaces configurable
  - Mapping of interfaces to configured implementations is held by a container

**Autofac IoC container**

- Create a ContainerBuilder and register your components
- Typical line that would register some type `SomeType` as some service `IService`

```csharp
var builder = new ContainerBuilder();
builder.RegisterType<SomeType>.As<IService>();
```

- Further reading: https://autofac.readthedocs.io/en/latest/getting-started/index.html

