ifdef::env-github[]
:tip-caption: :bulb:
:note-caption: :information_source:
:important-caption: :heavy_exclamation_mark:
:caution-caption: :fire:
:warning-caption: :warning:
endif::[]

TIP: Rancher installation

sudo docker run -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher

docker run -d --privileged --restart=unless-stopped --net=host -v /etc/kubernetes:/etc/kubernetes -v /var/run:/var/run rancher/rancher-agent:v2.0.7 --server https://localhost --token dmx6wc79zdxvxxhwm5x7dl5rjkjbsmhgx9hx5cs7mst45b8z57npm2 --ca-checksum fbb6fb274fef0cb59123e452edb63cd03095ba226f7c05c2acc805934ebf527f --etcd --controlplane --worker
bc9a60ef2c0291caf50e8a6e2014236e9220c84a9355ddeda00ef577b1fb4a8d
