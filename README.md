# 2019年中国全国5级行政区划（省、市、县、镇、村）

* 数据来源 中华人民共和国国家统计局 http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2018/
* 最新数据量 713479 （2018年10月31日）
* CSV格式 area_code_xxxx.csv.gz
* SQL格式 area_code_xxxx.sql.gz
* JSON格式 单JSON格式太大就不生成了
* 建议级联操作，数据量确实太大了
* 级别
  * 1级：省、直辖市、自治区
  * 2级：地级市
  * 3级：市辖区、县（旗）、县级市、自治县（自治旗）、特区、林区
  * 4级：镇、乡、民族乡、县辖区、街道
  * 5级：村、居委会


![summary](summary.png "汇总")

## CSV格式

* code,name,level,pcode
* level: 省1，市2，县3，镇4，村5
* code: 12位，省2位，市2位，县2位，镇3位，村3位
* pcode: 直接父级别的code

文本内容

```bash
$ gzcat area_code_2019.csv.gz |wc -l
  713479

$ gzcat area_code_2019.csv.gz |head
110101001001,多福巷社区居委会,5,110101001000
110101001002,银闸社区居委会,5,110101001000
110101001005,东厂社区居委会,5,110101001000
110101001006,智德社区居委会,5,110101001000
110101001007,南池子社区居委会,5,110101001000
110101001008,黄图岗社区居委会,5,110101001000
110101001009,灯市口社区居委会,5,110101001000
110101001010,正义路社区居委会,5,110101001000
110101001011,甘雨社区居委会,5,110101001000
110101001013,台基厂社区居委会,5,110101001000
```

## SQL 格式

> $ gzcat area_code_2019.sql.gz |head -n 38

```sql
$ gzcat area_code_2019.sql.gz |head -n 38
# ************************************************************
# Sequel Pro SQL dump
# Version 5428
#
# https://www.sequelpro.com/
# https://github.com/sequelpro/sequelpro
#
# Host: 127.0.0.1 (MySQL 8.0.13)
# Database: china_area
# Generation Time: 2019-03-07 10:27:09 +0000
# ************************************************************


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8 */;
SET NAMES utf8mb4;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;


# Dump of table area_code_2019
# ------------------------------------------------------------

DROP TABLE IF EXISTS `area_code_2019`;

CREATE TABLE `area_code_2019` (
  `code` bigint(12) unsigned NOT NULL COMMENT '区划代码',
  `name` varchar(128) NOT NULL DEFAULT '' COMMENT '名称',
  `level` tinyint(1) NOT NULL COMMENT '级别1-5,省市县镇村',
  `pcode` bigint(12) DEFAULT NULL COMMENT '父级区划代码',
  PRIMARY KEY (`code`),
  KEY `name` (`name`),
  KEY `level` (`level`),
  KEY `pcode` (`pcode`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
```

> 创建视图area_index

```sql
CREATE VIEW area_index_2019 AS
    SELECT a.code,e.name AS province,d.name AS city  ,c.name AS county,b.name AS town,a.name AS villagetr
    FROM area_code_2019 a
        JOIN area_code_2019 b ON a.level=5 AND b.level=4 AND a.pcode=b.code
        JOIN area_code_2019 c ON b.pcode=c.code
        JOIN area_code_2019 d ON c.pcode=d.code
        JOIN area_code_2019 e ON d.pcode=e.code
    ORDER BY a.code
```

查询几条记录

> SELECT * FROM area_index_2019 LIMIT 10

```text
code    province    city    county  town    villagetr
110101001001    北京市 市辖区 东城区 东华门街道办事处    多福巷社区居委会
110101001002    北京市 市辖区 东城区 东华门街道办事处    银闸社区居委会
110101001005    北京市 市辖区 东城区 东华门街道办事处    东厂社区居委会
110101001006    北京市 市辖区 东城区 东华门街道办事处    智德社区居委会
110101001007    北京市 市辖区 东城区 东华门街道办事处    南池子社区居委会
110101001008    北京市 市辖区 东城区 东华门街道办事处    黄图岗社区居委会
110101001009    北京市 市辖区 东城区 东华门街道办事处    灯市口社区居委会
110101001010    北京市 市辖区 东城区 东华门街道办事处    正义路社区居委会
110101001011    北京市 市辖区 东城区 东华门街道办事处    甘雨社区居委会
110101001013    北京市 市辖区 东城区 东华门街道办事处    台基厂社区居委会
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

- area_code_2019.csv.gz
- area_code_2019.sql.gz
- area_code_2019.json