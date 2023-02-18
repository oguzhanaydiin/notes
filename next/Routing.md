# Routing In Next

## File Based Routing

In src/api folder, every file you create to be evaluated as route in main application.
You can chose any name for your route but there are few expectional situations.

* Index.js -> it indicates the base route for its own folder
  * Example: for the src/pages/index.tsx          -> file it indicates -> localhost:3000                page
           
---
           
If you want to add new routes with same sub route name, you can create folders and you can create index files or any route files in them as well.

* for the src/pages/project/index.tsx  -> file it indicates -> localhost:3000/project        page
* for the src/pages/project/load.tsx   -> file it indicates -> localhost:3000/project/load   page

---

You can also make dynamic folders to match route.
  Example: 
  * localhost/bob/project    
  * localhost/max/project
  * localhost/alice/project  
      * You can match this routes by creating dynamic folders
                                     src/pages/[customer]/project.tsx     -> this project tsx file with dynamic [customer] 
                                                                             folder, you can create a route for any customer you want
