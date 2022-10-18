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


## Creating Postman API requests

1. Create a simple GET request for the Adalo app Applications collection 
      - You will need to set up authorization
2. Create a simple POST request for the Adalo app Applications collection, create a new application 
      - Simple: Set Full Name to static values 
      - Hard 💪: Set the application.id to the environment applicationId
      - Hard 💪: Add dynamic variables for First Name, Last Name -- see [Postman documenation](https://learning.postman.com/docs/writing-scripts/script-references/variables-list/) for details 
4. Create a simple PUT request to update the status of the application 
5. Create a simple DELETE request to delete the application you created in step #2
6. Add automatic checks to each request 
      - Check the response status code 200 on each of them
      - Only for GET request: Check that the `applicationId` created with POST request is actually present in the response of the GET request. 
      - Hard 💪: make every request to be independent from one another. Hint: use pre-request scripts and tests to create and cleanup data
7. Run the collection in Postman Collection Runner 



## Running collections in command line using Newman collection runner 
1. 



You might need to install/update Node.js and npm
- Check if you have Node.js and npm installed by checking their versions: `node -v` AND `npm -v`, install them if needed 
