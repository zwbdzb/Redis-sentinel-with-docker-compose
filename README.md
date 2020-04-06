# Redis-sentinel-for-docker-compose
redis-sentinel ha deploy using docker-compose, the example deploy the basic model: 1 master, 2 slave, 3 sentinel


## ideas
this redis-sentinel ha deploy is progressive， please deploy master/slave first, then deploy deploy redis sentinel using the master/slave network, So the sentinels can communicate  with all the redis node

## Tip
1. please  config the sentinel config using the master container ip in the first deploy time
2. if you using `requirepass` set the client access pwd, please ensure usinng the `masterauth` set the replicas replication pwd
3. In the sentinel docker-copose.yml, if you have set the 'requirepass' set the master, please set the 'masterauth' for the master,
   because the master will become a slvae when failover，then it is also need a masterauth
