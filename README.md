# Packer image Debian 10 with Nginx and Docker on GCP

This image is made into a Packer using Google Cloud capacities on which Debian 10, Nginx and Docker are installed.

If you want to download this image, then you need to fix the variables in the vars.json file:

>"product_images_project_id":
You will find this variable in the information about your project in Google Сloud Project ID

>"zone":Write any server zone that is convenient for you

>"product_name":Write any name your product

>"source_image_family":The original Image Family on the basis of which we make our image

>"image_description":just a description of your image

In the template file.json, I prescribed to use data from the account.json account to connect.
You need to create this file in your Google Cloud account
>Open the IAM tab

>Next, Service Accounts, and Create a service account to create it.

>Fill in the name and click Create.

>Next, we are offered to attach roles to our newly created account. 

>Roles are needed to allow an account to do something specific, for example, only run virtual machines.

>Choose two roles: Compute Instance Admin and Service Account User

>Next, be sure to create a key, click create, and select the JSON format

You will download the key, the name will be like:

>premium-student-2691809-dec8327adc1.json

Now it is important to rename it to account.json, and put it in the folder where the three Packer files are now.
Now we need to check if everything is fine with our files, you need to enter this command while in the folder with our files:
> packer validate -var-file=vars.json template.json

Then when you saw the message "Template validated successfully"
Run the command:
>packer build -var-file=vars.json template.json

You should have a message:
## Builds finished. The artifacts of successful builds are

By the way, you can always find your image by following the link:

> https://console.cloud.google.com/compute/images
