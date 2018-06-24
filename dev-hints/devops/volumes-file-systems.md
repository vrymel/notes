# Volumes/File systems

#### List volumes and mountpoints

    lsblk

#### Check if volume has a file system

    file -s [/dev/xvdb]

#### Format volume to a file system

    mkfs -t [ext4] [/dev/xvdb]

#### Mount volume to a directory

    mount [/dev/xvdb] [/projects]

#### Unmount volume

    umound [device name or mount point]

