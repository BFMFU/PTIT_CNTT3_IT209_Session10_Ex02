PS D:\IT209\Session10\Ex02\Hello> docker build -t hw-backend:v1 .                                 
[+] Building 1.8s (10/10) FINISHED                                                                                                                         docker:desktop-linux
 => [internal] load build definition from Dockerfile                                                                                                                       0.0s
 => => transferring dockerfile: 270B                                                                                                                                       0.0s
 => [internal] load metadata for docker.io/library/eclipse-temurin:17-jre-alpine                                                                                           1.4s
 => [auth] library/eclipse-temurin:pull token for registry-1.docker.io                                                                                                     0.0s
 => [internal] load .dockerignore                                                                                                                                          0.0s
 => => transferring context: 2B                                                                                                                                            0.0s
 => [1/4] FROM docker.io/library/eclipse-temurin:17-jre-alpine@sha256:3c472129dc75a8d1d7a3f2df5b2093a8077e4493deff046754d4764d0371de63                                     0.0s
 => => resolve docker.io/library/eclipse-temurin:17-jre-alpine@sha256:3c472129dc75a8d1d7a3f2df5b2093a8077e4493deff046754d4764d0371de63                                     0.0s
 => [internal] load build context                                                                                                                                          0.0s
 => => transferring context: 114B                                                                                                                                          0.0s
 => CACHED [2/4] WORKDIR /app                                                                                                                                              0.0s
 => CACHED [3/4] COPY build/libs/Hello-0.0.1-SNAPSHOT.jar app.jar                                                                                                          0.0s
 => CACHED [4/4] RUN addgroup -S app && adduser -S -G app app                                                                                                              0.0s
 => exporting to image                                                                                                                                                     0.1s
 => => exporting layers                                                                                                                                                    0.0s
 => => exporting manifest sha256:93fc9d3cccf4d7bc099223b452f69f60d3a31f9f20dad4c072bb091dc61c7bf8                                                                          0.0s
 => => exporting config sha256:49767e64cc0f4a9f6e3e0c9355c7e87f9539bcfc3971d6eb5a8b59eea81c4de6                                                                            0.0s
 => => exporting attestation manifest sha256:26036e2a69bca11c5f07ef3deb268baeb87f2d23dfc79d3354ae3bdb39a087db                                                              0.0s
 => => exporting manifest list sha256:941581c813c02898daa13cbdc38d33d53e856cd47134ee784c11f86073211361                                                                     0.0s
 => => naming to docker.io/library/hw-backend:v1                                                                                                                           0.0s
 => => unpacking to docker.io/library/hw-backend:v1                                                                                                                        0.0s
PS D:\IT209\Session10\Ex02\Hello> docker run -d --name app-single-stage -p 8080:3000 hw-backend:v1
ac2b4c88f3e12e167075a657bb0a77942e018a3888e45aeb3d73b10e156dee67
PS D:\IT209\Session10\Ex02\Hello> docker ps
CONTAINER ID   IMAGE           COMMAND                  CREATED          STATUS                          PORTS                                         NAMES
ac2b4c88f3e1   hw-backend:v1   "/__cacert_entrypoin…"   11 seconds ago   Up 10 seconds                   0.0.0.0:8080->3000/tcp, [::]:8080->3000/tcp   app-single-stage
7fc9e8c30fad   mysql:8.0       "docker-entrypoint.s…"   8 hours ago      Restarting (1) 58 seconds ago                                                 student-mysql
PS D:\IT209\Session10\Ex02\Hello> docker logs app-single-stage

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v4.1.1)                                                                                                                                      
                                                                                                                                                                                
2026-10-12T10:37:10.722Z  INFO 1 --- [Hello] [           main] ra.edu.hello.HelloApplication            : Starting HelloApplication v0.0.1-SNAPSHOT using Java 17.0.20.1 with PID 1 (/app/app.jar started by app in /app)                                                                                                                                       
2026-10-12T10:37:10.726Z  INFO 1 --- [Hello] [           main] ra.edu.hello.HelloApplication            : No active profile set, falling back to 1 default profile: "default"
2026-10-12T10:37:11.622Z  INFO 1 --- [Hello] [           main] o.s.boot.tomcat.TomcatWebServer          : Tomcat initialized with port 3000 (http)
2026-10-12T10:37:11.635Z  INFO 1 --- [Hello] [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2026-10-12T10:37:11.635Z  INFO 1 --- [Hello] [           main] o.apache.catalina.core.StandardEngine    : Starting Servlet engine: [Apache Tomcat/11.0.24]
2026-10-12T10:37:11.661Z  INFO 1 --- [Hello] [           main] b.w.c.s.WebApplicationContextInitializer : Root WebApplicationContext: initialization completed in 873 ms
2026-10-12T10:37:12.039Z  INFO 1 --- [Hello] [           main] o.s.boot.tomcat.TomcatWebServer          : Tomcat started on port 3000 (http) with context path '/'
2026-10-12T10:37:12.052Z  INFO 1 --- [Hello] [           main] ra.edu.hello.HelloApplication            : Started HelloApplication in 1.827 seconds (process running for 2.324)
PS D:\IT209\Session10\Ex02\Hello> curl -i http://localhost:8080/api

cmdlet Invoke-WebRequest at command pipeline position 1
Supply values for the following parameters:
Uri: 
PS D:\IT209\Session10\Ex02\Hello> curl  http://localhost:8080/api  

Security Warning: Script Execution Risk
Invoke-WebRequest parses the content of the web page. Script code in the web page might be run when the page is parsed.
      RECOMMENDED ACTION:
      Use the -UseBasicParsing switch to avoid script code execution.

      Do you want to continue?
    
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y


StatusCode        : 200
StatusDescription : 
Content           : Hello World
RawContent        : HTTP/1.1 200 
                    Keep-Alive: timeout=60
                    Connection: keep-alive
                    Content-Length: 11
                    Content-Type: text/plain;charset=UTF-8
                    Date: Mon, 12 Oct 2026 10:37:47 GMT
                    
                    Hello World
Forms             : {}
Headers           : {[Keep-Alive, timeout=60], [Connection, keep-alive], [Content-Length, 11], [Content-Type, text/plain;charset=UTF-8]...}
Images            : {}
InputFields       : {}
Links             : {}
ParsedHtml        : mshtml.HTMLDocumentClass
RawContentLength  : 11



PS D:\IT209\Session10\Ex02\Hello> 