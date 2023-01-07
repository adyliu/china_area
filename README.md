# 2023年中国全国5级行政区划（省、市、县、镇、村）

* 数据来源 中华人民共和国国家统计局 http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2022/index.html
* 最新数据量 664483 （2022年10月31日）
* CSV格式 area_code_2023.csv.gz
* SQL格式 area_code_2023.sql.gz
* JSON格式 单JSON格式太大就不生成了
* 建议级联操作，数据量确实太大了
* 级别
  * 1级：省、直辖市、自治区
  * 2级：地级市
  * 3级：市辖区、县（旗）、县级市、自治县（自治旗）、特区、林区
  * 4级：镇、乡、民族乡、县辖区、街道
  * 5级：村、居委会
* 城乡分类 (1开头是城镇，2开头是乡村)
  * 111表示主城区；
  * 112表示城乡接合区；
  * 121表示镇中心区；
  * 122表示镇乡接合区；
  * 123表示特殊区域；
  * 210表示乡中心区；
  * 220表示村庄

![summary](summary2023.png "汇总")
![total](total2023.png "分省汇总")

# 2009 - 2023 年数据对比

| 城乡分类 |  分类描述  |  2009  |  2023  |   差距  |
|----------|------------|--------|--------|---------|
|   111    |   主城区   | 58509  | 74838  |  +16329 |
|   112    | 城乡接合区 | 20389  | 30050  |  +9661  |
|   121    |  镇中心区  | 46440  | 53157  |  +6717  |
|   122    | 镇乡接合区 | 48447  | 54413  |  +5966  |
|   123    |  特殊区域  |  6525  |  5622  |   -903  |
|   210    |  乡中心区  | 23198  | 11557  |  -11641 |
|   220    |    村庄    | 496599 | 389865 | -106734 |


从数据可以看出13年来，村庄从`519797` 减少 `118375` 到 `401422`，减少了 22.77%，相应的城镇数量`+37820`。
大量人口从农村进入城镇，城镇化率大幅提升。

未来此趋势可能持续，大量的村庄将会荒废直至被合并至其他村庄或者取消行政村。

分省份来看2009-2023数据变化:

![2009-2023](2009-2023.png "分省查看变化")

按照乡村减少比例排序

|     code     |       name       | 乡村2009 | 乡村2023 | 乡村变化 |   比例   |
|--------------|------------------|----------|----------|----------|----------|
| 460000000000 |      海南省      |   5499   |   2269   |  -3230   | -58.7380 |
| 430000000000 |      湖南省      |  38202   |  19242   |  -18960  | -49.6309 |
| 610000000000 |      陕西省      |  23740   |  12647   |  -11093  | -46.7270 |
| 510000000000 |      四川省      |  43097   |  24403   |  -18694  | -43.3766 |
| 330000000000 |      浙江省      |  23643   |  13863   |  -9780   | -41.3653 |
| 370000000000 |      山东省      |  64691   |  40760   |  -23931  | -36.9928 |
| 140000000000 |      山西省      |  25350   |  16225   |  -9125   | -35.9961 |
| 420000000000 |      湖北省      |  22765   |  17303   |  -5462   | -23.9930 |
| 520000000000 |      贵州省      |  15636   |  12254   |  -3382   | -21.6296 |
| 320000000000 |      江苏省      |  11188   |   8951   |  -2237   | -19.9946 |
| 340000000000 |      安徽省      |  13697   |  11582   |  -2115   | -15.4413 |
| 310000000000 |      上海市      |   838    |   712    |   -126   | -15.0358 |
| 120000000000 |      天津市      |   2673   |   2373   |   -300   | -11.2233 |
| 620000000000 |      甘肃省      |  14911   |  13557   |  -1354   | -9.0805  |
| 360000000000 |      江西省      |  14642   |  13386   |  -1256   | -8.5781  |
| 130000000000 |      河北省      |  39616   |  36338   |  -3278   | -8.2744  |
| 630000000000 |      青海省      |   3927   |   3626   |   -301   | -7.6649  |
| 640000000000 |  宁夏回族自治区  |   2062   |   1911   |   -151   | -7.3230  |
| 650000000000 | 新疆维吾尔自治区 |  10686   |  10070   |   -616   | -5.7646  |
| 450000000000 |  广西壮族自治区  |  13143   |  12511   |   -632   | -4.8086  |
| 530000000000 |      云南省      |  11803   |  11260   |   -543   | -4.6005  |
| 110000000000 |      北京市      |   2807   |   2686   |   -121   | -4.3107  |
| 410000000000 |      河南省      |  38078   |  36504   |  -1574   | -4.1336  |
| 350000000000 |      福建省      |  11825   |  11412   |   -413   | -3.4926  |
| 150000000000 |   内蒙古自治区   |  10908   |  10737   |   -171   | -1.5677  |
| 230000000000 |     黑龙江省     |   9197   |   9129   |   -68    | -0.7394  |
| 220000000000 |      吉林省      |   8402   |   8402   |    0     |  0.0000  |
| 540000000000 |    西藏自治区    |   5162   |   5188   |    26    |  0.5037  |
| 440000000000 |      广东省      |  14662   |  14740   |    78    |  0.5320  |
| 210000000000 |      辽宁省      |   9502   |   9678   |   176    |  1.8522  |
| 500000000000 |      重庆市      |   7445   |   7703   |   258    |  3.4654  |

一些有意思的数据：
- 市这个级别比较稳定，数据变化不大
- 绝大部分省份的城镇数量都在增加，只有黑龙江（`-214`）和四川（`-451`）的城镇有所减少
- 绝大部分省份的乡村数量都在减少，只有辽宁（`+176`）、广东（`+79`）、重庆（`+258`）、西藏（`+26`）的乡村数量在增加
- 吉林省的乡村数量绝对值没有变化(TODO：需要看历史数据变化)
- 山东省减少了`-23931`个乡村，同比减少`-37%`，是减少最多的省份
- 湖南、四川、山西减少的乡村数都超过10000个
- 海南、湖南、陕西、四川、浙江的乡村减少比例排在前5，都超过`41%`的比例
----


## CSV格式

* code,name,level,pcode
* level: 省1，市2，县3，镇4，村5
* code: 12位，省2位，市2位，县2位，镇3位，村3位
* pcode: 直接父级别的code

文本内容

```bash
$ gzcat area_code_2023.csv.gz |wc -l
  664483

$ gzcat area_code_2022.csv.gz |head
110101001001,多福巷社区居委会,5,110101001000
110101001002,银闸社区居委会,5,110101001000
110101001005,东厂社区居委会,5,110101001000
110101001006,智德社区居委会,5,110101001000
110101001007,南池子社区居委会,5,110101001000
110101001009,灯市口社区居委会,5,110101001000
110101001010,正义路社区居委会,5,110101001000
110101001013,台基厂社区居委会,5,110101001000
110101001014,韶九社区居委会,5,110101001000
110101001015,王府井社区居委会,5,110101001000
```

## SQL 格式

> $ gzcat area_code_2023.sql.gz |head -n 34

```sql
-- MariaDB dump 10.18  Distrib 10.5.8-MariaDB, for Linux ()
--
-- Host: localhost    Database: china_area
-- ------------------------------------------------------
-- Server version 10.5.8-MariaDB-log

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `area_code_2023`
--

DROP TABLE IF EXISTS `area_code_2023`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `area_code_2023` (
  `code` bigint(12) unsigned NOT NULL COMMENT '区划代码',
  `name` varchar(128) NOT NULL DEFAULT '' COMMENT '名称',
  `level` tinyint(1) NOT NULL COMMENT '级别1-5,省市县镇村',
  `pcode` bigint(12) DEFAULT NULL COMMENT '父级区划代码',
  PRIMARY KEY (`code`),
  KEY `name` (`name`),
  KEY `level` (`level`),
  KEY `pcode` (`pcode`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

```

> 创建视图 area_index_2023

```sql
CREATE VIEW area_index_2023 AS
    SELECT a.code,e.name AS province,d.name AS city  ,c.name AS county,b.name AS town,a.name AS villagetr
    FROM area_code_2023 a
        JOIN area_code_2023 b ON a.level=5 AND b.level=4 AND a.pcode=b.code
        JOIN area_code_2023 c ON b.pcode=c.code
        JOIN area_code_2023 d ON c.pcode=d.code
        JOIN area_code_2023 e ON d.pcode=e.code
    ORDER BY a.code
```

查询几条记录

> SELECT * FROM area_index_2023 LIMIT 10

```text
+--------------+-----------+-----------+-----------+-----------------+--------------------------+
| code         | province  | city      | county    | town            | villagetr                |
+--------------+-----------+-----------+-----------+-----------------+--------------------------+
| 110101001001 | 北京市    | 市辖区    | 东城区    | 东华门街道      | 多福巷社区居委会         |
| 110101001002 | 北京市    | 市辖区    | 东城区    | 东华门街道      | 银闸社区居委会           |
| 110101001005 | 北京市    | 市辖区    | 东城区    | 东华门街道      | 东厂社区居委会           |
| 110101001006 | 北京市    | 市辖区    | 东城区    | 东华门街道      | 智德社区居委会           |
| 110101001007 | 北京市    | 市辖区    | 东城区    | 东华门街道      | 南池子社区居委会         |
| 110101001009 | 北京市    | 市辖区    | 东城区    | 东华门街道      | 灯市口社区居委会         |
| 110101001010 | 北京市    | 市辖区    | 东城区    | 东华门街道      | 正义路社区居委会         |
| 110101001013 | 北京市    | 市辖区    | 东城区    | 东华门街道      | 台基厂社区居委会         |
| 110101001014 | 北京市    | 市辖区    | 东城区    | 东华门街道      | 韶九社区居委会           |
| 110101001015 | 北京市    | 市辖区    | 东城区    | 东华门街道      | 王府井社区居委会         |
+--------------+-----------+-----------+-----------+-----------------+--------------------------+
```

## 三级区划的JSON格式

JSON格式，适合web端js加载。


```json
[
  {
    "code": 110000000000,
    "name": "北京市",
    "level": 1,
    "pcode": 0,
    "children": [
      {
        "code": 110100000000,
        "name": "市辖区",
        "level": 2,
        "pcode": 110000000000,
        "children": [
          {
            "code": 110101000000,
            "name": "东城区",
            "level": 3,
            "pcode": 110100000000
          },
          {
            "code": 110102000000,
            "name": "西城区",
            "level": 3,
            "pcode": 110100000000
          }
        ]
      }
    ]
  }
]
```

## 文件列表

- [area_code_2023.csv.gz](area_code_2023.csv.gz)
- [area_code_2023.sql.gz](area_code_2023.sql.gz)
- [area_code_2023.json](area_code_2023.json)