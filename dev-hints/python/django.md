# Django 

#### Migration rollback

    python [manage.py](http://manage.py/) migrate <app name> <migration number>
    
    python manage.py migrate schematics 0011

In the example, the current state of the database is on migration 0012, running 0011 will revert migration 0012.

#### Running Celery task runner

    celery worker -A schematics

#### Running Redis server

    src/redis-server