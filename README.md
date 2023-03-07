# ansible-cisco-xrd-sr

* Following on from [cisco-xrd](https://hmntsharma.github.io/cisco-xrd/), This lab is a clone of [ansible-cisco-segment-routing](https://github.com/hmntsharma/ansible-cisco-segment-routing), which utilises the xrv9k image, but this time using the Cisco XRd containerized image.

* Everything appears to be functioning well, with the exception of Microloop Avoidance, which is triggered but does not generate an explicit path to avoid the loop.

> **Note**
> 
> For this lab, the docker-compose.yml and ansible.cfg files have been updated as needed.

## How TO
```bash
(vxrdlab) lab@xrdlab:~/github$ git clone https://github.com/hmntsharma/ansible-cisco-xrd-sr.git
Cloning into 'ansible-cisco-xrd-sr'...
remote: Enumerating objects: 129, done.
remote: Counting objects: 100% (129/129), done.
remote: Compressing objects: 100% (59/59), done.
remote: Total 129 (delta 69), reused 125 (delta 68), pack-reused 0
Receiving objects: 100% (129/129), 43.66 KiB | 2.30 MiB/s, done.
Resolving deltas: 100% (69/69), done.
(vxrdlab) lab@xrdlab:~/github$ 
```


```bash
(vxrdlab) lab@xrdlab:~/github$ cd ansible-cisco-xrd-sr/
```

```bash
(vxrdlab) lab@xrdlab:~/github/ansible-cisco-xrd-sr$ sudo docker-compose up -d
Creating network "ansible-cisco-xrd-sr_mgmt" with the default driver
Creating network "xrd-1-gi2-xrd-2-gi2" with the default driver
Creating network "xrd-2-gi0-xrd-3-gi0" with the default driver
Creating network "xrd-2-gi1-xrd-6-gi1" with the default driver
Creating network "xrd-2-gi3-xrd-7-gi3" with the default driver
Creating network "xrd-2-gi5-xrd-9-gi5" with the default driver
Creating network "xrd-3-gi1-xrd-7-gi1" with the default driver
Creating network "xrd-3-gi2-xrd-4-gi2" with the default driver
Creating network "xrd-3-gi3-xrd-9-gi3" with the default driver
Creating network "xrd-4-gi0-xrd-5-gi0" with the default driver
Creating network "xrd-4-gi1-xrd-8-gi1" with the default driver
Creating network "xrd-6-gi0-xrd-7-gi0" with the default driver
Creating network "xrd-7-gi2-xrd-8-gi2" with the default driver
Creating xrd-2 ... done
Creating xrd-6 ... done
Creating xrd-3 ... done
Creating xrd-8 ... done
Creating xrd-7 ... done
Creating xrd-4 ... done
Creating xrd-1 ... done
Creating xrd-9 ... done
Creating xrd-5 ... done
(vxrdlab) lab@xrdlab:~/github/ansible-cisco-xrd-sr$
```

```bash
(vxrdlab) lab@xrdlab:~/github/ansible-cisco-xrd-sr$ sudo docker ps
CONTAINER ID   IMAGE                    COMMAND                  CREATED          STATUS          PORTS     NAMES
51a073d591a6   localhost/ios-xr:7.7.1   "/bin/sh -c /sbin/xr…"   23 seconds ago   Up 20 seconds             xrd-5
c92817e14114   localhost/ios-xr:7.7.1   "/bin/sh -c /sbin/xr…"   23 seconds ago   Up 21 seconds             xrd-1
f0c53e74db53   localhost/ios-xr:7.7.1   "/bin/sh -c /sbin/xr…"   23 seconds ago   Up 20 seconds             xrd-9
79113cd5fbb0   localhost/ios-xr:7.7.1   "/bin/sh -c /sbin/xr…"   23 seconds ago   Up 18 seconds             xrd-4
47e472eba2f5   localhost/ios-xr:7.7.1   "/bin/sh -c /sbin/xr…"   23 seconds ago   Up 21 seconds             xrd-8
e993d8642e99   localhost/ios-xr:7.7.1   "/bin/sh -c /sbin/xr…"   23 seconds ago   Up 18 seconds             xrd-7
10112df01872   localhost/ios-xr:7.7.1   "/bin/sh -c /sbin/xr…"   23 seconds ago   Up 19 seconds             xrd-3
ed1a00be66b1   localhost/ios-xr:7.7.1   "/bin/sh -c /sbin/xr…"   23 seconds ago   Up 20 seconds             xrd-6
3dfc765a4223   localhost/ios-xr:7.7.1   "/bin/sh -c /sbin/xr…"   23 seconds ago   Up 18 seconds             xrd-2
(vxrdlab) lab@xrdlab:~/github/ansible-cisco-xrd-sr$
```

```bash
(vxrdlab) lab@xrdlab:~/github/ansible-cisco-xrd-sr$ cd ansible-cisco-segment-routing/
```

```bash
(vxrdlab) lab@xrdlab:~/github/ansible-cisco-xrd-sr/ansible-cisco-segment-routing$ ansible-playbook all_inclusive_play.yaml
```
