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

功能：

- 支持同步、异步发送数据
- 支持单条、批量发送数据

TODO：

- 异步模式当前以后台线程支持http请求模式实现（修改为基于事件库的模式？）
- 批量暂时效率不高（修改为单条HTTP发生N条数据）

