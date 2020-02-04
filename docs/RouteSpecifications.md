## Route Specifications

### Section 1. Definitions

1. **BaseUrl** 

   Is a base address for a set of REST APIs. It can contains paths or not.
   It means it's not necessary to BaseUri to be just to the authority.extension part of a Url.
   
2. **Schema**

   Is the schema of **BaseUrl**. 
   
3. **Path**

   Is the remaining part of a Url after the authority.extension part.
   
4. **Route**

   Is the full address - maybe with dynamic parts - of a Url.
   
### Section 2. Specifications

#### 1. BaseUrl detection

1. Each interface can be annotated with an attribute which defines the BaseUrl for all contained APIs.
2. If an interface doesn't provide the BaseUri explicitly, the BaseUrl would be 
searched in a configuration file with that interface's name as key.
3. If searching the BaseUrl for a not-annotated interface in the configuration file failed,
if the request is getting made in an AspNet context, the current request's authority.extension
part will be used as BaseUrl.
4. Each API - a method wrapped in an interface - can has its own BaseUrl which will override
the inherited value from parent interface.
4. If above approaches weren't successful, an exception should be thrown.  

### 2. Schema

1. The library supports `http` and `https` schemas.
2. Any route from anywhere - interface annotation, method annotation, configuration file,
etc. - can start with one of supported schemas. If found any, that will be used as BaseUrl.

### 3. Path detection

1. Paths are valid only on methods.
2. Any method can have it's own annotated path, or an equivalent key in the configuration file
that holds the path (path-template perhaps) for method.
3. Paths contains URL-Parameters (query string parameters).
4. Path parameters can be produced from:
   - Constant values as method parameters 
   - Some `Func<>`s as method parameters
5. Path parameter detection follows some sort of route-templating.

### 4. Route

1. The combination of BaseUrl and Path and path-parameters will build the Route.