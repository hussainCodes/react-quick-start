# react-quick-start

Steps | Action | Commands | Place | Line
---|---|---|---|---
**1** |Create react project | ```npx create-react-app``` `name`	| Terminal | |
**2** |Install routers| ```npm i react-router react-router-dom```	| Terminal | |
**3** |Install axios| ```npm i axios```	| Terminal | |
**4** |Install react query| ```npm i @tanstack/react-query```	| Terminal | |
**5** |Set up router| ```import { createBrowserRouter, RouterProvider } from "react-router-dom";```	| index.js | | 
| | | ```const router = createBrowserRouter([ {path: "/", element: <App/>},]);``` | index.js | after imports
| | |  ```<RouterProvider router={router}/>``` | index.js | inside ```<React.StrictMode>``` instead of ```<App/>``` 
**6** |Set up axios| *CREATE API FOLDER*	| src |  |
 | | |*CREATE INDEX.JS FILE* | src/api | |
|  | | ```import axios from 'axios'``` |src/api/index.js| |
| | | ```const instance = axios.create({ baseURL: 'URL-STRING-HERE'});                  export default instance``` |src/api/index.js| |
**7** |Set up HTTP Requests file| *CREATE* ```names.js``` *FILE //etc. [pets.js, students.js]*	| src/api | |
| | | ```import instance from "." ```| src/api/```names.js```||
**8**| Set up react query| ```import { QueryClient, QueryClientProvider} from '@tanstack/react-query'```|index.js| |
| | |```const queryClient = new QueryClient();```|index.js|after imports
| | |```<QueryClientProvider client={queyClient}>```| index.js|inside ```<React.StrictMode>``` wrap around ```<Router/>```



The following snippet is command lines for quick setup react-project 
- [x] CD to where you want to save the project
- [x] Change every ```NAME``` to your project name
- [x] Copy it to your terminal and run it

```javascript
npx create-react-app NAME
cd NAME
npm i react-router react-router-dom	
npm i axios	
npm i @tanstack/react-query
cd src
mkdir api
mkdir components
mkdir assets
mkdir context
cd assets
mkdir images
cd ..
cd api
touch index.js
touch auth.js
touch storage.js
```


Copy the following snippet and paste it in *API/INDEX.JS*
```js
import axios from 'axios'	
const instance = axios.create({ baseURL: 'URL-STRING-HERE'});
instance.interceptors.request.use((config) => {
  const token = localStorage.getItem("token");
  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }
  return config;
});
export default instance	
```


Delete everything in *SRC/INDEX.JS* and replce it with the following code

```JSX

import React from "react";
import ReactDOM from "react-dom/client";
import "./index.css";
import App from "./App";
import reportWebVitals from "./reportWebVitals";
import { createBrowserRouter, RouterProvider } from "react-router-dom";
import { QueryClient, QueryClientProvider} from '@tanstack/react-query'	

const queryClient = new QueryClient();	

const router = createBrowserRouter([{ path: "/", element: <App /> }]);
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(
  <React.StrictMode>
<QueryClientProvider client={queryClient}>	
    <RouterProvider router={router} />
</QueryClientProvider>
  </React.StrictMode>
);

// If you want to start measuring performance in your app, pass a function
// to log results (for example: reportWebVitals(console.log))
// or send to an analytics endpoint. Learn more: https://bit.ly/CRA-vitals
reportWebVitals();
```



