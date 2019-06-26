# tiny-influxpp

依赖：

- C++ 11
- libcurl

用法：

``` C++
    using namespace influxdb;

    uint32_t charid = 1024;

    InfluxDB *influx = new InfluxDB("http://127.0.0.1:8086/write?db=example");

    // 全局Tags
    influx->addGlobalTag("game", "zt2");
    influx->addGlobalTag("game_type", "17");
    influx->addGlobalTag("zone", "风雨同舟");
    influx->addGlobalTag("zone_id", "2208");

    // 全局Fields
    influx->addGlobalField("charid", charid);
    influx->addGlobalField("mac", "aa-bb-cc-dd");


    // 写入一条数据
    influx->write_async(Metric{"clientping"}
                          .tag("build", "2008")
                          .tag("version", "0.0.0")
                          .field("ping", 1024)
                          .field("salary", 1024.6)
                          .field("name", "david")
                          .timestamp());

```

