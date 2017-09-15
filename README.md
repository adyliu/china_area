# 2017年中国全国5级行政区划（省、市、县、镇、村）

* 数据来源 中华人民共和国国家统计局 http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2016/
* 最新数据量 713031 （2017/09/15）
* CSV格式 area_code.csv.gz
* SQL格式 area_code.sql.gz
* JSON格式 单JSON格式太大就不生成了
* 建议级联操作，数据量确实太大了


## CSV格式

* level,code,name,[code,name...]
* level: 省1，市2，县3，镇4，村5


    $ gzcat area_code.csv.gz |wc -l
      713031

    $ gzcat area_code.csv.gz |head
    1,11,北京市
    2,11,北京市,110100000000,市辖区
    3,11,北京市,110100000000,市辖区,110101000000,东城区
    4,11,北京市,110100000000,市辖区,110101000000,东城区,110101001000,东华门街道办事处
    5,11,北京市,110100000000,市辖区,110101000000,东城区,110101001000,东华门街道办事处,110101001001,多福巷社区居委会
    5,11,北京市,110100000000,市辖区,110101000000,东城区,110101001000,东华门街道办事处,110101001002,银闸社区居委会
    5,11,北京市,110100000000,市辖区,110101000000,东城区,110101001000,东华门街道办事处,110101001005,东厂社区居委会
    5,11,北京市,110100000000,市辖区,110101000000,东城区,110101001000,东华门街道办事处,110101001006,智德社区居委会
    5,11,北京市,110100000000,市辖区,110101000000,东城区,110101001000,东华门街道办事处,110101001007,南池子社区居委会
    5,11,北京市,110100000000,市辖区,110101000000,东城区,110101001000,东华门街道办事处,110101001008,黄图岗社区居委会


## SELECT count(*) FROM area_code

    713031


## on OS X:

    $ gzcat area_code.sql.gz |head -n 38
    # ************************************************************
    # Sequel Pro SQL dump
    # Version 4541
    #
    # http://www.sequelpro.com/
    # https://github.com/sequelpro/sequelpro
    #
    # Host: 127.0.0.1 (MySQL 5.7.9-log)
    # Database: bang
    # Generation Time: 2017-09-15 05:52:08 +0000
    # ************************************************************


    /*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
    /*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
    /*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
    /*!40101 SET NAMES utf8 */;
    /*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
    /*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
    /*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;


    # Dump of table area_code
    # ------------------------------------------------------------

    DROP TABLE IF EXISTS `area_code`;

    CREATE TABLE `area_code` (
      `code` bigint(12) unsigned NOT NULL AUTO_INCREMENT COMMENT '区划代码',
      `name` varchar(32) NOT NULL DEFAULT '' COMMENT '名称',
      `level` tinyint(1) NOT NULL COMMENT '级别1-5,省市县镇村',
      `pcode` bigint(12) DEFAULT NULL COMMENT '父级区划代码',
      PRIMARY KEY (`code`),
      KEY `name` (`name`),
      KEY `level` (`level`),
      KEY `pcode` (`pcode`)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

## 创建视图area_index

    CREATE VIEW area_index AS
        SELECT a.code,e.name AS province,d.name AS city  ,c.name AS county,b.name AS town,a.name AS villagetr FROM area_code a
            JOIN area_code b ON a.level=5 AND b.level=4 AND a.pcode=b.code
            JOIN area_code c ON b.pcode=c.code
            JOIN area_code d ON c.pcode=d.code
            JOIN area_code e ON d.pcode=e.code
        ORDER BY a.code


SELECT * FROM area_index LIMIT 10

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