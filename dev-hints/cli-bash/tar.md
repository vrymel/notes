# tar

Create an archive named `personal_directory.tar.gz` of the `personal` directory

Basic tar

    tar cvf personal_directory.tar personal

Tar with gzip

    tar cvfz personal_directory.tar.gz personal

Tar with bz2

    tar cvfj personal_directory.tar.gz personal

#### Unzip

    tar -xvf personal_directory.tar.gz