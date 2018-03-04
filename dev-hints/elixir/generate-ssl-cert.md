# Generate SSL cert

#### Steps

1. Make sure `.well-known` is accessible by defining it in `Plug.Static` 

        vim lib/waypoints_direct/endpoint.ex
    	
        plug Plug.Static,
            at: "/", from: :waypoints_direct, gzip: false,
            only: ~w(css fonts images js favicon.ico robots.txt .well-known)

2. Run application in HTTP mode

        mix phoenix.server

    - Make sure port 80 is open in AWS security group
    - Make sure port 80 is routed to the port Phoenix is using

3. Run certbot in certonly mode

        ./certbot-auto certonly

4. Select `webroot`  as mode of authorization

5. Specify domain

        waypoints.direct

6. Specify application webroot directory

        /home/ubuntu/waypoints_direct/_build/prod/lib/waypoints_direct/priv/static

7. By this point the certs should be generated. Take note of the locations of the certificates.

8. Set the _key file_ and _cert file_ in `.env` 

        cd <project directory>

        vim .env
        # used in prod.exs
        export WAYPOINTS_DIRECT_KEY_FILE="/etc/letsencrypt/live/waypoints.direct/privkey.pem"
        export WAYPOINTS_DIRECT_CERT_FILE="/etc/letsencrypt/live/waypoints.direct/cert.pem"

        source .env

9. Make sure `config/prod.exs` is properly configured to use HTTPS and pointing to the key and cert files

10. Stop the application running in HTTP.

11. Run application in HTTPS mode.

---

## Notes

- It is likely that *erlang* will not be able to access the certs, so change the permission of `/etc/letsencrypt`  to 755
  - There might be a better way to do this. But for now I do it this way.

Sources:

[https://medium.com/@a4word/phoenix-app-secured-with-let-s-encrypt-469ac0995775](https://medium.com/@a4word/phoenix-app-secured-with-let-s-encrypt-469ac0995775)

[https://medium.com/@zek/secure-your-phoenix-app-with-free-ssl-48ac749c17d7](https://medium.com/@zek/secure-your-phoenix-app-with-free-ssl-48ac749c17d7)
