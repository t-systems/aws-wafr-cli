# Optimizing Well-Architecting reviews with aws-wafr-cli

**aws-wafr-cli** is a tool to manage workloads of the Well-Architected Tool. Most important features are the import and export functionalities and the management of custom lenses.

## Why have we created this CLI tool?

At **Deutsche Telekom IT** and **T-Systems** we are managing large AWS Organizations. Both divisions provide to its customers an own Landing Zone solution. For internal and external customers also.

During the reviews done for these customers every time we had a part which was a repetition. A big part of the workload questions was solved with the Landing Zone solutions.

We wanted to store these answers somewhere so when we had our next reviews, we could import them into the Well-Architected Tool. So, we came up with the **aws-wafr-cli** which can export and import these preconfigured answers and notes. 

It can also export answers marked in the WAF tool. These exported answers are saved into a yaml file, which then can be stored in a source control repository for further usage.   

Now this tool is used to create the workload for our reviews. Whenever we initiate one for a new customer, we just select the template relevant for the account type and start with that the creation of the workload.

## Managing the templates

The Landing Zone provided by both divisions are continuously evolving, so these changes should also be added to the stored templates. To update a template either we edit the yaml file directly or we import the template into a new workload, edit the changes in the AWS Well-Architected tool and then export the changes back to the template. After this just needs to be committed into our repository.

## Handling custom templates

Some of our customers do use EKS workloads. These workloads can also be reviewed with the WA framework but using a Kubernetes orchestration brings in a lot of other aspects which are not covered by the standard question-set of the framework.

With the support of AWS professional services, we built an own custom question-set specialized for EKS workloads. The practice which we took over from AWS was not based on the WA tool but we needed those questions also in it. 

To solve this problem, we updated the aws-wafr-cli to be able to handle custom WA lenses. So now the tool can be used to manage custom lenses and based on these custom lenses the tool can also create the workloads and of course it can also handle templates based on these custom lenses. 

## Other use-cases

The tool was useful in other situations too. One is when we needed to migrate a workload from an external account into our organization’s account. The review was started by an AWS Solution Architect on and AWS account. But we needed the workload in our account. Now using the **aws-wafr-cli** we could easily export the already answered question and then import it into our own account.
## About the CLI
Our tool is available as an open source on github: <https://github.com/t-systems/aws-wafr-cli>.

It is written in python and uses the AWS wellarchitected service client APIs.

More information about the usage is available in the readme.md of our repository.

## Template structure

There is an example of the template which can be imported into the WA tool:

<https://github.com/t-systems/aws-wafr-cli/blob/main/templates/standard.yaml>

