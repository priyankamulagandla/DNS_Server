Docker image: https://hub.docker.com/r/rsaim/auth-server

```bash
$ docker build -t rsaim/auth-server:latest .
[+] Building 0.4s (11/11) FINISHED
 => [internal] load build definition from Dockerfile                                                                                                                                           0.0s
 => => transferring dockerfile: 37B                                                                                                                                                            0.0s
 => [internal] load .dockerignore                                                                                                                                                              0.0s
 => => transferring context: 2B                                                                                                                                                                0.0s
 => [internal] load metadata for docker.io/library/python:3.9                                                                                                                                  0.3s
 => [1/6] FROM docker.io/library/python:3.9@sha256:206efc55ae5a8cc3ab413105da3617d78fa15bf512acc437a4dce94e4430ddcc                                                                            0.0s
 => [internal] load build context                                                                                                                                                              0.0s
 => => transferring context: 66B                                                                                                                                                               0.0s
 => CACHED [2/6] RUN apt-get update   && apt-get clean   && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*                                                                                      0.0s
 => CACHED [3/6] RUN groupadd -g 799 nyu &&     useradd -r -u 999 -g nyu nyu                                                                                                                   0.0s
 => CACHED [4/6] WORKDIR /app                                                                                                                                                                  0.0s
 => CACHED [5/6] RUN pip install Flask                                                                                                                                                         0.0s
 => CACHED [6/6] COPY --chown=nyu:nyu . .                                                                                                                                                      0.0s
 => exporting to image                                                                                                                                                                         0.0s
 => => exporting layers                                                                                                                                                                        0.0s
 => => writing image sha256:eda320be191e0b3ae7077baf217a0c3217f781f6a27d912d648aecf5407ec9bb                                                                                                   0.0s
 => => naming to docker.io/rsaim/auth-server:latest                                                                                                                                            0.0s

Use 'docker scan' to run Snyk tests against images to find vulnerabilities and learn how to fix them
```

```bash
$ docker run -p 53533:53533/udp --network DNS_APP_NETW rsaim/auth-server
[01:55:33 AM auth_server.py:94] Spinning up authoritative server
[01:55:33 AM auth_server.py:63] UDP server up and listening on 172.19.0.2:53533
^[[C[04:08:15 AM auth_server.py:70] Message from Client: ('fibonacci.com', '172.19.0.3', 'A', 15)
[04:08:16 AM auth_server.py:40] Saving DNS record for fibonacci.com ('172.19.0.3', 1634184511.0510201, 15)
[04:18:35 AM auth_server.py:70] Message from Client: ('fibonacci.com', '172.19.0.3', 'A', 15)
[04:18:35 AM auth_server.py:40] Saving DNS record for fibonacci.com ('172.19.0.3', 1634185130.401172, 15)
[04:21:51 AM auth_server.py:70] Message from Client: ('A', 'fibonacci.com')
[04:21:51 AM auth_server.py:52] Got DNS records for fibonacci.com: ['172.19.0.3', 1634185130.401172, 15]
[04:21:51 AM auth_server.py:53] Curr time=1634185311.897173 ttl_ts=1634185130.401172
[04:21:51 AM auth_server.py:55] TTL expired for fibonacci.com
[04:22:19 AM auth_server.py:70] Message from Client: ('fibonacci.com', '172.19.0.3', 'A', 100000)
[04:22:19 AM auth_server.py:40] Saving DNS record for fibonacci.com ('172.19.0.3', 1634285339.5630207, 100000)
[04:22:24 AM auth_server.py:70] Message from Client: ('A', 'fibonacci.com')
[04:22:24 AM auth_server.py:52] Got DNS records for fibonacci.com: ['172.19.0.3', 1634285339.5630207, 100000]
[04:22:24 AM auth_server.py:53] Curr time=1634185344.6342757 ttl_ts=1634285339.5630207
[04:24:46 AM auth_server.py:70] Message from Client: ('A', 'fibonacci.com')
[04:24:46 AM auth_server.py:52] Got DNS records for fibonacci.com: ['172.19.0.3', 1634285339.5630207, 100000]
[04:24:46 AM auth_server.py:53] Curr time=1634185486.0046916 ttl_ts=1634285339.5630207
[04:27:57 AM auth_server.py:70] Message from Client: ('A', 'fibonacci.com')
[04:27:57 AM auth_server.py:52] Got DNS records for fibonacci.com: ['172.19.0.3', 1634285339.5630207, 100000]
[04:27:57 AM auth_server.py:53] Curr time=1634185677.368206 ttl_ts=1634285339.5630207
[04:29:05 AM auth_server.py:70] Message from Client: ('A', 'fibonacci.com')
[04:29:05 AM auth_server.py:52] Got DNS records for fibonacci.com: ['172.19.0.3', 1634285339.5630207, 100000]
[04:29:05 AM auth_server.py:53] Curr time=1634185745.2784417 ttl_ts=1634285339.5630207
[04:30:31 AM auth_server.py:70] Message from Client: ('A', 'fibonacci.com')
[04:30:31 AM auth_server.py:52] Got DNS records for fibonacci.com: ['172.19.0.3', 1634285339.5630207, 100000]
[04:30:31 AM auth_server.py:53] Curr time=1634185831.9984496 ttl_ts=1634285339.5630207
[04:31:10 AM auth_server.py:70] Message from Client: ('A', 'fibonacci.com')
[04:31:10 AM auth_server.py:52] Got DNS records for fibonacci.com: ['172.19.0.3', 1634285339.5630207, 100000]
[04:31:10 AM auth_server.py:53] Curr time=1634185870.4237156 ttl_ts=1634285339.5630207
```

```bash
$ docker push rsaim/auth-server
Using default tag: latest
The push refers to repository [docker.io/rsaim/auth-server]
40f42ed05907: Pushed
1ca8ebb2878d: Layer already exists
cd93ac2f9c3a: Layer already exists
5da471c81d43: Layer already exists
34b2899cd9e6: Layer already exists
febe96d6107f: Layer already exists
7b656b8058c4: Layer already exists
02a38a00d553: Layer already exists
7fcd2600f5ad: Layer already exists
8f56c3340629: Layer already exists
ba6e5ff31f23: Layer already exists
9f9f651e9303: Layer already exists
0b3c02b5d746: Layer already exists
62a747bf1719: Layer already exists
latest: digest: sha256:39cfb6adc8808b615481b77962376f7bf482cffa97e8cf385f6305f6837fb58f size: 3259
```



