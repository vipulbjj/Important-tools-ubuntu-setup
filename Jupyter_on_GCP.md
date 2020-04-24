https://tudip.com/blog-post/run-jupyter-notebook-on-google-cloud-platform/
Step 1. Create or log in to a GCP account
You must have an account in google cloud platform with which all the billing will be carried with it. You can also create a free tier account here and receive $300 GCP credits to spend on Google Cloud Platform over the next 12 months.

Refer here for more details on GCP free tier account.

Step 2. Create or select a GCP project
In order to setup an instance, you need to select or create a project in GCP. Creating a project is simple, here’s how:

add-gcp-project 
Step 3. Setup a VM instance
In a new project, you must enable billing to use Compute Engine Service. Go to Compute Engine > VM instance and click “Enable billing”.
setup-vm-instance 
Click “Create” to create a new VM instance with the configurations below:
Instance Name: <Name your instance>
Select your nearest region and zone.
Region: asia-south1 (Mumbai)
Zone: asia-south1-c
Machine Type: select “8 vCPUs 30 GB memory, n1-standard-8 (You can increase the memory as per your need)
Boot Disk: Choose a Deep Learning Image(Pytorch or Tensorflow according to required version)
Boot disk type: Standard Persistent disk
Size(GB): 100
Keep “Identity and API access” as default.
Firewall: Click the checkbox to allow both HTTP and HTTPS traffic.
Click “Management, security, disks, networking, sole tenancy” to expand and go to Disks section.
Uncheck “Delete boot disk when the instance is deleted” deletion rule.
Click on the “Create” button.
Now your instance is ready!
Note: When you are not using your instance, you can stop your instance to save money. You can stop your instance by clicking Stop present under three dots menu.three-dots 
Step 4. Make External IP as Static
In order to access the Jupyter notebook, we need to make External Ip as static.
Go to Networking > VPC Network > External IP addresses.
You will see an external IP address of your instance, change the type from Ephemeral to Static.
You will see a popup window where you need to provide a name for the new static IP address and click Reserve.
Note: Make a note of your external IP address, you will require it later.
Step 5. Create Firewall Rules
On the same path, click Firewall rules (Networking > VPC Network > Firewall rules) and Click “CREATE FIREWALL RULE” with below configuration:
Name: <Enter a firewall name>
Targets: All instances in the network
Source IP ranges: 0.0.0.0/0
Protocols and ports: Select “Specified protocols and ports” option.
tcp: 8888 <You can change any other port number>
Keep other configuration as default.
Click on the Create button.
firewall-rules 
