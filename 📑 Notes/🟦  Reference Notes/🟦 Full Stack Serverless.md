- **Type:** #[[🟦 Reference Note]] #[[📥 Inbox]] | #[[Full Stack]] #Serverless #[[AWS Amplify]] #React
- **Source:** https://learning.oreilly.com/library/view/full-stack-serverless/9781492059882/
- **Author:** [[Nader Dabit]]
- **Codebase:** https://github.com/dabit3/full-stack-serverless-code
- **Summary:**
    - 
- **Literature Notes:**
    - 
- ### Highlights first synced by #Readwise [[March 12th, 2021]]
    - # 1. Full Stack Development in the Era of Serverless Computing
        - The Amplify CLI provides an easy entry point for developers wanting to build applications on AWS. The CLI allows developers to create, configure, update, and delete cloud services directly from their frontend environment.
        - The CLI has a host of commands that allow you to create, update, configure, and remove services without having to leave your frontend environment. You can also spin up and deploy new environments using the CLI in order to test out new features without affecting the main environment.
        - Once you’ve created and deployed features using the CLI, you can then use the Amplify client libraries to begin interacting with the services from your client-side application.
        - Amplify client
        - The Amplify client is a library made especially to provide an easy-to-use API for JavaScript applications that need to interact with AWS services. Amplify also has client SDKs for React Native, native iOS, and native Android.
        - The approach that the Amplify client takes is to provide a higher level of abstraction and bake in best practices to provide a declarative, easy-to-use API. At the same time, it gives you full control over the interactions with your backend. It’s also built especially with the client in mind, with features like WebSocket and GraphQL subscription support. It utilizes localStorage for the browser and AsyncStorage for React Native to store security tokens like IdTokens and AccessTokens to persist user authentication.
        - The Amplify Framework does not support the entire suite of AWS services; instead, it supports a subset of them with almost all of them falling into the category of serverless.
        - Amplify was created as an end-to-end solution to fill a previously unfilled gap, but it also encompasses a new way to build full stack cloud applications.
        - AWS AppSync
        - AWS AppSync is a managed API layer that uses GraphQL to make it easy for applications to interact with any data source, REST API, or microservice.
        - The API layer is one of the most important parts of an application. Modern applications typically interact with a large number of backend services and APIs; things like databases, managed services, third-party APIs, and storage solutions, among others.
        - GraphQL, a technology created and open sourced by Facebook, offers an especially good abstraction for creating an API gateway. GraphQL introduces a defined and consistent specification for interacting with APIs in the form of three operations: queries (reads), mutations (writes/updates), and subscriptions (real-time data). These operations are defined as part of a main schema that also provides a contract between the client and the server in the form of GraphQL types. GraphQL operations are not bound to any specific data source, so you as a developer are free to use them to interact with anything from a database, an HTTP endpoint, a microservice, or even a serverless function.
        - Typically, when building a GraphQL API, you need to deal with building, deploying, maintaining, and configuring your own API. With AWS AppSync, you can instead offload the server and API management as well as the security to AWS.
        - Modern applications often also have concerns such as real-time and offline support. Another benefit of AppSync is that it has built-in support for offline (Amplify client SDKs) as well as real time (GraphQL subscriptions) to enable developers to build these types of applications.
        - Introduction to the AWS Amplify CLI
        - Installing and Configuring the Amplify CLI
        - To get started, you first need to install and configure the Amplify CLI:
        - ~ npm install -g @aws-amplify/cli
        - To create a new user and configure the CLI, you’ll run the configure command:
        - ~ amplify configure
        - Initializing Your First Amplify Project
        - Now that the CLI has been installed and configured, you can create your first project. This step is usually done within the root of your client application. Since you will be using React for most of this book, we’ll start by initializing a new React project:
        - ~ npx create-react-app amplify-app
        - Now you need to install the Amplify that you’ll be using on the client. The libraries you’ll be using are AWS Amplify and AWS Amplify React for the React-specific UI components:
        - ~ npm install aws-amplify @aws-amplify/ui-react
        - Next, you can create an Amplify project. To do so, you’ll run the init command:
        - ~ amplify init
        - When the initialization is complete, you will have two additional resources created for you in your project: a file called aws-exports located in the src directory and a folder named amplify located in your root directory.
        - The aws-exports file is a key-value pairing of the resource categories created for you by the CLI along with their credentials.
        - Creating and Deploying Your First Service
        - To create a new service, you can use the add command from Amplify:
        - ~ amplify add auth
        - Deleting the Resources
        - To remove an individual feature, you can run the remove command:
        - ~ amplify remove auth
        - To delete an entire Amplify project along with all of the corresponding resources that have been deployed in your account, you can run the delete command:
        - ~ amplify delete
    - # Chapter 2. Getting Started with AWS Amplify
        - At the core of most applications is the data/API layer. This layer could look like many things. In the serverless world, this usually will be composed of a combination of API endpoints and serverless functions.
        - There are two main ways of creating APIs with Amplify:



A combination of Amazon API Gateway and a Lambda function


A GraphQL API connected to some type of data source (database, Lambda function, or HTTP endpoint)
        - API Gateway is an AWS service that allows you to create API endpoints and route them to different services, often via a Lambda function. When you make an API call, it will route the request through API Gateway, invoke the function, and return the response.
        - Using the Amplify CLI, you can create both the API Gateway endpoint as well as the Lambda function; the CLI will automatically configure the API to be able to invoke the Lambda function via an HTTP request.
        - In this chapter, you’ll create your first full stack serverless app that will interact with a serverless function via an API Gateway endpoint. You’ll use the CLI to create an API endpoint as well as a serverless function, and then use the Amplify client libraries to interact with the API.
        - At first, the app will fetch a hardcoded array of items from the function. You’ll then learn how to update the function to make an asynchronous HTTP request to another API to retrieve data and return it to the client.
        - Creating and Deploying a Serverless Function
        - At the core of many serverless applications are serverless functions. Serverless functions run your code in stateless compute containers that are event-driven, short-lived (may last for one invocation), and fully managed by the cloud provider of your choice. These functions scale seamlessly and do not require any server operations.
        - While most people think of serverless functions as being invoked or triggered by an API call, these functions can also be triggered by a variety of different events. In addition to HTTP requests, a few popular ways to invoke a serverless function are via an image upload to a storage service, a database operation (like create, update, or delete), or even from another serverless function.
        - Now that you know about serverless functions, let’s take a look at how you can create a serverless function and hook it up to an API that will invoke it from an HTTP request.
        - Creating the React Application and Installing the Dependencies
        - To get started, you’ll first need to create the React application. To do so, you can use npx:
        - ~ npx create-react-app amplify-react-app
~ cd amplify-react-app
        - Next, you will need to install the dependencies. For this app, you’ll only need the AWS Amplify library:
        - ~ npm install aws-amplify
        - After installing the dependencies, you can now initialize a new Amplify project in the root of the React application:
        - ~ amplify init
        - Creating a New Serverless Function with the Amplify CLI
        - To create the function, run the following command:
        - ~ amplify add function
        - You should now see a new subfolder located within the amplify directory at amplify/backend/function/cryptofunction.
        - Walking Through the Code
        - When you created this resource, a new folder in amplify/backend was created named function.
        - In the cryptofunction folder, you will see a couple of configuration files as well as an src directory where the main function code is located.
        - Serverless functions are essentially just encapsulated applications running on their own.
        - Next, have a look at the function entry point located at src/index.js, in the cryptofunction folder. In this file you’ll see that there is a function called exports.handler. This is the entry point for the function invocation. When the function is invoked, this is the code that is run.
        - You can handle the event directly in this function if you would like, but since you will be working with an API, a more useful way to do this is to proxy the path into an express app with routing
        - The serverless express framework provides an easy way to do this and has been built into the function boilerplate for you.
        - Creating the /coins Route
        - Now that you have seen how the application is structured, let’s create a new route in app.js and return some data from it. The route that you will be creating is a /coins route. This route will be returning an object containing a coins array.
        - Adding the API
        - Now that the function is created and configured, let’s put an API in front of it so you can trigger it with an HTTP request.
        - To do this, you will be using Amazon API Gateway. API Gateway is a fully managed service that enables developers to create, publish, maintain, monitor, and secure REST and WebSocket APIs. API Gateway is one of the services supported by both the Amplify CLI as well as the Amplify client library.
        - Creating a New API
        - To create the API, you can use the Amplify add command. From the root of the project, run the following command in your terminal:

~ amplify add api
        - Deploying the API and the Lambda Function
        - Now that the function and API have both been created, you need to deploy them to your account to make them live. To do so, you can run the Amplify push command:

~ amplify push
        - You can use the Amplify CLI status command at any time to see the current status of your project. The status command will list out all of the currently configured services in your project and give you the status for each of them:
        - Interacting with the New API
        - Now that the resources have been deployed, you can begin interacting with the API from the React application.
        - Configuring the Client App to Work with Amplify
        - To use the Amplify client library in any application, there is a base configuration that needs to be set up, usually at the root level. When you create the resources, the CLI populates the aws-exports.js file with information about your resources. You will use this file to configure the client application to work with Amplify.
        - The Amplify Client API Category
        - The Amplify client library has various API categories that can be imported and used for various types of functionality, including Auth for authentication, Storage for storing items in S3, and API for interacting with REST and GraphQL APIs.
        - API has various methods available—including API.get, API.post, API.put, and API.del—for interacting with REST APIs, and API.graphql for interacting with GraphQL APIs.
        - When working with a REST API, API takes in three arguments:

API.get(apiName: String, path: String, data?: Object)
        - apiName

The name given when you create the API from the command line. In our example, this value would be cryptoapi.
        - path

The path that you would like to interact with. In our example, we created /coins, so the path would be /coins.
        - data

This is an optional object containing any properties you’d like to pass to the API, including headers, query string parameters, or a body.
        - In our example, the API call is going to look like this:

API.get('cryptoapi', '/coins')
        - Calling the API and Rendering the Data in React
        - Updating the Function to Call Another API
        - Next, you’ll update the function to call another API, the CoinLore API, that will return dynamic data from the CoinLore service.
        - Installing Axios
        - The first thing you need to do is install the Axios package in your function folder in order to send HTTP requests from the function.
        - Updating the Function
        - Next, update the /coins route
        - In the req parameter, there is an apiGateway property that holds the event and the context variables. In the function just defined, there is a check to see if this event exists as well as the queryStringParameters property on the event. If the queryStringParameters property exists, we use those values to update the base URL with the parameters. Using queryStringParameters, the user can specify the start and limit values when querying the CoinLore API.
        - Updating the Client App
        - Now that you have updated the function, let’s update the React app to give the user the option to specify the limit and start parameters.
        - To do so, you’ll need to add fields for user input and give the user a button to trigger a new API request.
