# rsync

#### Target remote

    rsync -avz --progress \ 
        remoteuser@remotehost:/directory/file \
        ~/destination_directory/file

#### Target remote with identity file

    rsync -avz --progress -e "ssh -i '~/certs/cert-file.pem'" \
       remoteuser@remotehost:/directory/file \
       ~/destination_directory/file 

#### Sync directories

    rsync -avz --progress dir1/ dir2

The trailing `/` in the first directory is important as it indicates the contents of `dir1` should be sync to dir2. Without it the sync would result in `dir2/dir1`.

