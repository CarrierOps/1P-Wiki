# Networking

Behind the scenes of our infrastructure, we make use of many services that relate to networking and make use of a [VPC](#vpc) network. There are 3 main use cases for using a network & related network services: allowing our applications/services on GCP to communicate with each other, allow them access to the internet (or, going the other direction, accessing our services from the internet), and security around access to our applications. Here are the networks & network services we use:

## VPC

A `VPC` is a 'private cloud' within GCP (which is a public cloud). It stands for **V**irtual **P**rivate **C**cloud. `VPC` let's you create virtual versions of a physical network inside GCP. It serves as the host for our applications.

We use the `default` network as the host for all of our applications that require a network (cloud run, sql databases, etc).

[Check this document](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/TinyTechTidbits/VPC.md) for more info on VPC.

## Load Balancer

Serves as a 'middle man' between end-users and applications to re-distribute traffic between apps in the network.

Load Balancers in use:

- dwh-pipelines-url-map-url-map
  - This is a layer 7 load balancer. It maps traffic from a external (public) IP address to the cloud run application where Mage is running.

[Check this document](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/TinyTechTidbits/VPC.md) for more in-depth info.

## Cloud Armor

Security service that protects our applications from malicious attacks and unauthorized access.

[Check this document](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/TinyTechTidbits/cloud-armor.md) for more in-depth info

## NEG (network endpoint group)

Enables us to use load balancers with our cloud run applications.

`NEG` in use:

- dwh-pipelines-neg
  - `NEG` for the cloud run service hosting & running our Mage production server.
  - Is used with the `dwh-pipelines-url-map-url-map` load balancer.

[Check this document](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/TinyTechTidbits/NEG.md) for more in-depth info.

## Serverless VPC connector

These enable our serverless applications to interact seamlessly with other services in our network.

serverless `VPC` connectors in use:

- dwh-pipelines-connector
  - Gives Cloud Functions (& other apps) access to the `default` VPC network.
  - Used by Cloud Functions that need to interact with Mage production server (for ex: API triggers).
