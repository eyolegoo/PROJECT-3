## PROJECT-3: MERN STACK IMPLEMENTATION


***STEP 1: BACKEND COMFIGURATION***

- I updated Ubuntu using `sudo apt update` followed by upgrading Ubuntu `sudo apt upgrade`

<img width="600" alt="UPDATE UBUNTU" src="https://user-images.githubusercontent.com/115954100/211135295-82fcd244-1f84-48b4-9132-b2378b4c5db1.png">

<img width="782" alt="UBUNTU UPGRADED" src="https://user-images.githubusercontent.com/115954100/211135304-0c81bd22-4eac-42a5-97bd-388296032d2f.png">

- I entered the location of **Node.js software** from Ubuntu repositories using the command `curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -`.

- Then I Installed **Node.js** with the command `sudo apt-get install -y nodejs`. This command installs both **nodejs and npm**. **NPM** is a package manager for Node like **apt** for Ubuntu, it is used to install Node modules & packages and to manage dependency conflicts.

<img width="439" alt="NODE INSTALLATION CONFIRMED" src="https://user-images.githubusercontent.com/115954100/211135272-0893c905-c28a-49a9-a422-27ae433801e4.png">


- **Setting up the application code**

- I created a new directory for your To-Do project using `mkdir Todo`.

<img width="353" alt="TODO CREATED" src="https://user-images.githubusercontent.com/115954100/211135344-8b153d41-577d-431b-8fb4-0e9ee2fce8bd.png">

- With the `ls` command, I verified if the new To-do directory was created.

- In order to see some more useful information about files and directories, you can use following combination of keys *ls -lih* – it will show you different properties and size in human readable format. You can learn more about different useful keys for ls command with *ls --help*.

- I changed my current directory to the newly created one using `cd Todo`

- Next, I used the command `npm init` to initialise my project, and a new file named **package.json** was created. This file normally contain information about my application and the dependencies that it needs to run. I followed the prompts after running the command. I pressed *Enter* several times to accept default values, then I accepted to write out the **package.json** file by typing yes.

<img width="576" alt="INITIALISED THE PROJECT AND PACKAGE JSON FILE CREATED" src="https://user-images.githubusercontent.com/115954100/211135233-2d0c68e6-6fe3-4acb-b7b8-61f759957e5f.png">

- I ran the command `ls` to confirm that you have **package.json** file created.


- **ESPRESSJS INSTALLATION**

- Express is a framework for Node.js, therefore a lot of things developers would have programmed is already taken care of out of the box. Therefore it simplifies development, and abstracts a lot of low level details. For example, Express helps to define routes of your application based on HTTP methods and URLs.

- I installed *EXPRESS* using the command code `npm install express`

- create a file **index.js** with the command code `touch index.js`

- I ran `ls` to confirm that your index.js file is successfully created

- Immediately after that, I installed the **dotenv module** using the command code `npm install dotenv` 

<img width="397" alt="express, index js, dotenv" src="https://user-images.githubusercontent.com/115954100/211199044-85e4f3bd-9d88-476f-a36a-ce28ccd5b0d4.png">

- I Opened the **index.js file** with the command code `vim index.js`

- I copied and pasted the below code into the opened **index.js**

```
const express = require('express');
require('dotenv').config();

const app = express();

const port = process.env.PORT || 5000;

app.use((req, res, next) => {
res.header("Access-Control-Allow-Origin", "\*");
res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
next();
});

app.use((req, res, next) => {
res.send('Welcome to Express');
});

app.listen(port, () => {
console.log(`Server running on port ${port}`)
});
```

- Notice that I have specified to use *port 5000* in the code. This will be required later when we go on the browser. I saved the file in vim using `w` and exited the vim using `qa`.

- I started the server to see if it works. I Opened my terminal in the same directory as the **index.js** file and type: `node index.js`.

<img width="264" alt="running server port 5000" src="https://user-images.githubusercontent.com/115954100/211199003-eb614645-174c-4807-a735-fdaf90185d95.png">

- This feedback *Server running on port 5000* in your terminal shows everything is right.

- I opened this port *5000* in EC2 Security Groups.

<img width="809" alt="Inbound rule for port 5000" src="https://user-images.githubusercontent.com/115954100/211199487-518785f5-3473-49c6-8266-13da1f164db5.png">

- I Opened up my browser and accessed my server’s Public IP or Public DNS name followed by port 5000:

- `http://<PublicIP-or-PublicDNS>:5000`

<img width="516" alt="Welcome to Express" src="https://user-images.githubusercontent.com/115954100/211199685-553aeef4-cac9-47bb-9061-49cec59a961b.png">


- **ROUTES**

There are three actions that our To-Do application needs to be able to do:

- 1 Create a new task
- 2 Display list of all tasks
- 3 Delete a completed task

- Each task will be associated with some particular endpoint and will use different standard HTTP request methods: **POST, GET, DELETE**.

- For each task, we need to create routes that will define various endpoints that the *To-do* app will depend on. So let us create a folder *routes*
`mkdir routes`

- Change directory to *routes* folder using the commmand code `cd routes`.

- I created a file **api.js** with the command code `touch api.js`.

- I opened the file with the command `vim api.js`.

- I copied and pasted below code into the open **api.js** file

```
const express = require ('express');
const router = express.Router();

router.get('/todos', (req, res, next) => {

});

router.post('/todos', (req, res, next) => {

});

router.delete('/todos/:id', (req, res, next) => {

})

module.exports = router;
```


- **MODELS**

- Since the app is going to make use of Mongodb which is a NoSQL database, I need to create a model. A model is at the heart of *JavaScript based applications*, and it is what makes it interactive. I also use models to define the database schema . This is important so that we will be able to define the fields stored in each Mongodb document. In essence, the Schema is a blueprint of how the database will be constructed, including other data fields that may not be required to be stored in the database. These are known as virtual properties.

- To create a Schema and a model, I installed *mongoose* which is a *Node.js* package that makes working with mongodb easier.

- I changed directory back Todo folder with `cd` .. and installed Mongoose using the command code `npm install mongoose`.

- I created a new folder *models*, using the command code `mkdir models`.

<img width="402" alt="Mongoose- todo" src="https://user-images.githubusercontent.com/115954100/211204410-8815293f-afd0-4def-8e78-22886c4ff8e8.png">

- I changed directory into the newly created ‘models’ folder using the code `cd models`.

- Inside the models folder, I created a file and name it *todo.js* using the code `touch todo.js`.

- All three commands above can be defined in one line to be executed consequently with help of && operator, like this: `mkdir models && cd models && touch todo.js`.

- I opened the file I created with using `vim todo.js` then pasted the code below in the file:

```
const mongoose = require('mongoose');
const Schema = mongoose.Schema;

//create schema for todo
const TodoSchema = new Schema({
action: {
type: String,
required: [true, 'The todo text field is required']
}
})

//create model for todo
const Todo = mongoose.model('todo', TodoSchema);

module.exports = Todo;
```
- Now I updated my *routes* from the file *api.js* in ‘routes’ directory to make use of the new model.

<img width="295" alt="Updated routes from api js file" src="https://user-images.githubusercontent.com/115954100/211204462-b650e7b5-9a21-4660-a3fe-fb00aec1e195.png">

- In Routes directory, I opened *api.js* with **vim api.js**, I deleted the code inside with *:%d* command and pasted the code below into it then saved and exited.

```
const express = require ('express');
const router = express.Router();
const Todo = require('../models/todo');

router.get('/todos', (req, res, next) => {

//this will return all the data, exposing only the id and action field to the client
Todo.find({}, 'action')
.then(data => res.json(data))
.catch(next)
});

router.post('/todos', (req, res, next) => {
if(req.body.action){
Todo.create(req.body)
.then(data => res.json(data))
.catch(next)
}else {
res.json({
error: "The input field is empty"
})
}
});

router.delete('/todos/:id', (req, res, next) => {
Todo.findOneAndDelete({"_id": req.params.id})
.then(data => res.json(data))
.catch(next)
})

module.exports = router;
```


- **MONGODB DATABASE**

- I need a database where we will store our data. For this we will make use of mLab. mLab provides MongoDB database as a service solution (DBaaS), so to make life easy, I signed up for a shared clusters free account, which is ideal for my use case. [Mongo](https://www.mongodb.com/contributor-guide-index.md). I followed the sign up process, I selected AWS as the cloud provider, and choosed a region near me. 

- I completed a get started checklist as shown on the image below

<img width="1667" alt="MLab-dashboard 1" src="https://user-images.githubusercontent.com/115954100/211211958-a45f2227-834e-4bcb-ad34-30e351118bf4.png">

- I allowed access to the MongoDB database from anywhere (Not secure, but it is ideal for testing)

- **NOTE** In the image below, I changed the time of deleting the entry from 6 Hours to 1 Week

<img width="1537" alt="MogoDB-Network-Access 2" src="https://user-images.githubusercontent.com/115954100/211212252-f9ca8398-6539-466b-b352-013eb3b74d73.png">

- I created a MongoDB database and collection inside mLab

<img width="1235" alt="Mongo-create-DB-1 3" src="https://user-images.githubusercontent.com/115954100/211212334-3c1deb71-b19d-4aba-9ed0-8f325b1e0cd5.png">

<img width="1585" alt="Mongo-create-DB-2 4" src="https://user-images.githubusercontent.com/115954100/211212368-30d204cf-6e3c-4db7-a603-2d771ad6d798.png">

- In the **index.js file**, 1 specified **process.env** to access environment variables, but I have not yet created this file. So I need to do that now.

- I created a file in my *Todo directory* and name it **.env** using the code `touch .env` then opened the file `vi .env`

- I added the connection string to access the database in it, just as below:

- `DB = 'mongodb+srv://<username>:<password>@<network-address>/<dbname>?retryWrites=true&w=majority'`

- I ensured to update <username>, <password>, <network-address> and <database> according to your setup

- Here is how to get your connection string

<img width="1276" alt="Mongo-connection string1 5" src="https://user-images.githubusercontent.com/115954100/211213321-9bb07c73-5a45-4f99-a31d-3c32d1ee4957.png">
  
<img width="1539" alt="Mongo-connect string2 6" src="https://user-images.githubusercontent.com/115954100/211213331-d55d601c-ac07-4f7b-a827-ec2602ba8b21.png">

- I updated the **index.js** to reflect the use of *.env* so that *Node.js* can connect to the database.
  
- I Simply deleted the existing content in the file, and updated it with the entire code below.

- To do that using vim, follow below steps

- I opened the file with `vim index.js`
- I pressed esc
- I typed :
- I typed %d
- I hit ‘Enter’
- The entire content will be deleted, then,

- I pressed 'I' to enter the insert mode in vim
- Now, pasted the entire code below in the file.  

```
const express = require('express');
const bodyParser = require('body-parser');
const mongoose = require('mongoose');
const routes = require('./routes/api');
const path = require('path');
require('dotenv').config();

const app = express();

const port = process.env.PORT || 5000;

//connect to the database
mongoose.connect(process.env.DB, { useNewUrlParser: true, useUnifiedTopology: true })
.then(() => console.log(`Database connected successfully`))
.catch(err => console.log(err));

//since mongoose promise is depreciated, we overide it with node's promise
mongoose.Promise = global.Promise;

app.use((req, res, next) => {
res.header("Access-Control-Allow-Origin", "\*");
res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
next();
});

app.use(bodyParser.json());

app.use('/api', routes);

app.use((err, req, res, next) => {
console.log(err);
next();
});

app.listen(port, () => {
console.log(`Server running on port ${port}`)
});  
```

- Using environment variables to store information is considered more secure and best practice to separate configuration and secret data from the application, instead of writing connection strings directly inside the **index.js** application file.
  
- I started the server using the command `node index.js`  
  
<img width="947" alt="Database connected successfully" src="https://user-images.githubusercontent.com/115954100/211215517-4a8e6cd2-31a2-4e3f-ba67-aae75fbfe573.png">
  
- You shall see a message **‘Database connected successfully’**, if so – we have our backend configured. Now we are going to test it.

- **Testing Backend Code without Frontend using RESTful API**
  
- So far I have written backend part of my To-Do application, and configured a database, but I do not have a frontend UI yet. I need **ReactJS** code to achieve that. But during development, I will need a way to test the code using *RESTfulL API*. Therefore, I will need to make use of some API development client to test my code.

- In this project, I used [Postman](https://www.postman.com) to test our API. 
  
- I clicked [Install Postman](https://www.postman.com/downloads/) to download and install postman on your machine.
  
- Click [HERE](https://www.youtube.com/watch?v=FjgYtQK_zLE) to learn how [perform CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete) operartions on Postman.
  
- I tested all the API endpoints and make sure they are working. For the endpoints that require body, you should send **JSON** back with the necessary fields since it’s what we setup in our code.
  
- I opened my Postman, created a POST request to the API `http://<PublicIP-or-PublicDNS>:5000/api/todos`. This request sends a new task to our To-Do list so the application could store it in the database.

- **Note:** make sure your set header key *Content-Type* as *application/json*
  
![postman_header 7](https://user-images.githubusercontent.com/115954100/211219235-ca3201ab-0a1e-455e-945e-f0fb592c3925.png)

- I checked the image below:
  
![post-request](https://user-images.githubusercontent.com/115954100/211219350-93e7ce99-3175-43c7-8675-b8a0be81d7cb.png)

- I created a GET request to my API on `http://<PublicIP-or-PublicDNS>:5000/api/todos`. This request retrieves all existing records from out To-do application (backend requests these records from the database and sends it to us back as a response to GET request).
  
![get-request](https://user-images.githubusercontent.com/115954100/211219565-c669085e-140e-4649-99b8-48e8fb154021.png)
  
- Now I have tested backend part of our To-Do application and have made sure that it supports all three operations I wanted:
  
- Display a list of tasks – HTTP GET request
- Add a new task to the list – HTTP POST request
- Delete an existing task from the list – HTTP DELETE request
  
- **POST**
 
<img width="957" alt="POSTMAN POST REQUEST" src="https://user-images.githubusercontent.com/115954100/211220145-da58af9e-139c-487d-8295-9904f92141d7.png">
  
- **GET**  
  
<img width="960" alt="POSTMAN GET REQUEST" src="https://user-images.githubusercontent.com/115954100/211220170-10ff5d7a-ee88-4b29-b4d8-c5a548ab5371.png">
  
- **DELETE**
  
<img width="960" alt="HOW TO DELETE ON POSTMAN" src="https://user-images.githubusercontent.com/115954100/211220274-2e6a93d7-b1ba-4a5e-a36a-64d419640cdd.png">
  
<img width="960" alt="DELETE STEP" src="https://user-images.githubusercontent.com/115954100/211220302-409c5a55-92d2-4fc0-8516-982c2965eda2.png">

<img width="958" alt="ID DELETED" src="https://user-images.githubusercontent.com/115954100/211220343-d5e9efef-a63b-4a0e-ad4b-2f3e92a8248e.png">

- I have successfully created my Backend, now let's create the Frontend.
  
 
 ***STEP 2: FRONTEND CREATION***
  
- Since I'm done with the functionality I need from the backend and API, it is time to create a user interface for a Web client (browser) to interact with the application via *API*. To start out with the frontend of the **To-do app**, I used the **create-react-app** command to scaffold our app

- In the same root directory as my backend code, which is the **Todo directory**, I ran: `npx create-react-app client`.
  
- This created a new folder in my **Todo directory** called **client**, where all the **react code** will be added.
  
- <img width="960" alt="client install" src="https://user-images.githubusercontent.com/115954100/211305129-a35e3c84-5f4b-475e-a9da-513058b650b5.png">

- **Running a React App**
  
- Before testing the **react app**, there are some dependencies that need to be installed.
  
- I installed [concurrently](https://https://www.npmjs.com/package/concurrently). It is used to run more than one command simultaneously from the same terminal window. Using `npm install concurrently --save-dev`.
  
- I installed nodemon [nodemon](https://www.npmjs.com/package/nodemon). It is used to run and monitor the server. If there is any change in the server code, nodemon will restart it automatically and load the new changes. Using `npm install nodemon --save-dev`.
  
- In **Todo folder** open the **package.json** file.  I changed the highlighted part of the below screenshot and replaced with the code below.

```
"scripts": {
"start": "node index.js",
"start-watch": "nodemon index.js",
"dev": "concurrently \"npm run start-watch\" \"cd client && npm start\""
},
```  
![script](https://user-images.githubusercontent.com/115954100/211307934-d502be8d-f865-404d-a3ad-d58f2ce42569.png)

- Configure Proxy in **package.json**
  
- Changed directory to ‘client’ `cd client`.
  
- Opened the **package.json** file `vi package.json`
  
- i added the key value pair in the **package.json** file **"proxy": "http://localhost:5000"**.
The whole purpose of adding the proxy configuration in number 3 above is to make it possible to access the application directly from the browser by simply calling the server url like **http://localhost:5000** rather than always including the entire path like **http://localhost:5000/api/todos**  
  
-   
