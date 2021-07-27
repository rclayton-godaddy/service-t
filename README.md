# Service T


```typescript

type Deps = {

  fooService: () => true
}

type Config = {
  foo: string,
}

const server = new Webserver<WebContext<Config, Deps>>()
  .config(async (env) => {
    return {
      foo: 'bar',
    }
  })
  .deps(async () => {
    return {
      fooService: asValue(() => true),
    }
  })
  .route({
    method: 'GET',
    path: '/foo',
    handler(req, res, next, deps) {
      res.json(deps.fooService());
    }
  })
  .initialize();
  
await server.start();  


```


