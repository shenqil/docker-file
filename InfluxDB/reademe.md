docker exec -it CONTAINER_NAME influxdb3 create token --admin

# 创建管理员 token
```
docker exec -it influxdb3 influxdb3 create token --admin
```


## 创建其他 token
```
docker exec -it influxdb3 influxdb3 create token --admin --token=you_token --name=hcs-admin
```


# 数据库
## 创建数据库 （数据永久保存）
```
docker exec -it influxdb3 influxdb3 create database --token you_token test
```

```
docker exec -it influxdb3 influxdb3 create database --token you_token hcs
```
## 创建数据库 （数据过期删除 30天）
```
docker exec -it influxdb3 influxdb3 create database --token you_token --retention-period 30d hcs-db
```

## 更新数据库保留期
### 更新为40天

```
docker exec -it influxdb3 influxdb3 update database --database hcs-db --token you_token --retention-period 40d
```
### 更新为永久
```
docker exec -it influxdb3 influxdb3 update database --database hcs-db --token you_token --retention-period none
```

## 查看数据库
```
docker exec -it influxdb3 influxdb3 show databases --token you_token
```




# 数据表
## 创建
```
docker exec -it influxdb3 influxdb3 create table \
  --tags device_sn \
  --fields S-1:float64,S-2:float64,S-3:float64,S-4:float64,S-5:float64,S-6:float64,S-7:float64,S-8:float64,S-9:float64,S-10:float64,S-11:float64,S-12:float64,S-13:float64,S-14:float64,S-15:float64,S-16:float64 \
  --database test \
  --token you_token \
  sensor_data
```

```
docker exec -it influxdb3 influxdb3 create table \
  --tags device_sn \
  --fields channel:uint64,operationType:uint64,operator:utf8 \
  --database test \
  --token you_token \
  relay_operations
```

## 查询
```
docker exec -it influxdb3 influxdb3 query \
  --database test \
  --token you_token \
  "SHOW TABLES"
```