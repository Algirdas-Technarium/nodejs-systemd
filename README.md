# nodejs-systemd
run multiple nodejs apps with systemd

* Create the file in your system. The path is fully specified in the actual repo.
* If you will run this with a user not named `pi`, replace `pi` with your user name in lines `6`, `7` and `8`.
* Run `sudo systemctl daemon-reload`.
* Create a directory in your home: `nodejs_app_daemons`.
* For each application you want to run: 
  * In your `~/nodejs_app_daemons` directory, create a directory named `{{your_service_name}}`. Make sure it's a node app that contains `index.js` and `npm install` has been run.
  * Run `systemctl start nodejs-app-daemon@{{your_service_name}}`, this starts the service.
    * Run `systemctl status nodejs-app-daemon@{{your_service_name}}` to see how your app is running.
    * Use `journalctl -f -u nodejs-app-daemon@{{your_service_name}}` to see the logs pour in.
  * Run `systemctl enable nodejs-app-daemon@{{your_service_name}}` to make the service autorun and autorestart.
