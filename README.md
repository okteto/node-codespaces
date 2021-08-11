# Cloud Native Development Environments with GitHub CodeSpaces and Okteto

GitHub CodeSpaces lets you deploy preconfigured cloud-based development environments at the touch of a button. Okteto let's you develop your applications using realistic development environments directly in Kubernetes. Put them together to build a true Clod Native Development experience 🚀


## Deploy your CodeSpace

To try it out, go [to this GitHub repository](https://github.com/rberrelleza/node-codespaces), click on the `code` button, select the `code spaces` tab, and click on the `New codespace` button to deploy your first codespace.


While the CodeSpace starts, log in to your Okteto Cloud account (or create one, it's free), and create a personal token. 

Once the CodeSpace is running, open a terminal, and run `okteto login --token $TOKEN` to log in to your Okteto Cloud account.


In the same terminal, run `okteto namespace` to activate your Okteto namespace and download your credentials. With this, you are ready to run any okteto (or kubernetes) command directly from your CodeSpace terminal. 


Deploy the `movies` application in your Okteto namespace by running `okteto pipeline deploy`. When you execute this command, the pipeline will automatically build your images using the latest commit, and deploy all the application componenets directly in Okteto Cloud, using helm. 

Head over to Okteto Cloud, and click on the endpoint of your application to check it out. This is the dev version of your application, running in Okteto Cloud. 


Now, let's make a change on the app. But instead of changing the code in CodeSpaces and then redeploying the application like we normally do, we are going to develop it directly in Okteto. To do this, go to back to the terminal, navigate to the `frontend` folder, and then run `okteto up`.  

Running  `okteto up` will, among other things, synchronize the file system in your CodeSpace with the one in your application's container and run your application in hot reload mode. Anytime you change a file in your IDE, the change will be automatically synchronized, and the node process will hot reload it. 

Let's try it out. Open [frontend/src/App.jsx](frontend/src/App.jsx), and change line 85 to be like this:

```
<TitleList title="⭐ Movies" titles={movies.data} loaded={movies.loaded} /> 
```

Save the file. Notice how the terminal starts logging things things as soon as you save the file. This is because Okteto already detected that you made a change and automatically synchronized them to the container, where react picked them up, and hot relaoded the application. 

Head back to the browser, reload the page, and see if you notice any differences. 

Cool no? Let's do it one more time. Go back to [frontend/src/App.jsx](frontend/src/App.jsx) in your CodeSpace, and change line 86 to be like this:

<TitleList title={`Keep watching for ${session.name}`} titles={watching.data} loaded={watching.loaded} />

Save, go to the application's tab, and reload. Boom 💥, the changes are already applied. 

## Conclusion

This is an example of how you can combine the power of GitHub CodeSpaces and Okteto to create a truly cloud-native development environment. By combining them together you are able to:

1. Deploy a browser-based IDE with your code, credentials, and all your dependencies already preinstalled. 
2. Deploy a realistic copy of your application, using the same configuration that you would use in production. 
3. Get the fastest possible developer loop.

Okteto works with any IDE, any tool, and any stack. To learn more head over to https://okteto.com and deploy your own cloud native development environment in seconds!

