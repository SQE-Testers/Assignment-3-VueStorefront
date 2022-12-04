# Reliability of VUE Store Front
Vue Storefront Cloud is a blazing fast cloud infrastructure fitted to Vue Storefront. The cloud isn't only a compute power. There are intelligent algorithms to optimize and speed-up VSF instance.

## Problems solved by Cloud

- Slow Performance 
- Lack of Flexibility
- Enhanced Scalability 
- Security

## Kubernetes & Google Cloud Platform
Vue StoreFront uses Kubernetes - the best, Google-originated orchestration tool globally - and team it with Google Cloud Platform. It facilitates large-scale eCommerce run as fast as possible.So use of Kubernetes and Containers helps in scalability  and availability of the VueStorefront.

### Kubernetes
Containers are a good way to bundle and run your applications, these container make sure that no downtime occurs in a website.For example, if a container goes down, another container needs to start.Kubernetes provides you with a framework to run distributed systems resiliently. It takes care of scaling and failover for your application, provides deployment patterns, and more.


## Recoverability 
Support team provides daily backups, which makes testing new solutions safely. Daily backups by default makes business consistency perfectly secured. With daily back we will have our data secured. So for example if someone tries to attack our system then we still have our data and we can use it.
No one can black mail us.Moreover if one component is down then other componenets remain intact and can be used.

## CDN
Google Cloud CDN supports modern protocols initially developed at Google, like HTTP/2 and QUIC. These protocols have the ability to serve the thousands of requests per day and hence help in load balancing.

### QUIC
QUIC is a general-purpose transport layer network protocol.In conventional TCP connection we have to make three network round trip of transfer between client and Server and it costs alot of time when server is very far away from client.But in QUIC we have super fast one round trip of network which makes the Performance and reliablity and Avalilainility of application.
Vue Storefront uses this QUIC to make it's applications faster.

## Automatic deployments
Each deployment is managed via storefrontcloud-cli and the GitLab repository.A fully automatic deployment flow with the evidence of changes (git-log) and a simple restore process in case of any failure. This eleiminates the human errors.

#### StoreFrontCloud- Command Line Access
The Storefront Cloud CLI tool is designed to let you manage your Storefront Cloud namespaces.

##### Installation
First, install storefrontcloud-cli (requirements: node 8.x+, yarn):

```bash
git clone https://github.com/StorefrontCloud/storefrontcloud-cli.git`
cd storefrontcloud-cli
yarn install
```

## References
- [Features Documentation ](https://docs.vuestorefront.io/cloud/v2/in-a-nutshell/features.html#hosting)
- [Kubernetes Documentation ](https://kubernetes.io/docs/concepts/overview/)
