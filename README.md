# learning

## microservices 

- Write small functions and each function tries to does on thing; if we can't give the function just a simple name that says what it does, there is something wrong with it that we need to change the function so we can name it better.

- Microservices add complexity too that we are no longer maintaining the configuration for one app and we are maintaining many and then the interplay between them too. The complexity of managing app doesn't go away and we are just shifting the complexity to ops from software developer.

- If one microservice goes down it doesn't impact the whole application, we just start a new instance back up running and we have time to fix the problem. 

- Databases are one of the big reasons why deployments for monolithic applications. In microservices, each one has its own database so if we migrate one database, it has nothing to do with other databases. There is a problem with this though is we lose the ability to run joins since we don't have everything in one database and we can't join across HTTP requests, we have to do it in the Python space or it is starting to make more sense to go to NoSQL database. 

- If we have a big monolithc app we need to scale it, we need to scale the whole thing, in microservices we can scale each service independently and dynamically. Instagram has a cool story of moving Django from Python 2 to Python 3 while having millisions of users withtout going down, and they being very aggressive to get the best memory usuage with each server they work in, for example, they went far as disabling garbage collection. 

- To achieve scalability and no downtime upgrades, all the services need to be load balanced, even if we just run one instance, it needs to be behing a load balancer; when we use Lambda, AWS manages the load-balancing for us.

- There are situations to have a combination of stateless serrvelsss Lambda with more stateful, bigger microservice. Lambda does not support Websocket services, so if we need to have a permanent connection with the client, no way Lamba can handle since Lambda run and exist and doesn't exit any more, also if we are looking for performance, we will not be using Lambda , typically, REST API call that's posted on Lambda through API Gateway takes more than half a second for a simple call, we found no way to bring it below that no matter how simple the actual endpoint is, whereas in Flask of other Python WSGI app, 10 millisecond reponse would be totally reasonable.

- How to keep different servers connected without hard wiring into the code? there is common component called service registry that every microservice platform have in common, the first thing a service starts an instance is to talk to the service registry which is a known address so everybody knows where to find the service registry. The service registry is hard-coded and need to be highly available so that not to use a signle point of contact. If we are running docker for example, it is going to compe up with some port and record it is running on this service on this port to start the job.





