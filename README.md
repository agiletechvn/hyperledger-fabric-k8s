#### Setup 
==============

Run  
```sh
./fn.sh help [method]
```

Run fn from ssh mode  
```sh
./fnssh.sh user:passwd@server:/path
```


Copy chaincode  
```sh
cp -r chaincode /opt/share/channel-artifacts/
```

nfs server
for cluster please run sudo mount /opt/share <master_ip>:/opt/share  
```sh
echo "/opt/share -network <master_ip> -mask 255.255.255.0 -alldirs -maproot=root:wheel" | sudo tee -a /etc/exports
sudo nfsd restart
```

Build admin api images: **optional**  
```sh
# on master node
docker save hyperledger/admin-api > /opt/share/docker/admin-api.tar
# on slave node
docker load < /opt/share/docker/admin-api.tar
```

