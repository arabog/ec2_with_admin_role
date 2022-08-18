# EC2 Instance with an Admin Role
## Introduction
You will create an EC2 Instance based on Amazon Linux AMI that you can connect via SSH. While provisioning the instance, you will make sure to limit access to your IP address only, using Security Groups.  

Once the instance is running, create an IAM role with admin access to your account. Then, attach the role to your EC2. In this case, the CLI tool will pick up the credentials from the role and won’t need hard-coded credentials.  

## Objectives
By the end of this exercise, you will be able to:  
Launch a secure EC2 instance  
Create IAM role with admin privileges  
Attach the IAM role to the EC2 instance created earlier  
Connect to your EC2 instance via SSH  
Use CLI tool in the EC2 instance  

### Step 1. Create a default VPC

![vpc1](vpc1.png?raw=true "vpc1")


### Step 2. Launch an EC2 instance
Navigate to the EC2 dashboard, and select the Instances services in the left-hand navigation pane.  
Use the Launch Instance wizard to launch an instance with the following configuration, and leave the remaining values as the defaults:  

![vpc2](vpc2.png?raw=true "vpc2")

*Security Group:	New. Limit access to your IP address only.*  

![vpc3](vpc3.png?raw=true "vpc3")

### Step 3. Create an IAM Role
Navigate to the IAM dashboard, and select the Roles services in the left-hand navigation pane.  
Click on the Create role button, and provide the configuration details, as follows.  

Select AWS service as the type of trusted entity, and choose EC2 service to assume the new role. It will allow the EC2 instance, to whom we will attach this role later, to be able to call any AWS service on your behalf.  

![vpc4](vpc4.png?raw=true "vpc4")

In the Filter policies textbox, search for the "admin" policy. Select the AdministratorAccess policy to apply to the new role.  

![vpc5](vpc5.png?raw=true "vpc5")

Provide a name to the new role, such as VocareumSecureServerRole, or choose any other name of your choice.  

![vpc6](vpc6.png?raw=true "vpc6")

![vpc7](vpc7.png?raw=true "vpc7")

![vpc8](vpc8.png?raw=true "vpc8")

### Step 4. Attach the Role to the EC2 Instance
Go back to the EC2 dashboard, and view the list of the running instances.  
Select the checkbox against the recently launched EC2 instance, and click the Actions button on the top of the list. It will open up drop-down options, select the Security → Modify IAM role option.   

![vpc9](vpc9.png?raw=true "vpc9")

On the next window, select and apply the newly created role, admin_role, to your instance.  

![vpc10](vpc10.png?raw=true "vpc10")

### Step 5. Connect to your EC2 instance
![vpc11](vpc11.png?raw=true "vpc11")

After connecting to your instance, verify the existing installation of AWS CLI, and run any AWS command, such as aws iam list-users.  

![vpc12](vpc12.png?raw=true "vpc12")

This is a convenient way to have a properly configured - and secure - server that you can use to test and not have to worry about credentials.  