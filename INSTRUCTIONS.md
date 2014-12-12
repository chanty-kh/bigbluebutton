# Instructions

Create file called ``/etc/bigbluebutton/nginx/mekongconnect```

```
location /client {
    root /var/www/bigbluebutton;
    index index.html index.html;
}

location /client/BigBlueButton.html {
    rewrite ^ /mekongconnect permanent;
}

location /mekongconnect {
    alias /var/www/bigbluebutton/client;
    index BigBlueButton.html;
    expires 1m;
}
```

```
sudo rm /etc/bigbluebutton/nginx/client.nginx

sudo ln -s /etc/bigbluebutton/nginx/mekongconnect /etc/bigbluebutton/nginx/client.nginx

sudo /etc/init.d/nginx restart
```