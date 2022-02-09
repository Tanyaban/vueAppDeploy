1. It took me 1.5 days to complete on this test.
Things which i would like to add more are-
* Webhooks on github repository for each push event, so that a developer doesn't have to trigger pipeline manually
* Addition of certificates.
* To understand issues, monitoring setup is required so i would go for application monitoring
* For increase in load of jenkins, create master slave so that load can be distributed on slaves
* Store environment variables in configmaps and secrets
* Integrate with tools for vulnerability scan of images, code and application

2. I chose ansible for configuring jenkins on host as it was asked to use one configuration management tool. I used jenkins for continous integration of code. Chose UCD in particular
as deployment tool as UCD provides various sets of plugins and here we can create workflow which can also be used as templates in multiple microservices. Usage of docker and kubernetes is to
containerize app and deploy to cloud. Here kubernetes is orchestration tool with which load is scheduled to multiple nodes.  

3. Recently , A security issue was discovered in Kubernetes where a user may be able to create a container with subpath volume mounts to access files & directories outside of the volume, 
including on the host filesystem.

4. {
"name": "Tanya",
"lastname": "Bansal",
"age": 26,
"address":{
	"city": "Bengaluru",
	"state": "Karnataka",
	"country": "India"
},
"Hobbies": [
"Painting",
"Learning new things"
],
"languages":[
"English",
"Hindi"],
"Techskills":[
"Docker",
"Jenkins",
"kubernetes",
"UCD",
"Java",
"Cloud-ICP, ibm cloud,AWS certified",
"Mongodb",
"MySQL",
"Basics of Ansible and Terraform",
"php"],
"Strengths":[
"Team Player",
"Fast learner",
"Taking ownership of my tasks"
],
"weaknesses":[
"Hard time letting go of tasks until finished",
"Multitasking too much"],
"takePrideIn":[
"when applications are highly available for users(in my work)"],
"believes": [
"We all can make this world a better place"
]
}
