# ReactJS Installation (CentOS 8/ Rocky Linux)
### _Run the following commands preferrably as a `non-root` user and on a fresh OS install_
System Update
```
sudo dnf clean all
sudo dnf update
sudo dnf install gcc-c++ make
```
Add Node.js repository to CentOS
```
curl -sL https://rpm.nodesource.com/setup_14.x | sudo -E bash -
```
Install node version manager (npm) and Node.js
```
sudo dnf install nodejs
```
Verify node.js and npm installation.
- node (v 6.14.xx)
- npm v (14.19.xx)
```
node -v
npm -v
```
Install "create-react-app"

```
npm install -g create-react-app
```
Create a sample ReactJS application
```
create-react-app myreactjsapp
```
Start the ReactJS app
```
cd myreactjsapp
npm start
```
# Troubleshooting
If you have trouble accessing the app URL after running `npm start` (e.g http://192.168.1.149:3000), the firewall of CentOS / Rocky Linux might be preventing you from accessing the site's normal port (in this case, port 3000). To verify this, try disabling your firewall, then re-accessing the app URL:
```
sudo systemctl stop firewalld
```
# Sources
- https://idroot.us/install-reactjs-centos-8/
- https://linuxhint.com/disable-firewall-centos-8/
