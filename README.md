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

- I ran the command **ls** to confirm that you have **package.json** file created.
