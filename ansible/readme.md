

td-agent --version
dpkg -l | grep td-agent
systemctl status td-agent
journalctl -u td-agent.service -n 100  #логи

ss -tulnp | grep 8888
netstat -tulnp | grep 8888



Отправим тестовое сообщение
curl -X POST -d 'json={"source": "localhost", "message": "test"}' http://localhost:8888/test1
curl -X POST -d 'json={"source": "xxxxx", "message": "test"}' http://localhost:8888/test1

Теперь проверьте логи Fluentd, чтобы убедиться, что сообщение было получено и обработано 
посмотрите в файл логов Fluentd:
tail -f /var/log/td-agent/td-agent.log

или посмотрите журнал Fluentd:
journalctl -u td-agent.service -f


sudo nano /etc/td-agent/td-agent.conf

sudo systemctl restart td-agent
tail -f /var/log/td-agent/output.log
sudo nano /var/log/td-agent/output.log

ls /var/log/fluent/access
tail -f /var/log/fluent/access*.log

