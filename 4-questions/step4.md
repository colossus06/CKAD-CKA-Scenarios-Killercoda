
# Create a multi-container pod desin

You are going to create a multi-container Pod named `logger` from `multi.yaml` file for real-time logging purposes. Create the manifest file, name the main application container `main`, and use image `nginx`. 

Name the second container `helper` using another `nginx` image. Specify the commands 'less +F /var/log/nginx/access'.

Create an `emptydir` volume named and mount it to `/var/log/nginx` for main and helper containers.