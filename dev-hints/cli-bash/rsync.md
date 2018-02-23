# rsync

Target remote

    rsync -avz --progress \ 
        remoteuser@remotehost:/directory/file \
        ~/destination_directory/file

Target remote with identity file

    rsync -avz --progress -e "ssh -i '~/certs/cert-file.pem'" \
       remoteuser@remotehost:/directory/file \
       ~/destination_directory/file 