# tiny-influxpp

用法：

``` C++
uint32_t charid = 1024;

    InfluxDB *influx = new InfluxDB("http://127.0.0.1:8086/write?db=example");

    // 全局Tags
    influx->addGlobalTag("game", "zt2");
    influx->addGlobalTag("game_type", "17");
    influx->addGlobalTag("zone", "风雨同舟");
    influx->addGlobalTag("zone_id", "2208");

    // 全局Fields
    influx->addGlobalFieldInt("charid", charid);
    influx->addGlobalFieldString("mac", "aa-bb-cc-dd");


    // 写入一条数据
    influx->write_async(Metric{"clientping"}
                          .tag("build", "2008")
                          .tag("version", "0.0.0")
                          .fieldInt("ping", 1024)
                          .fieldFloat("salary", 1024.6)
                          .fieldString("name", "david"));
```

