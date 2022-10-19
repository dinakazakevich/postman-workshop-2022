# Postman Workshop 2022

Goal is to learn to test REST APIs with Postman collections, learn to run collections with Newman collection runner and see what an API look like in code.


## ✅ You will learn 
- To understand and test REST APIs 
- What an API looks like in code (not that scary!)
- To use Postman's out-of-the box basic automation capabilities
- Use Newman to run Postman collection in your command line 
- Bonus: Hook up Postman and Newman to Jenkins (only if we have the time).


## 🧱 Prerequisites
- UNIX terminal on local machine (you might need configure it separately if you are running on Windows)
- Postman installed locally https://www.postman.com/ 
- Basic understanding of software architecture: backend, frontend, database
- Ability to read basic javascript not necessarily to write it 
- Basic UNIX console knowledge: running basic commands 


## 🔧 Technologies you will use
- Javascript 
- Postman https://www.postman.com/ 
- Newman https://www.npmjs.com/package/newman
- Jenkins (if we have enough time) https://www.jenkins.io/
- Adalo as an API service https://www.adalo.com/ 
- Airtable as an API service https://airtable.com/


-----

#testing4good

🌎 Testing for Good enables great test automation engineering while shaping a more equitable society.👩‍💻
Today, we're asking for donations for Environmental Working Group

------


## Instructor: Dina Kazakevich 

I'm a Senior QA Analyst at [Adalo](https://www.adalo.com/) and a former mentor at [Practicum by Yandex](https://practicum.com/) where I taught over 100 aspiring software testers. I've attended the BBST Foundations and the Instructors courses by AST as well as courses by James Bach and Michael Bolton. I'm passionate about remote work and slow traveling and I run an international community of remote tech professionals [Remote Ever After](https://t.me/remoteeverafter) (currently in Telegram but migrating to Reddit). I've been living out of my suitecase and traveling the world for over 5 years now. 

- Twitter: https://twitter.com/dinakazakevich 
- LinkedIn: https://www.linkedin.com/in/dinakazakevich/ 
- Polywork: https://www.polywork.com/dinakazakevich <br>
- Instagram: https://www.instagram.com/dina.kazakevich/ 
- TikTok: https://www.tiktok.com/@remoteeverafter 


## ⚙️ Setup

1. Install Postman https://www.postman.com/ 
2. Sign up for a free Adalo account https://www.adalo.com/?via=dina
3. Logging into your Adalo account
4. Follow the link and clone this [sample Adalo app](https://remoteeverafter.adalo.com/applicants) — we will be using its collections
5. Enable Free Integrations Trial in Adalo Editor: Settings > App Access > Start Trial 
6. Generate API Key


## ✨ Bonus task: Set up a local API service with Express.js 
1. Create an express js app https://expressjs.com/en/starter/generator.html
	1. Create a dedicated directory and run this in the terminal 
	2. ```npx express-generator ```
	3. Install dependencies 
	```sh
	$ cd myapp
	$ npm install
	```
2. Run the expressjs-sample project locally, look through the routes/users.js
	```sh
	$ npm start
	```
3. Access it at http://localhost:3000/ 
4. Replace you routes/user.js with the respectful file from https://github.com/dinakazakevich/expressjs-sample  
5. Look at how API endpoints look like, search for `router.get`, `router.post`, `router.delete`
6. Start the express-sample service locally by 
7. Test with Postman, specifically the POST request
8. The update the POST endpoint to return result: `New user aded` instead of `New user created`
9. Restart the service and run POST request again to confirm ti was updated. 


## Creating Postman API requests

1. Create a simple GET request for the Adalo app Applications collection 
      - Hint: You will need to set up authorization
2. Create a simple POST request for the Adalo app Applications collection, create a new application 
      - Simple ☑️: Set Full Name to static values 
      - Simple ☑️: Set the application.id to the environment applicationId
      - Hard 💪: Add dynamic variables for First Name, Last Name -- see [Postman documenation](https://learning.postman.com/docs/writing-scripts/script-references/variables-list/) for details 
3. Create a simple PUT request to update the status of the application 
4. Create a simple DELETE request to delete the application you created in step #2
5. Add automatic checks to each request [Postman documentation](https://learning.postman.com/docs/writing-scripts/test-scripts/)
      - Simple ☑️: Check the response status code 200 on each of them
      - Hard 💪: Only for GET request, Check that the `applicationId` created with POST request is actually present in the response of the GET request. 
      - Hard 💪: make every request to be independent from one another. Hint: use pre-request scripts and tests to create and cleanup data
6. Run the collection in Postman Collection Runner — [Postman documentation](https://learning.postman.com/docs/running-collections/intro-to-collection-runs/)
7. Set up a Monitor for the Collection to run every hour — [Postman documentation](https://learning.postman.com/docs/monitoring-your-api/setting-up-monitor/)
8. There is a sample postman collection with Adalo public API set up in [./postman-collections/adalo-postman-collection](https://github.com/dinakazakevich/postman-workshop-2022/tree/main/postman-collections/adalo-postman-collection)
	IMPORTANT: Please use your own Adalo app tokens and Authentication key to run this locally. 

## Running collections in command line using Newman collection runner 
1. We can also run the Postman Collection in the command line using Newman Open Source Collection Runner 
2. Install Newman 
```sh
$ npm i newman -g
```
3. Export Collection and Environment and save them locally 
4. Run the collection 
```sh
$ newman run PostmanCollection.json -e environment.json
```

## Generating HTML reports
1. Install htmlextra https://www.npmjs.com/package/newman-reporter-htmlextra
```sh
$ npm i newman-reporter-htmlextra
```
2. Run a collection with newman and generate an html report 
```sh
$ newman run collection.json -e environment.json -r htmlextra
```


Note: You might need to install/update Node.js and npm
- Check if you have Node.js and npm installed by checking their versions: `node -v` AND `npm -v`, install them if needed 
- Installation steps are here https://nodejs.org/en/download/package-manager/


## 🛣️ Jenkins Pipeline
1. Install Jenkins https://www.jenkins.io/doc/book/installing/
2. Troubleshoot `Permissions denied` error by running 
```sh
$ sudo chown -R $(whoami) /path/to/restricted/directory
```
3. Install Node.js and Newman in Jenkins: more info here https://learning.postman.com/docs/running-collections/using-newman-cli/continuous-integration/
      - Go to your Jenkins server (it's at http://localhost:8080 by default if you are running it locally) and sign in.
      - Go to Manage Jenkins > Manage Plugins and install the NodeJS plugin.
      - Go to Manage Jenkins > Global Tool Configuration and under NodeJS, select Add NodeJS.
      - Enter a name for the Node.js installation.
      - In Global npm packages to install, enter newman.
      - Select Save.
4. Setup Jenkins
	- With Jenkins running, go to http://localhost:8080 and sign in.
	- On the Dashboard page, select New Item on the left sidebar to create a new job.
	- Select a Freestyle project from the options. Name your project, and select OK.
	- In General > Build, add a build step in the project, and choose Execute Shell. The build step executes a shell command. Enter a shell command to run, such as newman run ~/Desktop/jenkins_demo_postman_collection.json.
	- In Build Environment > Build Environment, select Provide Node & npm bin/ folder to PATH and choose the NodeJS install you configured with Newman.
	- Select Save to finish creating the project.
4. Run the Build 

 
 
 
# Additional task — Airtable API 
1. Repeat teh exercise for Airtable Database API 
2. Sign up for a free Airtable account 
3. Clone this app to your account https://airtable.com/shrECwvJjBJzTgiQs/tblymCw8pWMTvUccW/viwtmKb10IVAhPY5F
4. Generate API key in https://airtable.com/account 


### Tasks for Airtable
1. Created simple GET/POST/DELETE reuests 
2. First loop them to clean after the run 
3. Second, make them run an stnadalone tests that create and delete data after themselves. 
4. GET: 
      - pre-scripts: (1) create a new record, (2) save the recordId to an environment variable
      - tests: (1) response status 200, (2) response contains new applicant created, (3) delete the record created
5. POST: 
      - pre-scripts: n/a
      - tests: (1) check response status code is 200, (2) Set Environment variable applicantId to the id of the user created, (3) Test that the user we created was returned in the response, (4) Send DELETE request to delete the user you have just created
6. DELETE 
      - pre-scripts: (1) Send POST request to create a new user and save the id of the applicant to an environment variable 
      - tests: (1) Status code is 200
7. Run the Collection manually 
8. Set up a Monitor to run every hour 
9. Run the collection via command line using Newman 
10. Run the collection via command line using Newman and generate and html report 
11. Answers to the above are in a sample collection in [./postman-collections/airtable-postman-collection](https://github.com/dinakazakevich/postman-workshop-2022/tree/main/postman-collections/airtable-postman-collection)
	IMPORTANT: Please use your own Airtable app tokens and Authentication key to run this locally. 



### Additional reading 
1. [Difference between Postman CLI vs Newman Collection Runner](https://learning.postman.com/docs/postman-cli/postman-cli-overview/)
