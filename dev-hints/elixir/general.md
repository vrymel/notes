# Elixir

## Loading associations

    iex> WaypointsDirect.Repo.preload(<changeset or model>, :association_name>)
    
    iex> WaypointsDirect.Repo.preload(route_edge, :from_intersection)

## Create changeset without using build_assoc

    iex> changeset = RouteEdge.changeset(%RouteEdge{from_intersection_id: 10, to_intersection_id: 11})

Changeset will not be loaded when using this method, do a preload if the association model is needed.

## Recompile application in iex

    iex> IEx.Helpers.recompile()

## Turn off char list display

    iex> IEx.configure inspect: [charlists: false]
    
    IO.inspect(:variable, charlists: :as_lists)

## Using Ecto.Query in iEX

    iex> import Ecto.Query

## Debugging Ecto generated SQL

    iex> query = Ecto.Query.where(Post, [p], p.views > 10)
    iex> Ecto.Adapters.SQL.to_sql(:all, Repo, query)

[Syntax](./Syntax-3bfde798-4956-4d93-b4bd-97858ed3aec6.md)

[Install Erlang in Ubuntu 16](./Install-Erlang-in-Ubuntu-16-e7ede586-5861-4343-8db4-7c2450f57f3c.md)

[Release Phoenix framework](./Release-Phoenix-framework-2d4ce9b2-72fb-4795-b77d-d8e38834b4ae.md)

[Generate SSL cert](./Generate-SSL-cert-7280f6fd-e621-46b5-b503-47be458d9e7a.md)