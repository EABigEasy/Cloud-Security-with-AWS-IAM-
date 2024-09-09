AWS  Services Used in this Project.
💻 EC2 instances
📏 IAM Policies
🔖 AWS Account Alias
👩‍👩‍👧‍👧 IAM Users and User Groups


<img width="645" alt="architecture" src="https://github.com/user-attachments/assets/ce503640-5052-45e6-ac80-be3a69b3d6bf">



1.Launching 💻 EC2 instances with tags.

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
we create Policies, then attach to IAM Groups, Then add IAM users to our IAM groups.
This is different from a Resourcce Policy.

Key information of an  IAM Policy is " Statement, Effect, Resource,Action, Condition ".
Action : what services
resource: * means all. 
Effects are: allow. deny,notaction
Select Create Policy, we can use visual steps or JSON.

Sample json code is :
```json
{    
  "Version": "2012-10-17",    
  "Statement": [        
    {            
      "Effect": "Allow",            
      "Action": "ec2:*",            
      "Resource": "*",            
      "Condition": {                
        "StringEquals": {                    
          "ec2:ResourceTag/Env": "development"                
        }            
      }        
    },        
    {            
      "Effect": "Allow",            
      "Action": "ec2:Describe*",            
      "Resource": "*"        
    },        
    {            
      "Effect": "Deny",            
      "Action": [                
        "ec2:DeleteTags",                
        "ec2:CreateTags"            
      ],            
      "Resource": "*"        
    }    
  ] 
}

```
Click on the Visual to see the resources permissions. Then Create Policy name similar to the tags environment e.g NextWorkDevEnvironmentPolicy


3. Create An AWS account Alias.
   
An Account Alias is a friendly custom name for your AWS account that you can use instead of your account ID (which is usually a bunch of digits) to sign in to the AWS Management Console.

Your AWS account's sign-in page has this URL by default: https://Your_Account_ID.signin.aws.amazon.com/console/

If you create an AWS account alias for your AWS account ID, your sign-in page URL looks more like: https://Your_Account_Alias.signin.aws.amazon.com/console/

Go to IAM Dashboard, Create an AWS Account Alias

4.  👩‍👩‍👧‍👧 IAM Users and User Groups. 
Create an IAM user Group, e.g a group name like "nextwork-dev-group"

then add IAM Policies. Add the created policy "NextWorkDevEnvironmentPolicy" 

Create an IAM user to add to the IAM User Group.
Create a user, check the mark  management console access, but for now add the user to a group by selecting "attach permissions from a group".
Download csv file after creating user to have it saved.

Remember we can  create Policies, then create IAM user Groups then attach policies to the IAM user Groups. Then Cretae IAM users and add to our IAM groups.



5. Test User's Access.
Copy the "Console sign-in URL"  Do not close this tab!
Open a new incognito window on your browser.
Open the new console sign-in URL in your incognito window.
Using the User name and Console password given in your IAM tab, let's log in!

As a new user, the AWS console will treat you as someone that is starting from 0 again. Awesome for the new team member that you'll be giving this User to!

As a new user, you'll notice that some of your dashboard panels are showing "Access denied" already!

If you try to stop an instance like "Production Instance" it will fail because you were not authorized with permissions to do that. 

Only development instance you have permissions to. remember IAM policy stringEqauals to development EC2 tag.

Try to stop development instance, you'll see that you can.

### Understand Zero Trust Policy ###
### Understand Principle of Least Priviledge access ###

## End of Project 1.##

















