
# Create a multi-container pod desin

Create a Multi-container Pod with the name `logger`.

You are going to create a multi-container Pod named `logger` from multi.yaml for real-time logging purposes.
Name the main application container as `main`, use image nginx. Name the second container `helper` use another nginx image. Specify the commands 'less +F /var/log/nginx/access'.

Create an emptydir volume named and mount it to /var/log/nginx for main and helper containers.