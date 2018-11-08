## Discourse deployment in Kubernetes

Prerequisite:

- Have a Postgres and a Redis instance running



Steps:

1. Create `discourse` user and database in PostgreSQL. Ensure that `discourse` is a superuser unless it cannot create extension `hstore`
2. Copy web_only.yml to `discourse_docker/containers` and edit it to meet your need
3. Build Docker image using `./launcher bootstrap web_only`. If you want to upload image to your private hub, you can do so.
4. Edit `k8s_deploy/01pvc.yaml`. Typically you would like to change storage class. I use nfs here.
5. Edit `02discourse.yaml` and `03service.yaml` if you need to. This is entirly optional.
6. `kubectl apply -f k8s_deploy` and you will see your app running. Use [ClusterIP]:80 to see your app now.



References:

- https://medium.freecodecamp.org/how-to-set-up-an-internal-team-forum-in-half-a-day-using-discourse-b13588d907fe
- https://github.com/discourse/discourse_docker
