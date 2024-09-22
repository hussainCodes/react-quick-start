# react-quick-start

Steps | Action | Commands | Place | Line
---|---|---|---|---
**1** |Create react project | ```npx create-react-app``` `name`	| Terminal | |
**2** |Install routers| npm i react-router react-router-dom	| Terminal | |
**3** |Install axios| npm i axios	| Terminal | |
**4** |Install react query| npm i @tanstack/react-query	| Terminal | |
**5** |Set up router| import { createBrowserRouter, RouterProvider } from "react-router-dom";	| index.js | | 
| | | const router = createBrowserRouter([ {path: "/", element: <App/>},]); | index.js | after imports
| | |  ```<RouterProvider router={router}/>``` | index.js | inside <React.StrictMode> instead of <App/> 
**6** |Set up axios| *CREATE API FOLDER*	| src |  |
 | | |CREATE INDEX.JS FILE | src/api | |



