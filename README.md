# Cloud Foundry Tryout

## What happened when you push a node application

Current directory name: node
List of files:
1. main.js
2. package.json
3. Procfile

Push the app
```shell
cd node
cf push node -n node-py
```

This tells PCF to upload, build and run the application named as "node". The option "-n" tells PCF to use "node-py" as the subdomain.

Here is what happened:
1. Create the "node" applicaton
```shell
Creating app node in org pheelysville / space development as <user_id>...
OK
```

2. Create route with the subdomain "node-py"
```shell
Creating route node-py.cfapps.io...
OK
```
3. Bind the route to the application
```shell
Binding node-py.cfapps.io to node...
```
4. Upload the node app
```shell
Uploading node... 
Uploading app files from: <dir_root>\node
Uploading 561B, 3 files
Done uploading
```
5. Start the app
```shell
Starting app node in org pheelysville / space development as <user_id>
Downloading binary_buildpack...
Downloading staticfile_buildpack...
Downloading java_buildpack...
Downloading ruby_buildpack...
Downloading nodejs_buildpack...
Downloaded staticfile_buildpack
Downloading go_buildpack...
Downloaded java_buildpack
Downloading python_buildpack...
Downloaded nodejs_buildpack
Downloading php_buildpack...
Downloaded go_buildpack
Downloading dotnet_core_buildpack...
Downloaded python_buildpack
Downloading dotnet_core_buildpack_beta...
Downloaded binary_buildpack
Downloaded php_buildpack
Downloaded dotnet_core_buildpack_beta
Downloaded dotnet_core_buildpack
Downloaded ruby_buildpack
```
6. Create container
```shell
Creating container
Successfully created container
```
7. Download app package
```shell
Downloading app package...
Downloaded app package (561B)
-----> Nodejs Buildpack version 1.6.5
-----> Installing binaries
       engines.node (package.json): unspecified
       engines.npm (package.json): unspecified (use default)
       **WARNING** Node version not specified in package.json. See: http://docs.cloudfoundry.org/buildpacks/node/node-tips.html
-----> Installing node 4.8.4
       Copy [/tmp/buildpacks/ea5f3c1b3b347a536113352aeb881c8b/dependencies/https___buildpacks.cloudfoundry.org_dependencies_node_node-4.8.4-linux-x64-230101ff.tgz]
       Using default npm version: 2.15.11
-----> Installing yarn 0.27.5
       Copy [/tmp/buildpacks/ea5f3c1b3b347a536113352aeb881c8b/dependencies/https___buildpacks.cloudfoundry.org_dependencies_yarn_yarn-v0.27.5-73002997.tar.gz]
       Installed yarn 0.27.5
-----> Creating runtime environment
       PRO TIP: It is recommended to vendor the application's Node.js dependencies
       Visit http://docs.cloudfoundry.org/buildpacks/node/index.html#vendoring
       NODE_ENV=production
       NODE_HOME=/tmp/contents899079695/deps/0/node
       NODE_MODULES_CACHE=true
       NODE_VERBOSE=false
       NPM_CONFIG_LOGLEVEL=error
       NPM_CONFIG_PRODUCTION=true
-----> Restoring cache
       Skipping cache restore (no previous cache)
-----> Building dependencies
       Installing node modules (package.json)
-----> Caching build
       Clearing previous node cache
       Saving 3 cacheDirectories (default):
       - .npm (nothing to cache)
       - .cache/yarn (nothing to cache)
       - bower_components (nothing to cache)
Exit status 0
```
8. Upload droplet
```shell
Uploading droplet, build artifacts cache...
Uploading build artifacts cache...
Uploading droplet...
Uploaded build artifacts cache (275B)
Uploaded droplet (9.9M)
Uploading complete
```
9. Destroy the container used for building the app
```shell
Destroying container
Successfully destroyed container
```
10. Start the app
```shell
1 of 1 instances running

App started

OK

App node was started using this command `node main.js`
```

