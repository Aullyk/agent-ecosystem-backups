# Restore

On the data-plane machine, stack running (postgres only is enough):

```
docker compose exec postgres psql -U agent -d postgres -c 'DROP DATABASE control_plane WITH (FORCE);' -c 'CREATE DATABASE control_plane;'
docker compose exec -T postgres pg_restore -U agent -d control_plane < control_plane.dump
agentctl start
```
