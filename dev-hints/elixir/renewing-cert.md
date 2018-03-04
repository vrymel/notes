# Renewing cert

These are the steps I did when I renewed `waypoints.direct`

#### Notes
- Make sure port 80 is open in AWS security group
- Make sure port 80 is routed to the port (default 4000) that Phoenix is using


#### Steps

1. Run the application in development mode

        mix phoenix.server

2. Make sure the server is accessible over the internet via HTTP

3. Make sure `.well-known`  is accessible

    - Include .well-known in `lib/waypoints_direct/endpoint.ex`
    - Test [http://waypoints.direct/.well-known/test.html](http://waypoints.direct/.well-known/test.html) (create first test.html) if it is accessible over the internet

4. Run `certbot-auto` 

        ./certbot-auto renew
