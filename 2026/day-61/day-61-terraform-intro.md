# Day 61 -- Introduction to Terraform and Your First AWS Infrastructure

## Task 1: Understand Infrastructure as Code

1.	What is Infrastructure as Code (IaC)? Why does it matter in DevOps?

Answer:

Infrastructure as Code (IaC) is the management and provisioning of infrastructure such as networks, virtual machines, load balancers, etc. through machine-readable definition files (code) rather than manual, physical hardware configuration or interactive configuration tools.

3.	What problems does IaC solve compared to manually creating resources in the AWS console?

Answer:

Infrastructure as Code solves problems like human errors, inconsistency, slow manual setup, lack of documentation, and difficulty in scaling. By using tools like Terraform, we can automate infrastructure creation, ensure consistency across environments, track changes using version control, and quickly recreate infrastructure when needed.

5.	How is Terraform different from AWS CloudFormation, Ansible, and Pulumi?

Answer:

Terraform is a multi-cloud infrastructure provisioning tool using HCL, while CloudFormation is AWS-specific. Ansible is mainly used for configuration management inside servers, not infrastructure creation. Pulumi is similar to Terraform but uses general-purpose programming languages like Python and JavaScript instead of a declarative language.

6.What does it mean that Terraform is "declarative" and "cloud-agnostic"?

Answer: 

i.	Declarative means we define the desired state of infrastructure, and Terraform automatically figures out how to achieve it.

ii.	Cloud-agnostic means Terraform can be used across multiple cloud providers like AWS, Azure, and GCP, instead of being limited to a single cloud.

## Task 2: Install Terraform and Configure AWS

1.	Install Terraform: Installation in aws ec2 instance ubuntu OS: 

wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg  

<img width="1090" height="285" alt="image" src="https://github.com/user-attachments/assets/bc827777-ef86-4736-8f8a-af5076b7d102" />

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list  

<img width="1090" height="94" alt="image" src="https://github.com/user-attachments/assets/3eaa8efc-a407-4067-beee-415a6230abec" />

sudo apt update && sudo apt install terraform  

<img width="1090" height="244" alt="image" src="https://github.com/user-attachments/assets/816da892-fbf8-41a0-b1b4-0051e7a9d405" />

2.	Verify:  terraform -version

<img width="814" height="129" alt="image" src="https://github.com/user-attachments/assets/d7b580e7-ff43-4004-b514-aae64ea0c129" />

3.	Install and configure the AWS CLI:

   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

   <img width="1090" height="116" alt="image" src="https://github.com/user-attachments/assets/fb6e7fea-ce45-4817-9960-6fc63f752489" />

   unzip awscliv2.zip  

   <img width="939" height="388" alt="image" src="https://github.com/user-attachments/assets/34ad203e-d616-4e6e-8b80-f5f0e6e7806e" />

   sudo ./aws/install

   <img width="875" height="115" alt="image" src="https://github.com/user-attachments/assets/8df67444-2dca-4f00-85cf-f6ec5bc98052" />

   Verify: aws  --version

   <img width="1090" height="94" alt="image" src="https://github.com/user-attachments/assets/9ed3035d-d449-47d3-832c-114b96a7cd5a" />

configure the AWS CLI:

step 1: create a user in aws IAM and create security credentials for user 

<img width="1090" height="367" alt="image" src="https://github.com/user-attachments/assets/e5d17967-6c50-4882-bfb1-092caab784a8" />

<img width="1090" height="472" alt="image" src="https://github.com/user-attachments/assets/ee6be390-3aa8-4cd3-9bad-d55028566bc9" />

<img width="1090" height="490" alt="image" src="https://github.com/user-attachments/assets/31d3b83b-e6c4-4d0d-ace4-46f4f4447c4c" />

Step 2 : create a access keys in security credentials.

<img width="1090" height="319" alt="image" src="https://github.com/user-attachments/assets/2bec04af-0c02-4ef3-bb9e-20d513266cda" />

<img width="1090" height="438" alt="image" src="https://github.com/user-attachments/assets/e3ddb1a5-5151-4eb2-95c5-a398bfb9f96f" />

Step3 : Configure AWS CLI 

<img width="1090" height="176" alt="image" src="https://github.com/user-attachments/assets/15316581-164f-4177-b120-20fdc0982235" />

Step4: Verify AWS access: aws sts get-caller-identity

<img width="964" height="214" alt="image" src="https://github.com/user-attachments/assets/7d2e0670-a6a8-4f87-9f7e-889f4b0afcbe" />

## Task 3: Your First Terraform Config -- Create an S3 Bucket

Create a project directory and write your first Terraform config: 

mkdir terraform-basics && cd terraform-basics  

<img width="1090" height="89" alt="image" src="https://github.com/user-attachments/assets/ca3acaae-0635-43c0-8050-eb05a5be62e4" />

Create a file called main.tf with:

1.	A terraform block with required_providers specifying the aws provider

2.	A provider "aws" block with your region 

3.	A resource "aws_s3_bucket" that creates a bucket with a globally unique name

<img width="965" height="440" alt="image" src="https://github.com/user-attachments/assets/baf84fe5-d1e2-4a49-947a-ea9bacdf375f" />

Run the Terraform lifecycle: 

terraform init      # Download the AWS provider 

<img width="1090" height="526" alt="image" src="https://github.com/user-attachments/assets/8eb48d21-5aa9-4383-af3e-ef38ad4d81d0" />

terraform plan      # Preview what will be created  

<img width="1090" height="887" alt="image" src="https://github.com/user-attachments/assets/97e20c5c-25f1-41b3-a348-5c0bb4689385" />

terraform apply     # Create the bucket (type 'yes' to confirm) 

<img width="1088" height="1134" alt="image" src="https://github.com/user-attachments/assets/acce5d3b-2a6b-4c4b-9667-8e8e40b12147" />

AWS S3 console and verify bucket exists. 

<img width="1090" height="264" alt="image" src="https://github.com/user-attachments/assets/171681aa-d118-412f-9044-c2085b254338" />

Q. What did terraform init download? What does the .terraform/ directory contain?
  
  Answer: 
  
  terraform init downloads providers plugins hashicorp/aws V6.38.0
  
  .terraform directory contains providers directory 

## Task 4: Add an EC2 Instance

1.	A resource "aws_instance" using AMI ami-0f5ee92e2d63afc18 (Amazon Linux 2 in ap-south-1 -- use the correct AMI for your region)

2.	Set instance type to t2.micro

3.	Add a tag: Name = "TerraWeek-Day1"

<img width="921" height="698" alt="image" src="https://github.com/user-attachments/assets/c155d090-0732-4cd8-bad4-dc46bb28ac3a" />

terraform plan      # You should see 1 resource to add (bucket already exists) 

<img width="1090" height="396" alt="image" src="https://github.com/user-attachments/assets/8279040b-ae81-4af1-be99-283e41a3f246" />

terraform apply

<img width="1090" height="1087" alt="image" src="https://github.com/user-attachments/assets/d3989ce6-7845-4739-ab86-0b30bf8b8261" />

AWS EC2 console and verify instance is running with the correct name tag.

<img width="1090" height="501" alt="image" src="https://github.com/user-attachments/assets/a0312195-fee0-482c-9c27-e159d0316480" />

Q. How does Terraform know the S3 bucket already exists and only the EC2 instance needs to be created? 

Answer: 

Terraform uses a file  terraform.tfstate state file   
State File?  
It’s a JSON file where Terraform stores:  
•	What resources it has created   
•	Their current configuration   
•	Their real-world IDs (like S3 bucket name, EC2 ID)  

ran terraform plan  
Terraform does 3 things:
1.	Reads your code (main.tf)   
2.	Reads state file (terraform.tfstate)  
3.	Compares with actual AWS infrastructure  


## Task 5: Understand the State File

Terraform tracks everything it creates in a state file. Time to inspect it.  
1.	Open terraform.tfstate in your editor -- read the JSON structure

   <img width="1090" height="926" alt="image" src="https://github.com/user-attachments/assets/73be940b-578b-4255-9beb-3dc90c8a508b" />

2.	Run these commands and document what each returns:  
    terraform show # Human-readable view of current state
  	<img width="1090" height="931" alt="image" src="https://github.com/user-attachments/assets/a0e5c0e1-e87c-4ce6-8033-f5833110e63e" />  
    <img width="1090" height="1016" alt="image" src="https://github.com/user-attachments/assets/114d3a3c-918d-4641-a766-5dd269cadbc9" />

3. terraform state list                    # List all resources Terraform manages

   <img width="869" height="120" alt="image" src="https://github.com/user-attachments/assets/b977cc74-7aa1-4d34-883a-d9ce5520856c" />

4. terraform state show aws_s3_bucket.<name>   # Detailed view of a specific resource

   <img width="1090" height="1030" alt="image" src="https://github.com/user-attachments/assets/084e0aef-7d38-4160-aea7-55ac994def03" />

5. terraform state show aws_instance.<name>

   <img width="1090" height="611" alt="image" src="https://github.com/user-attachments/assets/1630fffa-b8d2-4bea-bc35-5993974cc795" />
    
Q1. What information does the state file store about each resource?  
Answer: The terraform.tfstate file stores real infrastructure details so Terraform can track resources.  
Resource ID → e.g., S3 bucket name, EC2 instance ID  
Resource type & name → aws_s3_bucket.kunalbucket  
Attributes (current state) → region, ARN, tags, IP address, etc.  
Dependencies between resources → which resource depends on another  
Metadata → provider info, version, etc.  

2. Why should you never manually edit the state file?  
Answer: Because it can break infrastructure management.   
State becomes out of sync with real AWS resources  
Terraform may:  
i.	Recreate resources   
ii.	Delete resources  
iii.	Fail during plan/apply   
iv.	JSON formatting errors → Terraform crashes  

3. Why should the state file not be committed to Git?  
Answer:  Because it contains “sensitive data + environment-specific info”  

## Task 6: Modify, Plan, and Destroy

1.	Change the EC2 instance tag from "TerraWeek-Day1" to "TerraWeek-Modified" in your main.tf  

  	<img width="1090" height="748" alt="image" src="https://github.com/user-attachments/assets/e044192e-5c27-4551-9a56-a7ee3ed47b62" />

2. Run terraform plan and read the output carefully:

   <img width="1090" height="490" alt="image" src="https://github.com/user-attachments/assets/613bec6f-06a8-418a-b9dd-8cca103fc1f0" />

What do the ~, +, and - symbols mean? 

Answer: 
i.	+:  New resource added/create  
ii.	-: resource delete/destroy  
iii.	~: resource Modified  
iv.	-/+: Replace (Destroy+create)  

3.	Apply the change :  terraform apply

  	<img width="1090" height="583" alt="image" src="https://github.com/user-attachments/assets/2fd4c38c-1879-458f-b64b-dda05a00eda1" />

4.	Verify the tag changed in the AWS console

   <img width="1090" height="489" alt="image" src="https://github.com/user-attachments/assets/c648e103-811f-4ce3-bc95-8dddeb44eeee" />

5.	Finally, destroy everything: terraform destroy

   <img width="1090" height="413" alt="image" src="https://github.com/user-attachments/assets/52c1ea3c-89a6-412e-9d60-c1f36cccfd12" />

6.	Verify in the AWS console -- both the S3 bucket and EC2 instance should be gone

   <img width="1090" height="170" alt="image" src="https://github.com/user-attachments/assets/298a3f2d-34f1-4619-996a-8c88e3e004dc" />  

   <img width="1090" height="329" alt="image" src="https://github.com/user-attachments/assets/f87dd605-2723-49aa-aec5-b891f0009b22" />

