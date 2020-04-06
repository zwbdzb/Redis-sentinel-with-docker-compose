# Redis-sentinel-with-docker-compose
redis-sentinel ha deploy using docker-compose, the example deploy the basic model: 1 master, 2 slave, 3 sentinel  

![这里随便写文字](https://imgkr.cn-bj.ufileos.com/6145772a-0cfd-4760-8edf-450d2f1bd405.png)

## ideas
The redis-sentinel ha deploy is progressive， please deploy master/slave first, then  deploy redis sentinel with the master/slave bridge network, So the sentinels can communicate with all the redis node

## tip
1. please  config the sentinel config using the master container ip in the first deploy time
2. if you using `requirepass` set the client access pwd, please ensure usinng the `masterauth` set the replicas replication pwd
3. In the sentinel docker-copose.yml, if you have set the 'requirepass' set the master, please set the 'masterauth' for the master,
   because the master will become a slvae when failover，then it is also need a masterauth
