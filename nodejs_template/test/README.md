# Faas Inspector Testing and Deployment Tools

    📁 nodejs_template
        📁 scr
            function.js
            Inspector.js
            package.json
        📁 test
            📁 node_modules
                ...
            config.json
            publish.sh
            partestcpu.sh
            local.js
        📁 platforms  
            ...
  

The scr folder contains all of the code for your function. 

  * [**Inspector.js**](nodejs_template/src/Inspector.js) is the FaaS Inspector itself and is completely independent of any files or folders in this project. If you do not plan to use this file sctructure, Inspector.js can be used and moved to any Node.js project.
  
  * [**function.js**](nodejs_template/src/function.js) file is the handler that each cloud provider will execute. 

  * [**package.json**](nodejs_template/src/package.json) is where 3rd party dependencies must be defined (**WARNING:** If you are deploying onto Azure Functions, dependencies must also be downloaded into test/node_modules). 
    
### 📁 test Folder

This folder contains tools to help test and deploy serverless functions onto each supported platform. For more detailed documentation please see the comments at the beginning of each file. 

  * **config.json** contains all of the neccessary variables to deploy a function. This includes the name of the function, the Azure Function app name, and other information.
  * **publish.sh** is a script used to deploy a function onto each platform. This requires each each cloud providers CLI to be installed and properly configured.
  * **partestcpu.sh** is a script to test a function after it has been deployed. The script can make many calls in parallel to create stress on each platform.
  * **local.js** is an additional handler used to execute a function locally. This can be useful to test a function before deploying onto the cloud.
    

This folder contains all of the platform specific files needed to deploy onto each cloud provider. NONE of these files need to be edited to deploy a function. The publish.sh script copies these files into the scr folder, constructs the correct folder structure, deploys the function, and then cleans up the scr folder back to its original state.