# cron

`cron` is executed per user. 

#### To add a task for the current user

    crontab -e

#### List tasks for the current user

    crontab -l

#### Allow cron for user

On some Linux distro, `cron` is only enabled for the `root` user. Specify the user in the `/etc/cron.allow` file so the system will execute the tasks for the user.

    cat /etc/cron.allow
    # /etc/cron.allow contents
    centos
    anotheruser

One user per line.