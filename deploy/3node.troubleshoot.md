# Guide for basic troubleshooting
> Caution: Don't stop the stop the db machine without stopping all dbs manually, else there can be data corruption.
1. While installing some step failed.
    1. re running the installation script will fix the problem on most cases.
2. After installation if you're getting 502 error  
   1. login to core machine
   2. `kubectl rollout restart deployment -n dev`
   3. `watch kubectl get po -n dev`
   4. wait for all pods to come up
3. Default username and password for keycloak is `admin` `admin`  
   For security reasons Keycloak is only exposed in private network  
   Refer to change password: [change the username and password](https://www.keycloak.org/docs/latest/server_admin/index.html#server-initialization)
4. All kong admin operations can be done against `<core-ip>:12000/admin-api/`  
   for example, To get consumer key and secret to create jwt token from kong:
    ```
    curl http://localhost:12000/admin-api/consumers/<name>/jwt
    ```
5. Published contents are not visible in library  
   in KP machine run the below query to check the content is synced to ES
   `curl localhost:9200/compositesearch/cs/<do_idxxx>?pretty`
