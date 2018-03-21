# kuzzle-playground
Just testing

## Requisites

> From http://docs.kuzzle.io/guide/essentials/installing-kuzzle/

1. Docker v1.10+
2. Docker-compose v1.8+
3. Maximum virtual memory >= 262144
    - if `sysctl -n vm.max_map_count` is not >= 262144, run `echo "vm.max_map_count=262144" >> /etc/sysctl.conf`
4. `docker-compose up`
    - Expected response on initialization process:  _kuzzle_1         | [✔] Kuzzle server ready_
    - This command shoud return a JSON result `curl "http://localhost:7512/?pretty"`