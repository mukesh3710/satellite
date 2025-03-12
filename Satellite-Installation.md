## Satellite Installation

---
### Foreman katello Installation 
Step-by-Step Guide to Install and Configure Foreman and Katello on Rocky Linux 9:
- A fresh installation of Rocky Linux 9.
- Proper DNS resolution or host entries in /etc/hosts.
- At least 20GB RAM and sufficient disk space.
```bash
dnf update -y
systemctl disable --now firewalld
reboot
```
- Follow link for installation -> https://docs.theforeman.org/3.13/Quickstart/index-katello.html
- Verify installation 
```bash
vi ~/.hammer/cli.modules.d/foreman.yml  # update hammer password after changing from GUI
hammer ping # check system status 
foreman-maintain service status -b # also check the status
```
- Post Installation tasks:
  - Configure Content Management. Create a new product (Content -> Products)
  - Add repositories & sync the repos
  - Create & Assign repositories to Content Views and publish them.
  - Create activation key (Register Host)
 
  Register Clients:
```bash
sudo dnf install -y katello-ca-consumer-latest.noarch.rpm
subscription-manager register --org="Default_Organization" --activationkey="your-activation-key"
```
