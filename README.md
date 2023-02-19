# A start with Cloud Computing (Google Cloud Platform)
What is Cloud Computing?
On-demand delivery of computer power, databases, storage applications, and other IT resources through the internet with pay-as-you-go pricing.

In this article, I’ll tell you how to create a new Linux VM instance on the Google Cloud Platform. Google Cloud Platform provides different cloud computing services.

Google Cloud Platform
Creation/Registration on the Google Cloud Platform
Before starting we have to create an account on the Google Cloud Platform, for this, we have to select the options accordingly. While creating we have to provide a Credit card or any other card number. So far Google gives you free $300 credits for 90 days after then it will charge from the account.

Register and Create a VM Instance
Follow the following steps in order to create a VM instance:

1. 1. Open the Navigation menu

2. Go to Compute Engine

3. Select VM instances

4. Click on Create Instance

5. Specify the name of the machine. Keep in mind that the name should follow the requirements that are length between 1–63, start with a lower letter, should not end with a hyphen

6. Assign labels in key, value format

7. Select the region and zones but we cannot change them after the creation

8. After then select the options accordingly

After checking the cost and reviewing the information press the create button

Configure SSH keys for secure access to the VM
1. Download it from URL https://cloud.google.com/sdk/docs/install

2. Install the program. After Installation makes sure that the run command on the CLI checkbox is checked. It will run gcloud command and connect it with our account. It opens a window where we can sign in to our account.

3. Select the project in CLI by entering its id

4. Select the Region and Zone

5. First, using CLI, To add a public SSH key to our account use gcloud compute os-login ssh-keys add. Here is the syntax

gcloud compute os-login ssh-keys add \
 - key-file="PUBLIC_KEY_FILE_PATH" \
 - project=PROJECT \ (optional)
 - ttl=EXPIRE_TIME (optional) 
    -> (s for seconds, m for minutes, h for hours, and d for days)
→ First create an SSH key using the ssh-keygen command on CLI

→ Use a public key file (that is with .pub)

Or
6. Or second, using Google Cloud Platform, Open Google Cloud Platform and go to VM instances

7. Select the instance, and make sure your instance is running

8. Click on the Edit option

9. In SSH key section, click on the Add item button to add your public SSH key with some details given below

→ ssh-rsa (public key)= google-ssh {“userName”:”Username”,”expireOn”:”Date”}

-> Date Example — 2023–02–18T08:16:23+0000

10. Click on add item and save

Note: For using gcloud, make sure that you are running gcloud commands in their respective folder which is Cloud SDK in my case.

Access the VM using SSH
There are many ways to connect to VM using SSH. For example, Console, gcloud, OpenSSH client, PuTTy app, and Secure Shell Chrome app.

Using gcloud

gcloud compute ssh --project=PROJECT_ID --zone=ZONE VM_NAME
• PROJECT_ID: the ID of the project that contains the VM
• ZONE: the name of the zone that the VM is located in
• VM_NAME: the name of the VM
Using OpenSSH client

ssh -i “PATH_TO_PRIVATE_KEY” USERNAME@EXTERNAL_IP
• Username used in the ssh-key
References

https://www.youtube.com/watch?v=jVPPQ8jCFrE&t=3s

https://www.youtube.com/watch?v=JGcW1QdEQGs

https://cloud.google.com/compute/docs/connect/standard-ssh
