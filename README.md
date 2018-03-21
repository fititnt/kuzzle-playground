# kuzzle-playground
Just testing. See [fititnt/chatops-wg-datalake#9](https://github.com/fititnt/chatops-wg-datalake/issues/9) and the working group [fititnt/chatops-wg](https://github.com/fititnt/chatops-wg).

## Step by step

Based on the documentation at http://docs.kuzzle.io/guide/essentials/installing-kuzzle/

> You can see some results at [screenshots/](screenshots/) folder.

1. Requires: Docker v1.10+
2. Requires: Docker-compose v1.8+
3. Requires: Maximum virtual memory >= 262144
    - if `sysctl -n vm.max_map_count` is not >= 262144, run `echo "vm.max_map_count=262144" >> /etc/sysctl.conf`
4. Execute `docker-compose up` on this same repository folder (already downloaded docker-compose.yml)
    - Expected response on initialization process:  _kuzzle_1         | [✔] Kuzzle server ready_
    - This command shoud return a JSON result `curl "http://localhost:7512/?pretty"`
5. `ngrok http 7512` (Note: Use free account from https://ngrok.com, and install Ngrok on your system)
6. Go to http://kuzzle-backoffice.netlify.com/ and configue the server with ngrok public URL
7. Go to http://docs.kuzzle.io/guide/essentials/persisted/
8. Do a POST request to URL http://localhost:7512/myindex/_create (Note: you can a great GUI for this, https://www.getpostman.com/)
9. Do a PUT request to URL http://localhost:7512/myindex/mycollection
10. Do a GET request to URL http://localhost:7512/myindex/_list (this list collections)
11. Do a POST request to http://localhost:7512/myindex/mycollection/_create to create a document with body:
    - `{  "message": "Hello, world!" }`
12 Copy the `_id_` from last respose an use on next request instead of xxxxxxxxxxxxxx
12. Do a POST request to http://localhost:7512/myindex/mycollection/xxxxxxxxxxxxxx/_update to update a document with body:
    - `{ "message": "in a bottle", "an_englishman": "in New York" }`
13. Ops. Request headers must set PUT & POST body content as `Content-Type: application/json` (see screenshots for details)
14. Search documents with POST to http://localhost:7512/myindex/mycollection/_search and params on body (see screenshots for details)
15. Go to http://kuzzle-backoffice.netlify.com and look around (see screenshots `15..19-kuzzle-backoffice.png`)


Stop and clean up
1. <kbd>Ctrl + C</kbd> at ngrok terminal to stop the proxy connection
2. `docker-compose down --volumes --rmi all`
