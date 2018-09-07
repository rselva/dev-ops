ifdef::env-github[]
:tip-caption: :bulb:
:note-caption: :information_source:
:important-caption: :heavy_exclamation_mark:
:caution-caption: :fire:
:warning-caption: :warning:
endif::[]

:bulb: Rancher installation
```
$ docker  volume rm $(docker volume ls -q)
$ rm -rf /var/lib/etcd /etc/kubernetes/ssl /etc/cni /opt/cni /var/lib/cni /var/run/calico /etc/kubernetes/.tmp/
$ mount --bind /var/lib/docker/ /var/lib/docker
$ docker run -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher
$ docker run -d --privileged --restart=unless-stopped --net=host -v /etc/kubernetes:/etc/kubernetes -v /var/run:/var/run rancher/rancher-agent:v2.0.8 --server https://10.10.181.210 --token 99md7vlnbglpt5s4p6gvrc2wmjjrfspxsc5k8h8lmxc9r2ln6fl85d --ca-checksum e68b3cb459705b2970ced8cdc4b6f69a8d9a94188165294744188f441a4563b8 --etcd --controlplane --worker
```

