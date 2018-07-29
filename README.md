# NetCoreWebApiDocker

change needed in program.cs for raspberry docker version:
.UseUrls("http://*:5000")

 docker build -f "C:\Git\NetCoreWebApiDocker\NetCoreWebApiDockerLinux\Dockerfile" -t "webapilinuximg" "C:\Git\NetCoreWebApiDocker"
 
 docker tag webapilinuximg milanmilas/webapilinuximg
 
 docker login
 docker push milanmilas/webapilinuximg
 
 Raspberry shell:
 Docker run --rm -it -p 5000:5000 milanmilas/webapilinuximg
  
 local machine:
  http://192.168.1.111:5000/api/values

run docker on local machine linux not arm build:
docker run -p 5250:80 webapilinuximg
