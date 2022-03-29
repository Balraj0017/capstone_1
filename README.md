# Website of fleetms which has database MYSQL
To run this project , just follow these commands 

mvn clean 
mvn test
mvn package
Then the jar file will generate 

# I had made 2 deployments 
one is for front-end ,which had nodeport service
another one is bakck-end , which had headless service 

# Run the website 
simply write 
minikube service list 
It will list all the ip's , there you can find the nodeport ip address 
Copy this and apply on your browser
