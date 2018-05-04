# LB2 - Wordpress mit Mysql Datenbank

***Installation***

Als erstes muss ein Mysql Container aufgesetzt werden, dies kann mit folgedem Befehl durchgeführt werden:
```
docker run --detach --name=test-mysql --env="MYSQL_ROOT_PASSWORD=mypassword" mysql
```

Danach wird die Wordpress Installation vorgenommen, dies kann mit folgendem Befehl durchgeführt werden. Dabei wird auch direkt die Verlinkung mit der Datenbank hergestellt:
```
docker run --detach --name test-wordpress --link test-mysql:mysql -P wordpress
```

Um zu überprüfen ob die beiden Container korrekt aufgesetzt wurden, wird folgender Befehl ausgeführt:
```
docker ps
```
In der Ausgabe dieses Befehles sind die einzelnen Container und auch ihre Ports sichtbar:
```
14c9b3c8cbbe        wordpress           "docker-entrypoint.s…"   33 minutes ago      Up 33 minutes       0.0.0.0:32768->80/tcp    test-wordpress
789a65e428f4        mysql               "docker-entrypoint.s…"   About an hour ago   Up 42 minutes       0.0.0.0:6603->3306/tcp   test-mysql
```
