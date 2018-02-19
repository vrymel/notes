# Renewing expired cert

These are the steps I did when I renewed (cert already expired) waypoints.direct

## Notes

- Make sure server is accessible, allow all port/IP to communicate to the server during cert creation/renewal
  - If in AWS EC2, check security group

1. Run the application in development mode

    mix phoenix.server

2. Make sure the server is accessible over the internet via HTTP

3. Make sure `.well-known`  is accessible

- Include .well-known in `lib/waypoints_direct/endpoint.ex`
- Test [http://waypoints.direct/.well-known/test.html](http://waypoints.direct/.well-known/test.html) (create first test.html) if it is accessible over the internet

4. Run `certbot-auto` 

    ./certbot-auto certonly

5. Select webroot in the option

6. Specify the domain

    waypoints.direct

7. Specify the application webroot

    /home/ubuntu/waypoints_direct/priv/static