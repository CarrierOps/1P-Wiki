# NEG

Most of our applications run on [cloud run ]() which is a [serverless]() service. Traditionally, load balancers would direct traffic from to an instance of the application. But containers can scale and have multiple instances, that's where NEG enters the picture. NEG enables us to takes a leap from instance based load balancing to service based load balancers