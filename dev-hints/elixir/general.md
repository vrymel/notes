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
