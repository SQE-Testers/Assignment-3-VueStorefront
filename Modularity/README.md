
# 1. Micro-Services
Microservices architecture is a concept of building an application based on breaking it into multiple modules. Each module has its own specific responsibilities but communicates with others to form a unified system. This approach provides freedom of development and choice of tools (technology language, framework) within each application.

![Micro Services](https://i.imgur.com/ELcmMjy.png)

## Micro-Services Example in Vue StoreFront Code

![GitHub picture of packages](https://i.imgur.com/gEN73AD.png)

In this image, we can see Vue StoreFront has
micro-services requirements as they divided the services in many micro ones which has its own responsibilities
but communicate with others to form a unified system.
## 2. Modular Structure
Every project has its own requirements and each team has its own way of working, so this is not THE guide on how to structure your Vue project; it’s more of a source of ideas and good practices that you can follow to improve your code maintainability:

- Source code navigation
- Testability
- Monitoring + Observability
- Debugging
- Collaboration

## Module-based, not file-based structure

When starting a new Vue project, the easiest way to go is vue-cli project structure, which somehow forces you to group your files by type: components, services, helpers with a few odd exceptions, such as the router and the store. This structure is not wrong — for small applications, it’s very easy to maintain, but for mid-size/large applications there are a few downsides:
- The source code navigation is not simple: imagine the amount of files inside the components folder, and knowing the purpose of each one — same for any other file type
- Debugging can be very time-consuming: you’d need to jump file-to-file and draw a mental map of how a simple process works to get to the root cause of a bug.

A better alternative is to structure your project using old-fashioned modules and to think of each module as a small vue-cli project, decreasing the downsides explained above, so you get something like this:


![Micro Services](https://i.imgur.com/tln2Yys.png)


## 3. Class/Components Reusability

Vue StoreFront is doing each functionality in a separate module and whenever they need that module to be there they just simply "import" that module.

- Example:
 ![Micro Services](https://i.imgur.com/HnZcfKJ.png)
All these imports are using the other modules which that file needed.

## 4. Extensibility

## Introduction:

Extensibility is one of the key selling points of many frameworks, and Vue Storefront is no exception. There is a good reason for this - at some point, most projects need to extend the base of the framework to meet their needs, be it with a ready-to-use or a custom plugin. Well-thought-out extensions or plugins system enables flexibility to meet the demands of the most, even very diverse projects. On this page, we will discuss possible ways to extend Vue Storefront if the basic features are not enough for your project.

First, you should consider which part of the application you need to extend - frontend, backend, or both. Depending on your needs, you may need to extend:

- Vue.js
- Nuxt.js
- Server Middleware

## Extending Vue.js
Plugins allow adding global-level functionalities to Vue.js, such as components, methods, helpers, or directives. These mainly extend the frontend portion of the application and can be divided into two categories:
- UI plugins
- Non-UI plugins

### Vue.js UI plugins
UI plugins extend how the application looks or behaves on user interactions. They include plugins that add support for:
- Event handling.
- Responsive design, resizing, scrolling, and animations.
- Handling forms and validation.
- Routing, lazy loading, lazy hydration, meta tags.

### Vue.js non-UI plugins
Non-UI plugins extend how the application works under the hood or handles state and storage. They include plugins that add support for:
- Making HTTP requests.
- Internationalization (i18n).
- Custom events.
- Persistence (storage).
- State management.
- Web workers.


# 5. Linters for better code quality

The first linters used to check the source code and find potential optimizations for compilers. But, over the years, many other checks and analysis would be included in the process of linting.

The usage of linters has also helped many developers to write better code for not compiled programming languages. As there is not compiling time errors, finding typos, syntax errors, uses of undeclared variables, calls to undefined or deprecated functions, for instance, helping developers to fix it faster and reduce bugs before execution.


## Performance improvements:

Every experienced developer knows not only the importance of performing software but many tricks that improve it. The problem is: what about newcomers? How can you pass this knowledge forward? Even senior programmers can miss a technique or two. So, why not let an automation software do it for you?

Did you know that in CSS, the universal selector (*) may slow down a page loading time? Or that unqualified attribute selectors have the same performance characteristics as the universal selector? Avoiding them is good practice.

Many linters include a performance check. They can add different kinds of performance improvements for experienced and newcomers developers. CSSLint is just an example.

