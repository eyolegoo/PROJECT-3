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

- I need a database where we will store our data. For this we will make use of mLab. mLab provides MongoDB database as a service solution (DBaaS), so to make life easy, I signed up for a shared clusters free account, which is ideal for my use case. (https://mongodb.com/contributor-guide-index.md). Sign up here. Follow the sign up process, select AWS as the cloud provider, and choose a region near you.
