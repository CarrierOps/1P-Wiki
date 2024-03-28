# Serverless vs Serverful

Whenever you run code (for an application, a website, a data pipeline, etc) all you need is a computer with RAM, a CPU, and (sometimes) persistent storage like a hard drive for example. This is painfully obvious if you think of how you would write code from you computer. But, in the context of the Cloud it becomes a lot less obvious by what is meant by 'a computer' since the cloud is made up of millions and millions of CPUs, RAM, hard drives, etc that are used by billions of people every day. That's where the concept of serverful vs serverless comes in.

Serverless if the concept that the cloud provider manages and dynamically allocates servers to you and your code/application. The cloud provider will manage the servers (operating systems, updates, security, etc).

Serverful on the other hand, in the context of the cloud, is where you run & operate servers on the cloud. You're the one managing the OS, updates, security.

One major distinction between serverless and serverful is how scaling your code/application is handles. As your application grows, let's say it get's more and more users, you'll need to scale up how much RAM, CPU & storage you give you application to handle the traffic from all your new users. In a serverless application, your cloud provider would automatically assign more servers to your app to meet your app's needs. In a serverful application, you would manually need to provision more servers in the cloud.

Effectively that means that if you hit your current server's limit, a serverful application will just crash because it doesn't have enough resources to operate. While a serverless application will continue to work because your cloud provider will dynamically allocate more servers to you application to satisfy it's resource needs.

There are pros & cons for both. A major con of serverless is that it is typically more expensive to use and you put yourself at risk of [running up a huge bill](https://www.reddit.com/r/AZURE/comments/1arbror/ever_run_up_a_big_cloud_bill_by_accident_tell_me/) your app can scale up "infinitely". A major pro, however, is that serverless applications are a lot easier to deploy & maintain and your application won't crash if you go viral and suddenly have an influx of new users.
