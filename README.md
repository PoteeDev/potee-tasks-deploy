
curl -X 'POST' \
  'http://127.0.0.1:8000/v1/devices/' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer secret' \
  -H 'Content-Type: application/json' \
  -d '{
  "name": "wg1",
  "listen_port": 51821,
  "private_key": "wBHGU3RiK/IFWXAF2jbHjGSDAKEO2ddcsZFEWcQ+qGc=",
  "firewall_mark": 10
}'

curl -v -g \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer secret" \
    -X PATCH \
    -d '{
        "listen_port":51820, 
        "private_key": "cLmxIyJx/PGWrQlevBGr2LQNOqmBGYbVfu4XcRO2SEo="
    }' \
    http://127.0.0.1:8000/v1/devices/wg0/

### list defices
curl -v -g -H "Content-Type: application/json"  -H "Authorization: Bearer secret" -X GET http://127.0.0.1:8000/v1/devices/

### add client
curl -v -g -H "Content-Type: application/json" -H "Authorization: Bearer secret" -X POST -d '{"allowed_ips": ["10.0.1.2/32"],"preshared_key": "ihahanov"}' http://127.0.0.1:8000/v1/devices/wg0/peers/


curl -X 'GET' \
  'http://127.0.0.1:8000/v1/devices/wg0/peers/a1FMwC0zewNhhm4RWj1uMBy_oJsqhr0NxgMQZlvBzGE%3D/' \
  -H "Authorization: Bearer secret" \
  -H 'accept: application/json'

curl -X 'GET' \
  'http://127.0.0.1:8000/v1/devices/wg0/peers/FYzm1RK_Je-zS5vf9V1AG3pivIA063FxWj-TH0f7tBg=/quick.conf' \
  -H "Authorization: Bearer secret" \
  -H 'accept: application/json'


## create network 
```
docker network create  --driver=bridge --subnet=10.10.0.0/16 net
```# potee-tasks-deploy
