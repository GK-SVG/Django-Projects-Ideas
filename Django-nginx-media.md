# How to give Django media files permission to nginx
```shell
#Add nginx user and user group to media file
sudo chown -R www-data:www-data /your_django_media_path/media/

# Give read file permission to nginx user
sudo chmod -R 755 /your_django_media_path/media/

# If media files are inside multiple directories then you have give read permission for all directories

sudo chmod 755 /root/project_directory/
sudo chmod 755 /root/

#Restart Nginx Server
sudo systemctl restart nginx

```