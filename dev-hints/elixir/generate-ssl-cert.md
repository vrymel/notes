# Generate SSL cert

## Pre-notes

- On initial certificate generation, run the application in HTTP only and make sure it can be accessed thru the browser.
- Make sure server is accessible, allow all port/IP to communicate to the server during cert creation/renewal
  - If in AWS EC2, check security group

---

1. Make sure .well-known is accessible by defining it in `Plug.Static` 

    vim lib/waypoints_direct/endpoint.ex
    	
    plug Plug.Static,
        at: "/", from: :waypoints_direct, gzip: false,
        only: ~w(css fonts images js favicon.ico robots.txt .well-known)

2. Run certbot in certonly mode

    ./certbot-auto certonly

3. Select `webroot`  as mode of authorization

4. Specify domain

5. Specify application webroot directory

    /home/ubuntu/waypoints_direct/_build/prod/lib/waypoints_direct/priv/static

6. Set key file and cert file in environments after certificates have been generated

    vim ~/.bashrc
    	
    # used in prod.exs
    export WAYPOINTS_DIRECT_KEY_FILE="/etc/letsencrypt/live/waypoints.direct/privkey.pem"
    export WAYPOINTS_DIRECT_CERT_FILE="/etc/letsencrypt/live/waypoints.direct/cert.pem"

7. Make sure config/prod.exs is properly configured to use HTTPS and pointing to the key and cert files

---

## Post-notes

- It is likely that *erlang* will not be able to access the certs, so change the permission of `/etc/letsencrypt`  to 755
  - There might be a better way to do this. But for now we do it this way.

Sources:

[https://medium.com/@a4word/phoenix-app-secured-with-let-s-encrypt-469ac0995775](https://medium.com/@a4word/phoenix-app-secured-with-let-s-encrypt-469ac0995775)

[https://medium.com/@zek/secure-your-phoenix-app-with-free-ssl-48ac749c17d7](https://medium.com/@zek/secure-your-phoenix-app-with-free-ssl-48ac749c17d7)

[Renewing expired cert](./Renewing-expired-cert-56d79bd8-d396-4811-bfba-6dbb74a506a2.md)