Hey there, recently I've setup this brilliant product on my server and uploaded all my pictures. However, my disk is now at 90% usage and it will soon be full. My solution to that would be to add a new drive, which is going to be dedicated to storing images.  
How do I safely migrate all the images which I have already uploaded to the new drive, without corrupting anything? Immich is currently running in a standard docker-compose config, as advised on the wiki.

These are the steps I'm planning on taking:

1. stop the entire stack
2. mount the new drive
3. copy over the entire folder specified in `UPLOAD_LOCATION`
4. change the `UPLOAD_LOCATION` env variable to the new directory
5. start the immich stack again with `docker-compose up -d --force-recreate`
6. check whether all the images are still available via the web interface
7. delete the original folder




I guess we can divide this into few steps:

1. Stop the current immich server on Portainer.
    
2. Copy all the files at the current root upload folder to your intended upload location
    
3. Edit the environment variable UPLOAD_LOCATION in portainer to your desired new location. You will need to click the edit/make a duplicate button on portainer
    
4. Start immich on portainer
    
5. backup a new picture
    
6. check that you see the new picture in the new folder, and not in the old folder
    
7. delete the old folder