# Demo

### 1. Create a new mix project

    > mix new demo --sup

The `--sup` flag tells mix to stub out an application process. We'll use this later to start our
Ecto repo.

### 2. Open `./demo/mix.exs` and add `ecto` and `postgrex` dependencies

    defp deps do
      [
        {:ecto, "~> 2.0"},
        {:postgrex, "~> 0.11"}
      ]
    end

### 3. Generate a new Repo

    > mix deps.get
    > mix ecto.gen.repo -r Demo.Repo

Add the Repo supervisor to `./lib/demo/application.ex`

    def start(_type, _args) do
      children = [
        Demo.Repo,
      ]

      ...
    end

Update the repo config in `./config/config.exs`

    config :demo, Demo.Repo,
      adapter: Ecto.Adapters.Postgres,
      database: "demo_dev",
      username: "postgres",
      password: "postgres",
      hostname: "localhost"

    config :demo, ecto_repos: [Demo.Repo]

### 4. Create the Database

    > mix ecto.create

Heads Up! If you get an error here, run `psql postgres -c "CREATE ROLE postgres LOGIN CREATEDB;"`

### 5. Create our first table

    > mix ecto.gen.migration create_albums

### 6. Add Demo.Album

### 7. Add Demo.Album.Changeset

### 8. Add Demo.Album.Query

### 9. Add Demo.Track
