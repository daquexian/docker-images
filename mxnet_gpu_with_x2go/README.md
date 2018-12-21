Pull the image and

```
docker run -p your_port:22 -t -d daquexian/mxnet_gpu_with_x2go
```

For example,

```
docker run -p 2222:22 -t -d daquexian/mxnet_gpu_with_x2go
```

Create a new session and connect to your server Host : (Your Server IP) Port : 2222 Username : root Password : 123456

Select the Session TYPE as : XFCE
