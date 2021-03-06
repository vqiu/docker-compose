
etcd-3.1 可以使用名称代替IP，如下：
```
services:
    etcd-1:
        image: quay.io/coreos/etcd:latest
        entrypoint: /usr/local/bin/etcd
        command:
            - '--name=etcd-1'
            - '--initial-advertise-peer-urls=http://etcd-1:2380'
            - '--listen-peer-urls=http://etcd-1:2380'
            - '--listen-client-urls=http://etcd-1:2379,http://localhost:2379'
            - '--advertise-client-urls=http://etcd-1:2379'
            - '--initial-cluster-token=mys3cr3ttok3n'
            - '--heartbeat-interval=250'
            - '--election-timeout=1250'
            - '--initial-cluster=etcd-1=http://etcd-1:2380,etcd-2=http://etcd-2:2380,etcd-3=http://etcd-3:2380'
            - '--initial-cluster-state=new'
    etcd-2:
        image: quay.io/coreos/etcd:latest
        entrypoint: /usr/local/bin/etcd
        command:
            - '--name=etcd-2'
            - '--initial-advertise-peer-urls=http://etcd-2:2380'
            - '--listen-peer-urls=http://etcd-2:2380'
            - '--listen-client-urls=http://etcd-2:2379,http://localhost:2379'
            - '--advertise-client-urls=http://etcd-2:2379'
            - '--initial-cluster-token=mys3cr3ttok3n'
            - '--heartbeat-interval=250'
            - '--election-timeout=1250'
            - '--initial-cluster=etcd-1=http://etcd-1:2380,etcd-2=http://etcd-2:2380,etcd-3=http://etcd-3:2380'
            - '--initial-cluster-state=new'
    etcd-3:
        image: quay.io/coreos/etcd:latest
        entrypoint: /usr/local/bin/etcd
        command:
            - '--name=etcd-3'
            - '--initial-advertise-peer-urls=http://etcd-3:2380'
            - '--listen-peer-urls=http://etcd-3:2380'
            - '--listen-client-urls=http://etcd-3:2379,http://localhost:2379'
            - '--advertise-client-urls=http://etcd-3:2379'
            - '--initial-cluster-token=mys3cr3ttok3n'
            - '--heartbeat-interval=250'
            - '--election-timeout=1250'
            - '--initial-cluster=etcd-1=http://etcd-1:2380,etcd-2=http://etcd-2:2380,etcd-3=http://etcd-3:2380'
            - '--initial-cluster-state=new'
```

然而 etcd-3.2 时需要指定IP，所以添加了 `networks` 参数
