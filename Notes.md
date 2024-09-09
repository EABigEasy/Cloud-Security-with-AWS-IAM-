AWS  Services Used in this Project.
💻 EC2 instances
📏 IAM Policies
👩‍👩‍👧‍👧 IAM Users and User Groups
🔖 AWS Account Alias


1. Launching 💻 EC2 instances with tags.

We launch 2 Instances, 
First Instance is created name NextWorkProduction and with with production tag e.g  Key : env Value  :production
Second Instance is created name NextWorkDevelopment and with development tag e.g Key : env Value  :development
   Every EC2 instance must have a unique name in its AWS Region.
    Tags are necessary to identify and manage Instances and resources in multi resource deployment situations.
      For example Key : env 
                  Value  :production or development

 Note : What is a key pair? Why does it say (Not recommended) next to proceeding without one?

A key pair is primarily used for accessing your EC2 instance securely without going through the AWS Management Console. 
Instead of the Management Console, you're using SSH (Secure Shell) Access with your key pairs - this is out of scope for this project,
but you'll learn more about SSH and key pairs in a networking or compute-themed project!

Proceeding without a key pair means you won't have SSH (Secure Shell) access to your instance,
which is generally not recommended because it limits your ability to troubleshoot or manage your EC2 instance through a secure way outside of the Console. 
It's always safer and more flexible to have a key pair set up, so you would create a key pair for bigger projects that you work on over a longer period of time.

2.📏 IAM Policies
IAM manages  access to our AWS Resources.
we create Policies attach to IAM Groups, Then add IAM users to our IAM groups.
This is different from a Resourcce Policy.

Key information of an  IAM Policy is " Statemetn, Effect, Resource,Action".

Select Cretate Policy, we can use visual steps or JSON.

Sample json code is :

























