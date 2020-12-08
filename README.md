[<img src="https://github.com/elasticlabs/nextcloud-compose-nginx/blob/main/logo.jpg" align="right" width="250px">](https://nextcloud.com/)
# nextcloud-compose-nginx
This project is a Nextcloud composition stack designed to integrate with a Nginx HTTP reverse proxy.


**What is Nextcloud?** 
- [Nextcloud](https://nextcloud.com/) is open source software you can use to create a fully functional and state-of-art opensource collaborative solution. Share and collaborate on documents, send and receive email, manage your calendar and have video chats without data leaks. As fully on-premises solution, Nextcloud Hub provides the benefits of online collaboration without the compliance and security risks.

**Table Of Contents:**
  - [Docker environment preparation](#docker-environment-preparation)
  - [Nextcloud deployment preparation](#nextcloud-deployment-preparation)
  - [Stack deployment and management](#stack-deployment-and-management)

----

## Docker environment preparation 
This stack is meant to be deployed behind an automated NGINX based HTTPS proxy. The recommanded automated HTTPS proxy for this stack is the [Elasticlabs HTTPS Nginx Proxy](https://github.com/elasticlabs/https-nginx-proxy-docker-compose). This composition repository assumes you have this environment :
* Working HTTPS Nginx proxy using Let'sencrypt certificates
* A local docker LAN network called `revproxy_apps` for hosting your *bubble apps* (Nginx entrypoint for each *bubble*). 

**Once you have a HTTPS reverse proxy**, navigate to the  [next](#teamengine-deployment-preparation) section.

## Nextcloud deployment preparation :
* Choose & register a DNS name (e.g. `nextcloud.your-domain.ltd`). Make sure it properly resolves from your server using `nslookup`commands.
* Carefully create / choose an appropriate directory to group your applications GIT reposities (e.g. `~/AppContainers/`)
* GIT clone this repository `git clone https://github.com/elasticlabs/nextcloud-compose-nginx.git`
* Modify the following variables in `.env` file :
  * `TE_VHOST=` : replace `nextcloud.your-domain.ltd` with your choosen subdomain for portainer.
  * `LETSENCRYPT_EMAIL=` : replace `email@mail-provider.ltd` with the email address to get notifications on Certificates issues for your domain. 

## Stack deployment and management
**Deployment**
* Get help : `sudo make help`
* Bring up the whole stack : `sudo make build && sudo make up`
* Head to **`http://nextcloud.your-domain.ltd`** and enjoy your Headless Wordpress!

**Useful management commands**
* Go inside a container : `sudo docker-compose exec -it <service-id> bash` or `sh`
* See logs of a container: `sudo docker-compose logs <service-id>`
* Monitor containers : `sudo docker stats` or... use portainer!