# Name: Dhruv Patel
# StudentID: 9062297
# Assignment 3: Orchestration with Gitea

# Steps:

Clone the repo in my terminal: bash <(curl -s https://raw.githubusercontent.com/rhildred/bootstrap/main/oembootstrap)

configure cloudflared for my own tunnel: sudo su - ubuntu

To get a certificate from my cloudflare account: cloudflared tunnel login

Then create a tunnel: 
cloudflared tunnel create "Dhruvpatel-30"
sudo mkdir -p /etc/cloudflared

After create a /etc/cloudflared/config.yml config file:
![alt text](image-3.png)

Then I create the dns entry on cloudflare: cloudflared tunnel route dns b8503f88-2d27-4702-b71a-79716cc1c5cb DhruvPatel-30.dev
 ![alt text](image-4.png)

check status: sudo systemctl status cloudflared
![alt text](image-5.png)

Now,

```bash
pip install ansible kubernetes
git submodule update --init --recursive
ansible-playbook up.yml
![alt text](image.png)
![alt text](image-1.png)
```

Wait until `kubectl get pod` shows all pods running
![alt text](image-8.png)

After,

```bash
kubectl port-forward svc/gitea-http 8080:3000
![alt text](image-9.png)

```
now create ingress and apply it:
![alt text](image-11.png)
![alt text](image-10.png)

here is my ingress external:
![alt text](image-12.png)

Now you should be able to access gitea in development mode.
![alt text](image-13.png)
![alt text](image-14.png)

# Add database and use external database

![alt text](image-16.png)

![alt text](image-15.png)

# Verify All

![alt text](image-17.png)

![alt text](image-18.png)

# Expose your gitea instance publically

![alt text](image-14.png)
