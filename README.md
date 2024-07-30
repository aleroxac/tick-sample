# grafana-influx

POC usando o Grafana e Stack TICK(Telegraf, Influxdb, Cronograf e Kapacitor).


## Modo de uso
``` sh
## Subindo toda a Stack
docker volume create --name=tick_grafana_volume 
docker volume create --name=tick_influxdb_volume
docker volume create --name=tick_cronograf_volume
docker volume create --name=tick_kapacitor_volume
docker-compose up -d
docker-compose ps

## Escalando mais nós do Telegraf
docker-compose scale telegraf=3
docker-compose ps telegraf

## Estressando o container do Telegraf e visualizando as métricas via Grafana
docker-compose exec telegraf 'apt update && apt install -y stress & stress --cpu 2 --vm 6 --vm-bytes 2G --timeout 1m'
```


### Referências
- https://towardsdatascience.com/get-system-metrics-for-5-min-with-docker-telegraf-influxdb-and-grafana-97cfd957f0ac
- https://github.com/influxdata/telegraf
- https://www.tecmint.com/linux-cpu-load-stress-test-with-stress-ng-tool/
- https://guides.github.com/features/mastering-markdown/
