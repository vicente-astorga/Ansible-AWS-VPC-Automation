## Ansible AWS VPC Automation

By automating the deployment of infrastructure in the cloud, we **save time** on manual and repetitive tasks and in this way we become more agile, which is our goal as DevOps.

### **Infrastructure**

The automated construction of the VPC is done with the Ansible Playbooks that contain the necessary variables, configurations and modules. These modules use Python BOTO which makes the API calls to the AWS cloud. The project runs from an EC2 instance (ansible 2.12.0 - python3) with its respective role.

### Functioning

It start by configuring the VPC that has **three** public subnets and **three** private subnets in different zones. For public subnets, all outgoing traffic from the instances associated to its **route table** is routed through the **Principal Gateway.** For private subnets, the instances associated to its **route table** can access to Internet through the **NAT Gateway** (blocks incoming requests), which is located inside the public subnet. The creation of the **Nat Gateway** and the **Bastion host** is only done in the first subnet to avoid cost overruns.

Within the private subnet there is a **Bastion host** (Jump server) with its corresponding security group that allows the connection to the internet to the instances in the private subnet of the same zone

![Alt text](/files/diagrama.jpg "Image")
