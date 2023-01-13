# Creating a full stack app using Nx, React and Springboot

## Initialize the monorepo

```
npx create-nx-workspace@latest my-monorepo --preset=ts --nxCloud=false
```

There, we will choose `package-based monorepo` and won't enable cloud builds.

## Initialize the react front-end

To create the react app, we're going to use the Nx generator:

```
npm install --save-dev @nrwl/react
nx generate @nrwl/react:app front-end --style=css --routing --linter=eslint --unitTestRunner=none --e2eTestRunner=none --bundler=webpack
```

If required, install the missing dependency:

```
npm i @nrwl/web
```

You can then run the front-end with:

```
nx serve front-end
```

## Initialize the springboot back-end

Using [Spring Initializr](https://start.spring.io/), we can create a new project with the following dependencies:

- Spring Boot DevTools DEVELOPER TOOLS
- Lombok DEVELOPER TOOLS
- Spring Web WEB
- Spring Security SECURITY
- MySQL Driver

To do so in command line, we can use:

```
npm i --save-dev @nxrocks/nx-spring-boot
nx generate @nxrocks/nx-spring-boot:project backend --dependencies='lombok,web,devtools,security' --groupId=io.github.me --packageName=io.github.me.backend --projectType=application --buildSystem=maven-project --packaging=jar --artifactId=backend --language=java --description=backend --skipFormat
```

You can then run the backend with:

```
nx serve backend
```