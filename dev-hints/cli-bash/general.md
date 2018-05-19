# General

#### Adding a system user

    adduser <username>
    
    # add password to created user
    passwd <username>

#### Adding a user to a group

    usermod -aG <group> <username>

    # Adding current user to sudoer group
    usermod -aG sudo ${USER}

#### Check current users group memberships

    id -nG

