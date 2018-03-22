# Release Phoenix framework

1. If using environment variables in local .env

        source .env

2. Prepare production configuration file `config/prod.exs`

        config :waypoints_direct, WaypointsDirect.Endpoint,
          # http: [port: 4000],
          https: [port: "${PORT}",
                  keyfile: System.get_env("WAYPOINTS_DIRECT_KEY_FILE"),
                  certfile: System.get_env("WAYPOINTS_DIRECT_CERT_FILE")]
          url: [host: "${HOST}", port: "${PORT}"],
          cache_static_manifest: "priv/static/manifest.json",
          server: true,
          root: ".",
          version: Application.spec(:waypoints_direct, :vsn)

3. Run initial setup commands

        mix deps.get --only prod
    
        MIX_ENV=prod mix compile

4. Compile assets

        cd assets
    
        npm install
    	
        ./node_modules/.bin/brunch build --production
    	
        cd ..
    
        MIX_ENV=prod mix phx.digest

5. If fresh deployment run

        MIX_ENV=prod mix ecto.create

6. Run migrations

        MIX_ENV=prod mix ecto.migrate

7. Release command, needs distillery dep

        source .env
    
        MIX_ENV=prod mix release --env=prod

8. Since Elixir by default can't access port 80 (any port below 1024) we need to route port 80 to the port Phoenix is using, example 4000

        sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 4000
    	
        sudo iptables -t nat -D PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 4000

or if https

        sudo iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports 4000
    	
        sudo iptables -t nat -D PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports 4000

To remove entry, just replace -A to -D before PREROUTING

9. Run Phoenix server

        REPLACE_OS_VARS=true HOST=waypoints.direct PORT=4000 _build/prod/rel/waypoints_direct/bin/waypoints_direct [start|console|foreground]

## Notes

- Server that is used for building must have erlang, elixir and should be the same versions in production. This would not be a problem if we are using the same server to build and run/deploy the application.
- Make sure to check values in rel/config.exs, for easier deployment set *include_erts* to *true*
- *REPLACE_OS_VARS* flag is important for the template strings in *prod.exs* to work
- Rerouting port 80 to the port Phoenix is listening is one way to remedy the port 80 restriction.
  - Another is to add permission for the *erl* binary to listen to the restricted ports. See [https://elixirforum.com/t/whats-the-best-way-to-serve-restricted-ports-e-g-80-443-with-phoenix/2841](https://elixirforum.com/t/whats-the-best-way-to-serve-restricted-ports-e-g-80-443-with-phoenix/2841)
  - Using a reverse proxy like *nginx* is also an option, although the community states this is not necessary unless the application is under heavy traffic.
- Note if server was restarted issue the iptables command again