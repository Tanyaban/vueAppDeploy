Automation of vue app for deployment of application to cloud.

1. To deploy vue app, we need jenkins installed on our server. To do so, i am using ansible playbook jenkins_installation.yml(assuming ansible setup is already present).
Jenkins host should be added in ansible inventory file(inventory.txt).
target <hostname>
2. Run the playbook using "ansible-playbook jenkins_installation.yml -i inventory.txt" command.
3. Once Jenkins start running, access the host with 8080 port(default). Install all the required plugins from manage plugins option.
4. In the global tool configuration, add node js to run build on jenkins server.
5. Before creation of new pipeline generate access token in github repository and add the same in jenkins credentials to access git repository from jenkins pipeline
6. Now, create new pipeline ,give a name and select type as pipeline.
7. In the cofigure page, select github project and give your github url and select the credentials you created from the dropdown. Tick on pipeline from jenkinsfile and then 
add the name of your jenkinsfile present in github repository(here Jenkinsfile). This file contains all the stages of the pipeline.
8. Please refer to Jenkinsfile_pipeline.txt for pipeline details.
9. Now trigger the pipeline to deploy your application to the cloud.
10. For continous delivery to production environment, we can add one more stage in jenkins pipeline after Build stage for email approval of manager so once it is approved then only
it will move ahead to deployment to cloud.
11. For horizontal autoscaling we can use the following command:
kubectl autoscale deployment <deployment name> --cpu-percent=50 --min=2 --max=10
This command will create a hpa which will maintain the pods from 2 to 10 based on cpu utilization. we can also create hpa based on custom metrics.
For nodes autoscaling, we can add the environment variables in the already created cluster,
export NUM_NODES = 2
export KUBE_AUTOSCALER_MIN_NODES = 2
export KUBE_AUTOSCALER_MAX_NODES = 10
export KUBE_ENABLE_CLUSTER_AUTOSCALER = true
Now start the cluster by running kube-up.sh script. After this, if we increase the load of pods we can also observe the increase in number of nodes as well on more load.

