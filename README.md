#this is to make a reverse proxy
# to do that you need to change the sites-enabled/default file in Nginx
#therefore create a synced_folder link with the updated file in your vagrantfile/ provision
# the file it self requires location ...

# this is for the server to also include images etc...
location ~ ^/(images|javascript|js|css|flash|media|static)/  {
root    /home/ubuntu/app/public;
expires 30d;
  }
# this one for the actual server proxy 
location / {
        proxy_pass http://localhost:3000/;
