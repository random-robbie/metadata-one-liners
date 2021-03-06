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
curl http://metadata.google.internal/computeMetadata/v1beta1/instance/attributes/?recursive=true&alt=json

curl http://metadata.google.internal/computeMetadata/v1/project/attributes/ssh-keys?alt=json -H "Metadata-Flavor: Google"
curl http://metadata.google.internal/computeMetadata/v1/project/attributes/sshKeys -H "Metadata-Flavor: Google"
curl http://metadata.google.internal/computeMetadata/v1/instance/attributes/kube-env -H "Metadata-Flavor: Google"
curl http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/identity -H "Metadata-Flavor: Google"
curl http://metadata.google.internal/computeMetadata/v1/instance/hostname -H "Metadata-Flavor: Google"
curl http://metadata.google.internal/computeMetadata/v1/instance/attributes/?recursive=true&alt=json -H "Metadata-Flavor: Google"


```

Azure

```
curl -H Metadata:true http://169.254.169.254/metadata/instance?api-version=2019-08-15
curl 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2019-08-15&resource=https%3A%2F%2Fmanagement.azure.com%2F' -H Metadata:true -s
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
busybox wget -q -O - http://metadata.google.internal/computeMetadata/v1beta1/project/attributes/ssh-keys?alt=json
busybox wget -q -O - http://metadata.google.internal/computeMetadata/v1beta1/project/attributes/sshKeys
busybox wget -q -O - http://metadata.google.internal/computeMetadata/v1beta1/instance/attributes/kube-env
busybox wget -q -O - http://metadata.google.internal/computeMetadata/v1beta1/instance/service-accounts/default/identity
busybox wget -q -O - http://metadata.google.internal/computeMetadata/v1beta1/instance/hostname
```

Azure

```
busybox wget --header="Metadata: true" http://169.254.169.254/metadata/instance?api-version=2017-04-02

```

Powershell
---

```
powershell.exe -Command "invoke-webrequest http://169.254.169.254/latest/meta-data/iam/security-credentials/ | Select-Object -Expand Content"
```

```
powershell.exe -Command "invoke-webrequest http://metadata.google.internal/computeMetadata/v1beta1/project/attributes/ssh-keys?alt=json | Select-Object -Expand Content"
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

### Oracle Cloud
```
http://169.254.169.254/opc/v1/instance/
http://169.254.169.254/opc/v1/instance/metadata/ (gets public sshkey)
http://169.254.169.254/opc/v1/instance/shape
http://169.254.169.254/opc/v1/identity/cert.pem
http://169.254.169.254/opc/v1/identity/key.pem
http://169.254.169.254/opc/v1/identity/intermediate.pem
```

### Alibaba
```
http://100.100.100.200/latest/meta-data/
http://100.100.100.200/latest/meta-data/instance-id
http://100.100.100.200/latest/meta-data/image-id
```


# Rethink DB

### Google
```
r.http('http://metadata.google.internal/computeMetadata/v1/project/attributes/ssh-keys?alt=json',{  header: { 'Metadata-Flavor': 'Google' } })
```
