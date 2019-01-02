# metadata-one-liners

Retrive metadata endpoint data with these one liners.

Feel free to do a PR request if you want to add or alter anything.



Python 2
---

AWS

```
python -c 'import urllib2; print(urllib2.urlopen("http://169.254.169.254/latest/meta-data/").read())'
```

Digital Ocean

```
python -c 'import urllib2; print(urllib2.urlopen("http://169.254.169.254/metadata/v1/").read())'
```

Google

```
python -c 'import urllib2; print(urllib2.urlopen("http://metadata.google.internal/computeMetadata/v1beta1/project/attributes/ssh-keys?alt=json").read())'
```

Azure (not complete) need headers

```
python -c 'import urllib2; print(urllib2.urlopen("http://169.254.169.254/metadata/instance?api-version=2017-04-02").read())'
```






Python 3
---

AWS

```
python3 -c 'import urllib.request; print(urllib.request.urlopen("http://169.254.169.254/latest/meta-data/").read())''
```

Digital Ocean

```
python3 -c 'import urllib.request; print(urllib.request.urlopen("http://169.254.169.254/metadata/v1/").read())''
```

Google

```
python3 -c 'import urllib.request; print(urllib.request.urlopen("http://metadata.google.internal/computeMetadata/v1beta1/project/attributes/ssh-keys?alt=json").read())''
```


Azure (not complete) need headers

```
python3 -c 'import urllib.request; print(urllib.request.urlopen("http://169.254.169.254/metadata/instance?api-version=2017-04-02").read())''
```


Wget
---


AWS

```
wget -q -O - http://169.254.169.254/latest/meta-data/
```

Digital Ocean

```
wget -q -O - http://169.254.169.254/metadata/v1/
```

Google

```
wget http://metadata.google.internal/computeMetadata/v1beta1/project/attributes/ssh-keys?alt=json
```

Azure

```
wget --header="Metadata: true" http://169.254.169.254/metadata/instance?api-version=2017-04-02
```






Curl
---

AWS

```
curl http://169.254.169.254/latest/meta-data/
curl http://169.254.169.254/latest/meta-data/network/interfaces/macs/$(curl -s http://169.254.169.254/latest/meta-data/network/interfaces/macs/)/owner-id/
curl http://169.254.169.254/latest/meta-data/public-keys/0/openssh-key
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/$(curl -s http://169.254.169.254/latest/meta-data/iam/security-credentials/)
curl http://169.254.169.254/latest/dynamic/instance-identity/document/
curl http://169.254.169.254/latest/meta-data/security-groups/
curl http://169.254.169.254/latest/user-data
```

Digital Ocean

```
curl http://169.254.169.254/metadata/v1/
```

Google

```
curl http://metadata.google.internal/computeMetadata/v1beta1/project/attributes/ssh-keys?alt=json
curl http://metadata.google.internal/computeMetadata/v1beta1/project/attributes/sshKeys
curl http://metadata.google.internal/computeMetadata/v1beta1/instance/attributes/kube-env
curl http://metadata.google.internal/computeMetadata/v1beta1/instance/service-accounts/default/identity
curl http://metadata.google.internal/computeMetadata/v1beta1/instance/hostname
```

Azure

```
curl -H Metadata:true http://169.254.169.254/metadata/instance?api-version=2017-04-02
```



Busybox
---

AWS

```
busybox wget -q -O - http://169.254.169.254/latest/meta-data/
busybox wget -q -O - http://169.254.169.254/latest/meta-data/network/interfaces/macs/$(busybox wget -q -O - http://169.254.169.254/latest/meta-data/network/interfaces/macs/)/owner-id/
busybox wget -q -O - http://169.254.169.254/latest/meta-data/public-keys/0/openssh-key
busybox wget -q -O - http://169.254.169.254/latest/meta-data/iam/security-credentials/
busybox wget -q -O - http://169.254.169.254/latest/meta-data/iam/security-credentials/$(busybox wget -q -O - http://169.254.169.254/latest/meta-data/iam/security-credentials/)
busybox wget -q -O - http://169.254.169.254/latest/dynamic/instance-identity/document/
busybox wget -q -O - http://169.254.169.254/latest/meta-data/security-groups/
busybox wget -q -O - http://169.254.169.254/latest/user-data
```

Digital Ocean

```
busybox wget -q -O - http://169.254.169.254/metadata/v1/
```

Google

```
busybox wget http://metadata.google.internal/computeMetadata/v1beta1/project/attributes/ssh-keys?alt=json
```

Azure

```
busybox wget --header="Metadata: true" http://169.254.169.254/metadata/instance?api-version=2017-04-02
```


NC
---

AWS

```
echo -e "GET /latest/meta-data/ HTTP/1.0\r\n\r\n" | nc 169.254.169.254 80
```

Digital Ocean

```
echo -e "GET /metadata/v1/ HTTP/1.0\r\n\r\n" | nc 169.254.169.254 80
```

Google

```
TBC
```

Azure

```
TBC
```

## Oracle Cloud
http://192.0.0.192/latest/
http://192.0.0.192/latest/user-data/
http://192.0.0.192/latest/meta-data/
http://192.0.0.192/latest/attributes/

## Alibaba
http://100.100.100.200/latest/meta-data/
http://100.100.100.200/latest/meta-data/instance-id
http://100.100.100.200/latest/meta-data/image-id
