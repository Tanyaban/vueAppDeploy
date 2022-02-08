Automation of vue app to deploy to cloud.

1. To deploy vue app, we need jenkins installed on our server. To do so, i am using ansible playbook jenkins_installation.yml(assuming ansible setup is already present).
Jenkins host should be added in ansible inventory file.
2. Run the playbook using "ansible-playbook jenkins_installation.yml -i inventory.txt" command.
3. Once Jenkins start running, access the host with 8080 port(default). Install all the required plugins from manage plugins.
4. In the global tool configuration, add node js to run build on jenkins server 
5. Before creation of new pipeline generate access token in github repo and add the same in jenkins credentials to access git repo from jenkins pipeline
6. Now, create new pipeline , give a name and select type as pipeline
7. In the cofigure page, select github project and give your github url and select the credentials you created from the dropdown. Tick on peipeline from jenkinsfile and then 
add the name of your jenkinsfile present in github repo(here Jenkinsfile). This file contains all the stages of the pipeline.
8. Please refer to Jenkinsfile_pipeline.txt for pipeline details.
9. Now trigger the pipeline to deploy your application to the cloud.
10. For continous delivery to production environment, we can add one more stage in jenkins pipeline after Build stage for email approval of manager so once it is approved then only
it will move ahead to deployment to cloud.
