# Redis-sentinel-with-docker-compose
redis-sentinel ha deploy using docker-compose, the example deploy the basic model: 1 master, 2 slave, 3 sentinel  

![这里随便写文字](https://imgkr.cn-bj.ufileos.com/6145772a-0cfd-4760-8edf-450d2f1bd405.png)

## ideas
The redis-sentinel ha deploy is progressive， please deploy master/slave first, then  deploy redis sentinel with the master/slave bridge network, So the sentinels can communicate with all the redis master/slave nodes.

## redis client apps
 - deploy with the  same machine  
   : The  redis client apps can link the same above  docker bridge network that can access the whole redis-sentinel
 - deploy in other machine  
   : please alter the sentinel with the machine Ip and bind port （not the above  master container ip and cotainer expose ip）
   
## tip
1. please  config the sentinel config using the master [container ip] in the first deploy time
  >  when redis redis app deploy independence machine， please config the sentinel.conf with the  machine ip and  bind port
2. if you using `requirepass` set the client access pwd, please ensure usinng the `masterauth` set the replicas replication pwd
3. In the sentinel docker-copose.yml, if you have set the 'requirepass' for  the master, please set the 'masterauth' for the master,
   because the master will become a slvae when failover，then it is also need a masterauth
