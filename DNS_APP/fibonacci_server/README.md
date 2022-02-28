Docker Image: https://hub.docker.com/r/rsaim/fibonacci-server

```bash
$ docker build -t rsaim/fibonacci-server:latest .
[+] Building 3.4s (13/13) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                                                           0.0s
 => => transferring dockerfile: 410B                                                                                                                                                           0.0s
 => [internal] load .dockerignore                                                                                                                                                              0.0s
 => => transferring context: 2B                                                                                                                                                                0.0s
 => [internal] load metadata for docker.io/library/python:3.9                                                                                                                                  0.9s
 => [auth] library/python:pull token for registry-1.docker.io                                                                                                                                  0.0s
 => [1/7] FROM docker.io/library/python:3.9@sha256:f83d4b1356ee28b54c28ffe10dfcddb020e33b38e6fa109dba369b7286d2819b                                                                            0.0s
 => => resolve docker.io/library/python:3.9@sha256:f83d4b1356ee28b54c28ffe10dfcddb020e33b38e6fa109dba369b7286d2819b                                                                            0.0s
 => [internal] load build context                                                                                                                                                              0.0s
 => => transferring context: 444B                                                                                                                                                              0.0s
 => CACHED [2/7] RUN apt-get update   && apt-get clean   && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*                                                                                      0.0s
 => CACHED [3/7] RUN groupadd -g 799 nyu &&     useradd -r -u 999 -g nyu nyu                                                                                                                   0.0s
 => CACHED [4/7] WORKDIR /app                                                                                                                                                                  0.0s
 => CACHED [5/7] RUN pip install Flask                                                                                                                                                         0.0s
 => [6/7] RUN pip install requests                                                                                                                                                             2.2s
 => [7/7] COPY --chown=nyu:nyu . .                                                                                                                                                             0.0s
 => exporting to image                                                                                                                                                                         0.1s
 => => exporting layers                                                                                                                                                                        0.1s
 => => writing image sha256:c611685a47ee53c47161627c9384eeabb65a48ab8faf666de2b23d1c6d38df21                                                                                                   0.0s
 => => naming to docker.io/rsaim/fibonacci-server:latest                                                                                                                                       0.0s
 
 Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```



```bash
$ docker run -p 9090:9090 --net=DNS_APP_NETW rsaim/fibonacci-server
 * Serving Flask app 'fibonacci_server' (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: on
[FS: 04:07:42 AM]  * Running on all addresses.
   WARNING: This is a development server. Do not use it in a production deployment.
[FS: 04:07:42 AM]  * Running on http://172.19.0.3:9090/ (Press CTRL+C to quit)
[FS: 04:07:42 AM]  * Restarting with stat
[FS: 04:07:42 AM]  * Debugger is active!
[FS: 04:07:42 AM]  * Debugger PIN: 396-951-784
[FS: 04:07:47 AM] /register got body=None
[FS: 04:08:03 AM] /register got body={'hostname': 'fibonacci.com', 'fs_ip': '127.0.0.1', 'fs_port': 9090, 'as_ip': '127.0.0.1', 'as_port': 53533, 'ttl': 15}
[FS: 04:08:03 AM] Sending ('fibonacci.com', '127.0.0.1', 'A', 15) to ('127.0.0.1', 53533) via UDP socket
[FS: 04:08:03 AM] 172.19.0.1 - - [14/Oct/2021 04:08:03] "PUT /register HTTP/1.1" 200 -
[FS: 04:08:15 AM] /register got body={'hostname': 'fibonacci.com', 'fs_ip': '172.19.0.3', 'fs_port': 9090, 'as_ip': '172.19.0.2', 'as_port': 53533, 'ttl': 15}
[FS: 04:08:15 AM] Sending ('fibonacci.com', '172.19.0.3', 'A', 15) to ('172.19.0.2', 53533) via UDP socket
[FS: 04:08:15 AM] 172.19.0.1 - - [14/Oct/2021 04:08:15] "PUT /register HTTP/1.1" 200 -
[FS: 04:17:27 AM] 172.19.0.1 - - [14/Oct/2021 04:17:27] "GET / HTTP/1.1" 200 -
[FS: 04:18:35 AM] /register got body={'hostname': 'fibonacci.com', 'fs_ip': '172.19.0.3', 'fs_port': 9090, 'as_ip': '172.19.0.2', 'as_port': 53533, 'ttl': 15}
[FS: 04:18:35 AM] Sending ('fibonacci.com', '172.19.0.3', 'A', 15) to ('172.19.0.2', 53533) via UDP socket
[FS: 04:18:35 AM] 172.19.0.1 - - [14/Oct/2021 04:18:35] "PUT /register HTTP/1.1" 200 -
[FS: 04:22:19 AM] /register got body={'hostname': 'fibonacci.com', 'fs_ip': '172.19.0.3', 'fs_port': 9090, 'as_ip': '172.19.0.2', 'as_port': 53533, 'ttl': 100000}
[FS: 04:22:19 AM] Sending ('fibonacci.com', '172.19.0.3', 'A', 100000) to ('172.19.0.2', 53533) via UDP socket
[FS: 04:22:19 AM] 172.19.0.1 - - [14/Oct/2021 04:22:19] "PUT /register HTTP/1.1" 200 -
[FS: 04:26:36 AM] /fibonacci got n=9
[FS: 04:26:36 AM] 172.19.0.5 - - [14/Oct/2021 04:26:36] "GET /fibonacci?number=9 HTTP/1.1" 200 -
[FS: 04:26:40 AM] 172.19.0.5 - - [14/Oct/2021 04:26:40] "GET /fibonacci HTTP/1.1" 500 -
[FS: 04:26:43 AM] 172.19.0.5 - - [14/Oct/2021 04:26:43] "GET / HTTP/1.1" 200 -
[FS: 04:30:32 AM] /fibonacci got n=9
[FS: 04:30:32 AM] 172.19.0.4 - - [14/Oct/2021 04:30:32] "GET /fibonacci?number=9 HTTP/1.1" 200 -
[FS: 04:31:10 AM] /fibonacci got n=9
[FS: 04:31:10 AM] 172.19.0.4 - - [14/Oct/2021 04:31:10] "GET /fibonacci?number=9 HTTP/1.1" 200 -
[FS: 04:32:37 AM] 172.19.0.1 - - [14/Oct/2021 04:32:37] "GET /?number=9 HTTP/1.1" 200 -
[FS: 04:32:45 AM] /fibonacci got n=9
[FS: 04:32:45 AM] 172.19.0.1 - - [14/Oct/2021 04:32:45] "GET /fibonacci?number=9 HTTP/1.1" 200 -
```



```bash
$ docker push rsaim/fibonacci-server
Using default tag: latest
The push refers to repository [docker.io/rsaim/fibonacci-server]
22fb333b2e85: Pushed
bf7285c59f79: Pushed
1ca8ebb2878d: Mounted from rsaim/user-server
cd93ac2f9c3a: Mounted from rsaim/user-server
5da471c81d43: Mounted from rsaim/user-server
34b2899cd9e6: Mounted from rsaim/user-server
febe96d6107f: Mounted from rsaim/user-server
7b656b8058c4: Mounted from rsaim/user-server
02a38a00d553: Mounted from rsaim/user-server
7fcd2600f5ad: Mounted from rsaim/user-server
8f56c3340629: Mounted from rsaim/user-server
ba6e5ff31f23: Mounted from rsaim/user-server
9f9f651e9303: Mounted from rsaim/user-server
0b3c02b5d746: Mounted from rsaim/user-server
62a747bf1719: Mounted from rsaim/user-server
latest: digest: sha256:bdbfd5669f632ff730c0fc1e6675711397774cf29f81579102ab209eae884e84 size: 3470
```



