# Sumer project metarepo

This repo acts as the bucket that hosts all the repos that build up the sumer project. 

## What is this thing?

Sumer is a sample project that tests ideas about a future where social media content is stored on a standardized set of smart contracts running on the Polygon blockchain.

In this alternate future, the chain holds the social media content as nfts, giving users complete control over their own content, while exposing them to the consequences of any mistreatment they may induce. This would probably result in content that is mostly noise, with some gold sprinkled here and there.

Consumers of the social media content can then use a dapp of their own choice to access the decentralized social media content, with nothing inbetween them and the chain. The content could be reinterpreted differently depending on the design of the dapp, and some metadata specified in the social media standard.

However, most users probably wouldn't want to access an endless slue of unstructured dribbles created by people (and likely machines) from all around the planet, and would want some kind of filtration or curation applied over the data.

This is where private companies and open source organizations would come in, providing data on which posts qualify for what kinds of content lists. These lists could be created by web2 companies that use AI and/or other methods, and by web3 daos which use oracles and governance contracts to decide which content fits in certain niches. 

Advertising would probably be the main source of revenue for the filtration layer but I would also expect them to promote some content over others. These two could of course end up being the same thing eventually. 

Dapps would probably make money by either showing ads of their own or promoting certain filters above others. Considering that filtration would be a rather abstract layer, it's very likely that fitration companies would create their own apps to promote their own backend services. Dapps could also make money by transfer of nfts within the social media system.

Miners would of course make their money by storing the social media data on the chain.

## How do I run this thing?

The project consists of a bunch of different repos. You will need to clone all of them to run the system. If you just want to browse the code, there are some instructions below on how to do that.

### Cloning the project repos

This project is structured as a metarepo. The repo you are currently viewing is the root, and acts as a container for all other components of the project. You can clone the rest of the code by running `git meta sync`. This requires python's [metarepo](https://pypi.org/project/metarepo/) library and [Terraform](https://www.terraform.io/) to be installed on the system. 

If you don't want to install the said library, you can instead go through `manifest.yml` to manually clone the repos that are relevant to you. Note that the repos need to be cloned to custom paths declared at `path` property of each entry. Otherwise, repos that rely on each other for their build operations will fail.

### Running the project in a local environment

Once you clone the entire project, follow these steps:
1. Head to `infrastructure/local`. This dir houses the terraform code for local provisioning.
1. Run `scripts/replace-images.sh`. This will create docker images for repos that need a custom image.
1. Run `terraform init` to initialize terraform.
1. Run `terraform apply`, check the output and type `yes` if you are content with what you see.
1. In a while, the cluster should be running in 3 namespaces.

## I just want to browse the code

If you just want to peek at the code, here is the list of the repos:

* [WebDapp](https://github.com/utkusarioglu/sumer-web-dapp): Browser dapp
* [Project](https://github.com/utkusarioglu/sumer-project): UML diagrams and other documentation
* [Ingress](https://github.com/utkusarioglu/sumer-ingress): Ingress controller for the kubernetes cluster
* [Namespaces](https://github.com/utkusarioglu/sumer-namespaces): Kubernetes namespaces
* [Infrastructure](https://github.com/utkusarioglu/sumer-infrastructure): Terraform code to run the cluster on different environments
* [Wasm](https://github.com/utkusarioglu/sumer-wasm): WebAssembly component for the dapp
* [Kafka](https://github.com/utkusarioglu/sumer-kafka): Kafka cluster helm charts using strimzi operator
* [Ethereum Dispatcher](https://github.com/utkusarioglu/sumer-ethereum-dispatcher): Microservice for dispatching ethereum data to the cluster
* [Ethereum Contracts](https://github.com/utkusarioglu/sumer-ethereum-contracts): Ethereum/Polygon smart contracts for the social media
* [Env IC](https://github.com/utkusarioglu/sumer-env-ic): Environment Variables InitContainer
* [Rest Gateway](https://github.com/utkusarioglu/sumer-rest-gateway): Rest gateway
* [Secrets](https://github.com/utkusarioglu/sumer-secrets): Helm chart for kubernetes secrets. Actual secrets are all masked as "secret-dummy-value".
* [Websocket Gateway](https://github.com/utkusarioglu/sumer-websocket-gateway): Websocket gateway
* [Kafka Consumer IC](https://github.com/utkusarioglu/sumer-kafka-consumer-ic): Kafka consumer init container
