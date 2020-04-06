# Docker Notes

Delete all  containers `docker container rm $(docker container ls -aq) -f` 

`docker run -d  --rm -v $(pwd):/usr/share/nginx/html --name web1 nginx:alpine`
