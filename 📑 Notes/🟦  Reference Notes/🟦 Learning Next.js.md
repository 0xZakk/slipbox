- **Type:** #[[__ 🟦  Reference Note]] | #[[Next.js]]
- **Source:** https://nextjs.org/learn/basics/create-nextjs-app 
- **Project(s):** 
- **Summary:** 
- **Highlights:**
    - **Create a Next.js App**
        - Building a web application with React requires making a lot of decisions about how you want to build the code. You have to think through how you're going to bundle the code and transform or compile it, how to optimize it for production, whether or not you want to pre-render some pages for performance or SEO, and how you're going to connect React to your data store.
        - Frameworks exist to make some of these decisions for you. These frameworks need to have the right abstractions for you and have to have a good developer experience.
        - **Next.js: The React Framework**
            - Next.js is a React framework that tries to solve some of these problems and help you and your dev team.
            - Some of the features that Next.js provides are:
                - Page-based routing system that also supports dynamic routes
                - Pre-rendering with both static generation and server-side rendering
                - Che build process will do automatic code-splitting for you so your pages load faster
                - Client-side routing that also performs prefetching
                - Built in support for Sass and any [[CSS-in-JS]] library
                - A development environment that includes fast refresh
                - API routes to build API endpoints with serverless functions
        - **Setup**
            - The first step is getting next installed and setup.
            - At the moment, Next requires at least Node version 10.13
            - Create a Next App:
                - The following command will create a Next.JS app using [this template](https://github.com/vercel/next-learn-starter/tree/master/learn-starter):
                - ```javascript

npx create-next-app nextjs-blog \
  --use-npm \
  --example "https://github.com/vercel/next-learn-starter/tree/master/learn-starter"
```
                - This command uses the `create-next-app` command to bootstrap a Next.js app for you.
                - To run the Next.js server, use `npm run dev`
            - That's it! You should not be able to go to `localhost:3000` and see your application running there
    - **Navigate Between Pages**
        - The starter we build in the previous section only has one page. Generally, applications have more pages than that. In this section, we'll cover creating multiple pages using the integrated file system routing, how to use the `Link` component, and about the built-in support for code splitting and prefetching.
        - **Pages in Next.js**
            - A page is just a React component that is exported from a file in he `pages` directory. the route for a page is determined by its file name and file path, with some conventions:
                - `pages/index.js` will be associated with the `/` route
                - `pages/posts/first-post.js` will be at `/posts/first-post`
        - **Create a New Page**
            - Create a `posts` directory in the `pages` directory. Then, create a `first-post.js` file inside of `posts`. Add the following to that file:
                - ```javascript
export default function FirstPost() {
  return <h1>First Post</h1>
}```
            - Going forward, all you need to do to create pages is to add a file to a path inside the `pages` directory. If you wanted to add a page with the path of `/authors/me`, you'd create a file at `pages/authors/me.js`
        - **Link Component**
            - To link between pages in Next, you use the `Link` component from `next/link`.
            - The `Link` component has to wrap an `<a>` tag.
            - Import the `Link` component:
                - ```javascript
import Link from 'next/link'```
            - Create a link:
                - ```javascript

Read <Link href="/posts/first-post"><a>this page!</a></Link>
```
        - **Client-side Navigation**
            - The `Link` component enables **client-side navigation**, meaning the page transition uses JavaScript. This is faster than the default browser navigation.
            - **Code splitting and prefetching**
                - Next.js does the code splitting automatically
                - This means that each page only loads what is necessary for that page (re JavaScript and CSS)
                - This means that the homepage will load quickly, even if you have hundreds of pages. It also means that pages will be isolated, so that if one throws an error, the rest of the application will work.
                - In production, Nextjs will also automatically prefetch code wherever you've used the `Link` component, meaning the code for the page will load in the background
    - **Assets, Metadata, and CSS**
        - Next.js has built-in support for CSS, Sass, and CSS-in-JS
        - In this section, you'll learn about how to add static files (images, etc) to Next.js, how to customize the `<head>` tag for each page, how to create reusable React components with CSS Modules, and how to add global CSS in the `pages/_app.js`
        - **Assets**
            - Next.js serves static files like images from the top-level `public` directory. Files inside the `public` directory can be reference from the root of the application, similar to `pages`
            - The public directory is useful for any static asset, including the `robots.txt`, google site verification, and other static assets
            - Learn more about [Static File Serving](https://nextjs.org/docs/basic-features/static-file-serving)
        - **Metadata**
            - Next.js provides a `Head` component, which you can import from `next/head`
            - You can use this `Head` component to add metadata to the HTML `<head>` tag, like the `<title>`
            - ```javascript
import Head from 'next/head'

export default function Home() {
  return (
    <div className="container">
    	<Head>
    		<title>Set the title for this page</title>
		    <link rel="icon" href="/favicon.ico" />
	    </Head>
    </div>
  )
}```
        - **CSS Styling**
            - Next.js supports CSS and SCSS natively. You can also use third part styling libraries like Tailwind. Finally, you can use any CSS-in-JS solution that you'd like to style your application.
            - **Layout Component**
                - You can create layout components like you normally would: create a `layout.js` file inside a top-level `components/` directory and import it into the components you want to apply it to.
            - **CSS Modules**
                - Next.js has built-in support for CSS modules. All you have to do is name a CSS file with `.module.css` and Next.js will process that as a CSS module, modifying the class name to create the module
            - **Global Styles**
                - You can apply global styles in Next.js as well.
                - First you have to create a global, top-level `App` component. You can do this by adding a file called `_app.js` to the top-level `pages/` directory. In this file, export an `App` component:
                    - ```javascript
export default function App({ Component, pageProps }) {
  return <Component {...pageProps} />
}```
                - To add global styles, just import them into this top-level `App` component. Create a style sheet with global styles, like `global.css` and then import it into this top-level `App` component.
                - Styles will only be global if you import them into `_app.js`!
            - Using the `classnames` library
                - `classnames` is a library that makes toggling class names easier. YOu can install it via NPM
            - **Customizing PostCSS Config**
                - Next.js lets you customize the PostCSS Config. If you create a top-level file called `postcss.config.js` with a config object exported from this file, the config object will be applied to the PostCSS Config
        - **Pre-rendering and Data Fetching**
            - https://nextjs.org/learn/basics/data-fetching
