# /\*

#  Navicat MySQL Data Transfer

# 

#  Source Server         : java

#  Source Server Type    : MySQL

#  Source Server Version : 80029

#  Source Host           : localhost:3306

#  Source Schema         : advisor

# 

#  Target Server Type    : MySQL

#  Target Server Version : 80029

#  File Encoding         : 65001

# 

#  Date: 10/07/2025 10:11:23

# \*/

# 

# SET NAMES utf8mb4;

# SET FOREIGN\_KEY\_CHECKS = 0;

# 

# -- ----------------------------

# -- Table structure for a1\_fof\_config

# -- ----------------------------

# DROP TABLE IF EXISTS `a1\\\\\\\_fof\\\\\\\_config`;

# CREATE TABLE `a1\\\\\\\_fof\\\\\\\_config`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `fund\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金名称',

#   `weight` decimal(10, 4) NOT NULL COMMENT '权重',

#   `asset\\\\\\\_class` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '资产类别',

#   `rebalance\\\\\\\_frequency` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '再平衡频率',

#   `stop\\\\\\\_loss` decimal(10, 4) NULL DEFAULT NULL COMMENT '止损线',

#   `take\\\\\\\_profit` decimal(10, 4) NULL DEFAULT NULL COMMENT '止盈线',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '活跃' COMMENT '状态：活跃、暂停',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   `updated\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) ON UPDATE CURRENT\_TIMESTAMP(0) COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_fund\\\\\\\_code`(`fund\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE

# ) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = 'FOF组合配置表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a1\_fof\_config

# -- ----------------------------

# 

# -- ----------------------------

# -- Table structure for a1\_fof\_monitor

# -- ----------------------------

# DROP TABLE IF EXISTS `a1\\\\\\\_fof\\\\\\\_monitor`;

# CREATE TABLE `a1\\\\\\\_fof\\\\\\\_monitor`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `monitor\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '监控类型：风险监控、绩效监控、再平衡监控',

#   `monitor\\\\\\\_date` date NOT NULL COMMENT '监控日期',

#   `total\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '总收益率',

#   `annual\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '年化收益率',

#   `max\\\\\\\_drawdown` decimal(10, 4) NULL DEFAULT NULL COMMENT '最大回撤',

#   `sharpe\\\\\\\_ratio` decimal(10, 4) NULL DEFAULT NULL COMMENT '夏普比率',

#   `volatility` decimal(10, 4) NULL DEFAULT NULL COMMENT '波动率',

#   `beta` decimal(10, 4) NULL DEFAULT NULL COMMENT '贝塔系数',

#   `alpha` decimal(10, 4) NULL DEFAULT NULL COMMENT '阿尔法系数',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '正常' COMMENT '状态：正常、预警、异常',

#   `alert\\\\\\\_message` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '预警信息',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_monitor\\\\\\\_date`(`monitor\\\\\\\_date`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE

# ) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = 'FOF组合监控表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a1\_fof\_monitor

# -- ----------------------------

# 

# -- ----------------------------

# -- Table structure for a1\_fof\_portfolio

# -- ----------------------------

# DROP TABLE IF EXISTS `a1\\\\\\\_fof\\\\\\\_portfolio`;

# CREATE TABLE `a1\\\\\\\_fof\\\\\\\_portfolio`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合名称',

#   `portfolio\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合类型：FOF',

#   `risk\\\\\\\_level` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '风险等级：低风险、中风险、高风险',

#   `target\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '目标收益率',

#   `max\\\\\\\_drawdown` decimal(10, 4) NULL DEFAULT NULL COMMENT '最大回撤',

#   `strategy\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '策略代码',

#   `asset\\\\\\\_allocation` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '资产配置JSON',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '草稿' COMMENT '状态：草稿、活跃、暂停',

#   `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '组合描述',

#   `created\\\\\\\_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建人',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   `updated\\\\\\\_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新人',

#   `updated\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) ON UPDATE CURRENT\_TIMESTAMP(0) COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE,

#   INDEX `idx\\\\\\\_created\\\\\\\_time`(`created\\\\\\\_time`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 2 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = 'FOF组合表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a1\_fof\_portfolio

# -- ----------------------------

# INSERT INTO `a1\\\\\\\_fof\\\\\\\_portfolio` VALUES (2, '444', '444', 'FOF', '低风险', 44.0000, 44.0000, '444', '44', '草稿', '44', '44', '2025-07-06 20:01:28', NULL, '2025-07-06 20:01:28');

# 

# -- ----------------------------

# -- Table structure for a2\_index\_config

# -- ----------------------------

# DROP TABLE IF EXISTS `a2\\\\\\\_index\\\\\\\_config`;

# CREATE TABLE `a2\\\\\\\_index\\\\\\\_config`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `fund\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金名称',

#   `weight` decimal(10, 4) NOT NULL COMMENT '权重',

#   `asset\\\\\\\_class` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '资产类别',

#   `rebalance\\\\\\\_frequency` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '再平衡频率',

#   `tracking\\\\\\\_error\\\\\\\_limit` decimal(10, 4) NULL DEFAULT NULL COMMENT '跟踪误差限制',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '活跃' COMMENT '状态：活跃、暂停',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   `updated\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) ON UPDATE CURRENT\_TIMESTAMP(0) COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_fund\\\\\\\_code`(`fund\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE

# ) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '指数组合配置表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a2\_index\_config

# -- ----------------------------

# 

# -- ----------------------------

# -- Table structure for a2\_index\_monitor

# -- ----------------------------

# DROP TABLE IF EXISTS `a2\\\\\\\_index\\\\\\\_monitor`;

# CREATE TABLE `a2\\\\\\\_index\\\\\\\_monitor`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `monitor\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '监控类型：跟踪误差监控、绩效监控、再平衡监控',

#   `monitor\\\\\\\_date` date NOT NULL COMMENT '监控日期',

#   `total\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '总收益率',

#   `index\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '指数收益率',

#   `tracking\\\\\\\_error` decimal(10, 4) NULL DEFAULT NULL COMMENT '跟踪误差',

#   `information\\\\\\\_ratio` decimal(10, 4) NULL DEFAULT NULL COMMENT '信息比率',

#   `beta` decimal(10, 4) NULL DEFAULT NULL COMMENT '贝塔系数',

#   `alpha` decimal(10, 4) NULL DEFAULT NULL COMMENT '阿尔法系数',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '正常' COMMENT '状态：正常、预警、异常',

#   `alert\\\\\\\_message` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '预警信息',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_monitor\\\\\\\_date`(`monitor\\\\\\\_date`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE

# ) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '指数组合监控表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a2\_index\_monitor

# -- ----------------------------

# 

# -- ----------------------------

# -- Table structure for a2\_index\_portfolio

# -- ----------------------------

# DROP TABLE IF EXISTS `a2\\\\\\\_index\\\\\\\_portfolio`;

# CREATE TABLE `a2\\\\\\\_index\\\\\\\_portfolio`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合名称',

#   `portfolio\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合类型：指数型',

#   `index\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '指数代码',

#   `index\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '指数名称',

#   `risk\\\\\\\_level` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '风险等级：低风险、中风险、高风险',

#   `target\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '目标收益率',

#   `tracking\\\\\\\_error` decimal(10, 4) NULL DEFAULT NULL COMMENT '跟踪误差',

#   `strategy\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '策略代码',

#   `asset\\\\\\\_allocation` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '资产配置JSON',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '草稿' COMMENT '状态：草稿、活跃、暂停',

#   `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '组合描述',

#   `created\\\\\\\_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建人',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   `updated\\\\\\\_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新人',

#   `updated\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) ON UPDATE CURRENT\_TIMESTAMP(0) COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_index\\\\\\\_code`(`index\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE,

#   INDEX `idx\\\\\\\_created\\\\\\\_time`(`created\\\\\\\_time`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 2 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '指数组合表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a2\_index\_portfolio

# -- ----------------------------

# INSERT INTO `a2\\\\\\\_index\\\\\\\_portfolio` VALUES (1, 'A2\_20250706192226', '996', '指数型', '996', '996', 'HIGH', 0.0400, 0.0400, '996', NULL, '草稿', '996', NULL, '2025-07-06 19:22:26', NULL, '2025-07-06 19:22:26');

# INSERT INTO `a2\\\\\\\_index\\\\\\\_portfolio` VALUES (2, 'A2\_20250706193240', '555', '指数型', '555', '中证500', '中风险', NULL, NULL, '555', NULL, '活跃', '555', NULL, '2025-07-06 19:32:40', NULL, '2025-07-06 19:42:53');

# 

# -- ----------------------------

# -- Table structure for a3\_timing\_config

# -- ----------------------------

# DROP TABLE IF EXISTS `a3\\\\\\\_timing\\\\\\\_config`;

# CREATE TABLE `a3\\\\\\\_timing\\\\\\\_config`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `fund\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金名称',

#   `weight` decimal(10, 4) NOT NULL COMMENT '权重',

#   `asset\\\\\\\_class` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '资产类别',

#   `timing\\\\\\\_rules` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '择时规则JSON',

#   `stop\\\\\\\_loss` decimal(10, 4) NULL DEFAULT NULL COMMENT '止损线',

#   `take\\\\\\\_profit` decimal(10, 4) NULL DEFAULT NULL COMMENT '止盈线',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '活跃' COMMENT '状态：活跃、暂停',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   `updated\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) ON UPDATE CURRENT\_TIMESTAMP(0) COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_fund\\\\\\\_code`(`fund\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE

# ) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '择时组合配置表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a3\_timing\_config

# -- ----------------------------

# 

# -- ----------------------------

# -- Table structure for a3\_timing\_monitor

# -- ----------------------------

# DROP TABLE IF EXISTS `a3\\\\\\\_timing\\\\\\\_monitor`;

# CREATE TABLE `a3\\\\\\\_timing\\\\\\\_monitor`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `monitor\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '监控类型：择时信号监控、绩效监控、风险监控',

#   `monitor\\\\\\\_date` date NOT NULL COMMENT '监控日期',

#   `total\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '总收益率',

#   `annual\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '年化收益率',

#   `max\\\\\\\_drawdown` decimal(10, 4) NULL DEFAULT NULL COMMENT '最大回撤',

#   `sharpe\\\\\\\_ratio` decimal(10, 4) NULL DEFAULT NULL COMMENT '夏普比率',

#   `timing\\\\\\\_accuracy` decimal(10, 4) NULL DEFAULT NULL COMMENT '择时准确率',

#   `signal\\\\\\\_count` int NULL DEFAULT NULL COMMENT '信号次数',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '正常' COMMENT '状态：正常、预警、异常',

#   `alert\\\\\\\_message` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '预警信息',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_monitor\\\\\\\_date`(`monitor\\\\\\\_date`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE

# ) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '择时组合监控表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a3\_timing\_monitor

# -- ----------------------------

# 

# -- ----------------------------

# -- Table structure for a3\_timing\_portfolio

# -- ----------------------------

# DROP TABLE IF EXISTS `a3\\\\\\\_timing\\\\\\\_portfolio`;

# CREATE TABLE `a3\\\\\\\_timing\\\\\\\_portfolio`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合名称',

#   `portfolio\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合类型：择时型',

#   `timing\\\\\\\_strategy` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '择时策略',

#   `risk\\\\\\\_level` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '风险等级：低风险、中风险、高风险',

#   `target\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '目标收益率',

#   `max\\\\\\\_drawdown` decimal(10, 4) NULL DEFAULT NULL COMMENT '最大回撤',

#   `strategy\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '策略代码',

#   `asset\\\\\\\_allocation` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '资产配置JSON',

#   `timing\\\\\\\_signals` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '择时信号JSON',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '草稿' COMMENT '状态：草稿、活跃、暂停',

#   `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '组合描述',

#   `created\\\\\\\_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建人',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   `updated\\\\\\\_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新人',

#   `updated\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) ON UPDATE CURRENT\_TIMESTAMP(0) COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_timing\\\\\\\_strategy`(`timing\\\\\\\_strategy`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE,

#   INDEX `idx\\\\\\\_created\\\\\\\_time`(`created\\\\\\\_time`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 2 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '择时组合表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a3\_timing\_portfolio

# -- ----------------------------

# INSERT INTO `a3\\\\\\\_timing\\\\\\\_portfolio` VALUES (1, 'A3\_20250706192252', '996', '择时型', '技术分析', 'LOW', 0.0300, 0.0300, '996', NULL, '996', '草稿', '996', NULL, '2025-07-06 19:22:52', NULL, '2025-07-06 19:22:52');

# INSERT INTO `a3\\\\\\\_timing\\\\\\\_portfolio` VALUES (2, 'A3\_20250706193334', '555', '择时型', '基本面分析', '低风险', NULL, NULL, '555', NULL, NULL, '活跃', '555', NULL, '2025-07-06 19:33:34', NULL, '2025-07-06 19:43:07');

# 

# -- ----------------------------

# -- Table structure for a4\_holding\_fund

# -- ----------------------------

# DROP TABLE IF EXISTS `a4\\\\\\\_holding\\\\\\\_fund`;

# CREATE TABLE `a4\\\\\\\_holding\\\\\\\_fund`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `fund\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金名称',

#   `holding\\\\\\\_amount` decimal(15, 2) NOT NULL COMMENT '持仓金额',

#   `holding\\\\\\\_quantity` decimal(15, 4) NOT NULL COMMENT '持仓数量',

#   `current\\\\\\\_price` decimal(10, 4) NULL DEFAULT NULL COMMENT '当前价格',

#   `cost\\\\\\\_price` decimal(10, 4) NULL DEFAULT NULL COMMENT '成本价格',

#   `weight` decimal(10, 4) NOT NULL COMMENT '权重',

#   `profit\\\\\\\_loss` decimal(15, 2) NULL DEFAULT NULL COMMENT '盈亏',

#   `profit\\\\\\\_loss\\\\\\\_rate` decimal(10, 4) NULL DEFAULT NULL COMMENT '盈亏率',

#   `asset\\\\\\\_class` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '资产类别',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '持有' COMMENT '状态：持有、卖出',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   `updated\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) ON UPDATE CURRENT\_TIMESTAMP(0) COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_fund\\\\\\\_code`(`fund\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '持仓基金表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a4\_holding\_fund

# -- ----------------------------

# INSERT INTO `a4\\\\\\\_holding\\\\\\\_fund` VALUES (1, '666', '666', '666', 666.00, 666.0000, 666.0000, 666.0000, 666.0000, 666.00, 666.0000, '666', '持有', '2025-07-06 19:44:52', '2025-07-06 19:44:52');

# 

# -- ----------------------------

# -- Table structure for a4\_rebalance\_history

# -- ----------------------------

# DROP TABLE IF EXISTS `a4\\\\\\\_rebalance\\\\\\\_history`;

# CREATE TABLE `a4\\\\\\\_rebalance\\\\\\\_history`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `rebalance\\\\\\\_date` date NOT NULL COMMENT '调仓日期',

#   `rebalance\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '调仓类型：定期调仓、触发调仓、手动调仓',

#   `fund\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金名称',

#   `action\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '操作类型：买入、卖出、调整',

#   `old\\\\\\\_weight` decimal(10, 4) NULL DEFAULT NULL COMMENT '原权重',

#   `new\\\\\\\_weight` decimal(10, 4) NULL DEFAULT NULL COMMENT '新权重',

#   `quantity\\\\\\\_change` decimal(15, 4) NULL DEFAULT NULL COMMENT '数量变化',

#   `amount\\\\\\\_change` decimal(15, 2) NULL DEFAULT NULL COMMENT '金额变化',

#   `reason` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '调仓原因',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '已完成' COMMENT '状态：待执行、执行中、已完成、失败',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_rebalance\\\\\\\_date`(`rebalance\\\\\\\_date`) USING BTREE,

#   INDEX `idx\\\\\\\_fund\\\\\\\_code`(`fund\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '历史调仓表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a4\_rebalance\_history

# -- ----------------------------

# INSERT INTO `a4\\\\\\\_rebalance\\\\\\\_history` VALUES (1, '111', '2025-07-06', '111', '111', '111', '111', 111.0000, 111.0000, 111.0000, 111.00, '111', '已完成', '2025-07-06 19:45:23');

# 

# -- ----------------------------

# -- Table structure for a4\_strategy\_return

# -- ----------------------------

# DROP TABLE IF EXISTS `a4\\\\\\\_strategy\\\\\\\_return`;

# CREATE TABLE `a4\\\\\\\_strategy\\\\\\\_return`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `strategy\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略代码',

#   `strategy\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略名称',

#   `return\\\\\\\_date` date NOT NULL COMMENT '收益日期',

#   `daily\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '日收益率',

#   `cumulative\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '累计收益率',

#   `annual\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '年化收益率',

#   `max\\\\\\\_drawdown` decimal(10, 4) NULL DEFAULT NULL COMMENT '最大回撤',

#   `sharpe\\\\\\\_ratio` decimal(10, 4) NULL DEFAULT NULL COMMENT '夏普比率',

#   `volatility` decimal(10, 4) NULL DEFAULT NULL COMMENT '波动率',

#   `beta` decimal(10, 4) NULL DEFAULT NULL COMMENT '贝塔系数',

#   `alpha` decimal(10, 4) NULL DEFAULT NULL COMMENT '阿尔法系数',

#   `benchmark\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '基准收益率',

#   `excess\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '超额收益',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_strategy\\\\\\\_code`(`strategy\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_return\\\\\\\_date`(`return\\\\\\\_date`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '策略收益表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a4\_strategy\_return

# -- ----------------------------

# INSERT INTO `a4\\\\\\\_strategy\\\\\\\_return` VALUES (1, '333', '333', '333', '2025-07-01', 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, '2025-07-06 19:46:21');

# 

# -- ----------------------------

# -- Table structure for a4\_today\_trade

# -- ----------------------------

# DROP TABLE IF EXISTS `a4\\\\\\\_today\\\\\\\_trade`;

# CREATE TABLE `a4\\\\\\\_today\\\\\\\_trade`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键ID',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `trade\\\\\\\_date` date NOT NULL COMMENT '交易日期',

#   `fund\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金名称',

#   `trade\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '交易类型：买入、卖出',

#   `trade\\\\\\\_amount` decimal(15, 2) NOT NULL COMMENT '交易金额',

#   `trade\\\\\\\_quantity` decimal(15, 4) NOT NULL COMMENT '交易数量',

#   `trade\\\\\\\_price` decimal(10, 4) NULL DEFAULT NULL COMMENT '交易价格',

#   `commission` decimal(10, 2) NULL DEFAULT NULL COMMENT '手续费',

#   `trade\\\\\\\_reason` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '交易原因',

#   `strategy\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '策略代码',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '已成交' COMMENT '状态：待成交、已成交、已取消',

#   `created\\\\\\\_time` datetime(0) NULL DEFAULT CURRENT\_TIMESTAMP(0) COMMENT '创建时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   INDEX `idx\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_date`(`trade\\\\\\\_date`) USING BTREE,

#   INDEX `idx\\\\\\\_fund\\\\\\\_code`(`fund\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_status`(`status`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '今日成交表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of a4\_today\_trade

# -- ----------------------------

# INSERT INTO `a4\\\\\\\_today\\\\\\\_trade` VALUES (1, '222', '2025-07-17', '222', '222', '222', 222.00, 222.0000, 222.0000, 222.00, '222', '222', '已成交', '2025-07-06 19:45:49');

# 

# -- ----------------------------

# -- Table structure for b1\_strategy\_audit

# -- ----------------------------

# DROP TABLE IF EXISTS `b1\\\\\\\_strategy\\\\\\\_audit`;

# CREATE TABLE `b1\\\\\\\_strategy\\\\\\\_audit`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键',

#   `strategy\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略组合名称',

#   `strategy\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '类型（策略/FOF）',

#   `submitter` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '提交人',

#   `submit\\\\\\\_time` datetime(0) NOT NULL COMMENT '提交时间',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '审核状态（待审核/已上架/驳回）',

#   `audit\\\\\\\_opinion` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '审核意见',

#   `audit\\\\\\\_user` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '审核人',

#   `audit\\\\\\\_time` datetime(0) NULL DEFAULT NULL COMMENT '审核时间',

#   PRIMARY KEY (`id`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '策略组合上架审核表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of b1\_strategy\_audit

# -- ----------------------------

# INSERT INTO `b1\\\\\\\_strategy\\\\\\\_audit` VALUES (1, '996', '996', '996', '2025-07-07 19:12:53', '已上架', '996', '996', '2025-07-07 19:13:02');

# 

# -- ----------------------------

# -- Table structure for b2\_portfolio\_position

# -- ----------------------------

# DROP TABLE IF EXISTS `b2\\\\\\\_portfolio\\\\\\\_position`;

# CREATE TABLE `b2\\\\\\\_portfolio\\\\\\\_position`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键',

#   `portfolio\\\\\\\_id` bigint NOT NULL COMMENT '组合ID',

#   `fund\\\\\\\_code` varchar(30) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金名称',

#   `position\\\\\\\_ratio` decimal(8, 4) NOT NULL COMMENT '持仓比例',

#   `update\\\\\\\_time` datetime(0) NOT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '组合产品持仓表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of b2\_portfolio\_position

# -- ----------------------------

# INSERT INTO `b2\\\\\\\_portfolio\\\\\\\_position` VALUES (1, 1, '996', '996', 0.0112, '2025-07-07 19:17:11');

# 

# -- ----------------------------

# -- Table structure for b3\_trade\_instruction

# -- ----------------------------

# DROP TABLE IF EXISTS `b3\\\\\\\_trade\\\\\\\_instruction`;

# CREATE TABLE `b3\\\\\\\_trade\\\\\\\_instruction`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键',

#   `instruction\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '指令类型（买入/卖出）',

#   `fund\\\\\\\_code` varchar(30) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金名称',

#   `amount` decimal(16, 2) NOT NULL COMMENT '金额',

#   `trader` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '交易员',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '状态（待执行/已完成/已撤销）',

#   `create\\\\\\\_time` datetime(0) NOT NULL COMMENT '创建时间',

#   `execute\\\\\\\_time` datetime(0) NULL DEFAULT NULL COMMENT '执行时间',

#   `remark` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '备注',

#   PRIMARY KEY (`id`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '交易指令表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of b3\_trade\_instruction

# -- ----------------------------

# INSERT INTO `b3\\\\\\\_trade\\\\\\\_instruction` VALUES (1, '买入', '996', '996', 996.00, '996', '已完成', '2025-07-07 19:21:12', '2025-07-07 19:21:15', '996');

# 

# -- ----------------------------

# -- Table structure for b4\_error\_handle

# -- ----------------------------

# DROP TABLE IF EXISTS `b4\\\\\\\_error\\\\\\\_handle`;

# CREATE TABLE `b4\\\\\\\_error\\\\\\\_handle`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键',

#   `error\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '差错类型',

#   `description` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '差错描述',

#   `create\\\\\\\_time` datetime(0) NULL DEFAULT NULL COMMENT '创建时间',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '状态',

#   PRIMARY KEY (`id`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '差错处理表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of b4\_error\_handle

# -- ----------------------------

# INSERT INTO `b4\\\\\\\_error\\\\\\\_handle` VALUES (1, '996', '996', '2025-07-07 19:27:17', '待处理');

# 

# -- ----------------------------

# -- Table structure for b5\_quick\_action

# -- ----------------------------

# DROP TABLE IF EXISTS `b5\\\\\\\_quick\\\\\\\_action`;

# CREATE TABLE `b5\\\\\\\_quick\\\\\\\_action`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT COMMENT '主键',

#   `audit\\\\\\\_id` bigint NOT NULL COMMENT '关联审核ID',

#   `action\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '操作类型（下单/驳回）',

#   `operator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '操作人',

#   `action\\\\\\\_time` datetime(0) NOT NULL COMMENT '操作时间',

#   PRIMARY KEY (`id`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '一键操作表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of b5\_quick\_action

# -- ----------------------------

# INSERT INTO `b5\\\\\\\_quick\\\\\\\_action` VALUES (1, 996, '996', '996', '2025-07-07 19:33:24');

# 

# -- ----------------------------

# -- Table structure for backtest

# -- ----------------------------

# DROP TABLE IF EXISTS `backtest`;

# CREATE TABLE `backtest`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `backtest\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '回测代码',

#   `strategy\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略代码',

#   `strategy\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略名称',

#   `start\\\\\\\_date` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '回测开始日期',

#   `end\\\\\\\_date` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '回测结束日期',

#   `total\\\\\\\_return` double NULL DEFAULT NULL COMMENT '总收益率',

#   `annual\\\\\\\_return` double NULL DEFAULT NULL COMMENT '年化收益率',

#   `max\\\\\\\_drawdown` double NULL DEFAULT NULL COMMENT '最大回撤',

#   `sharpe\\\\\\\_ratio` double NULL DEFAULT NULL COMMENT '夏普比率',

#   `volatility` double NULL DEFAULT NULL COMMENT '波动率',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '运行中' COMMENT '回测状态',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建者',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `backtest\\\\\\\_code`(`backtest\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_backtest\\\\\\\_strategy`(`strategy\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_backtest\\\\\\\_status`(`status`) USING BTREE,

#   CONSTRAINT `backtest\\\\\\\_ibfk\\\\\\\_1` FOREIGN KEY (`strategy\\\\\\\_code`) REFERENCES `strategy` (`strategy\\\\\\\_code`) ON DELETE RESTRICT ON UPDATE RESTRICT

# ) ENGINE = InnoDB AUTO\_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '策略回测表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of backtest

# -- ----------------------------

# INSERT INTO `backtest` VALUES (1, 'BT001', 'ST001', '价值投资策略', '2023-01-01', '2023-12-31', 18.5, 18.5, -8.2, 1.85, 0.12, '已完成', '张三', '2024-01-20 10:00:00', '2024-01-20 10:00:00');

# INSERT INTO `backtest` VALUES (2, 'BT002', 'ST002', '动量策略', '2023-01-01', '2023-12-31', 22.3, 22.3, -12.5, 1.78, 0.15, '已完成', '李四', '2024-01-20 11:00:00', '2024-01-20 11:00:00');

# INSERT INTO `backtest` VALUES (3, 'BT003', 'ST003', '多因子策略', '2023-01-01', '2023-12-31', 25.8, 25.8, -10.1, 2.12, 0.13, '已完成', '王五', '2024-01-20 12:00:00', '2024-01-20 12:00:00');

# INSERT INTO `backtest` VALUES (4, 'BT004', 'ST001', '价值投资策略', '2024-01-01', '2024-12-31', 5.2, 6.8, -3.5, 1.45, 0.08, '运行中', '张三', '2024-01-21 09:00:00', '2024-01-21 09:00:00');

# INSERT INTO `backtest` VALUES (5, 'BT005', 'ST005', '低波动策略', '2023-06-01', '2023-12-31', 12.1, 24.2, -5.8, 2.05, 0.09, '已完成', '李四', '2024-01-21 14:00:00', '2024-01-21 14:00:00');

# 

# -- ----------------------------

# -- Table structure for derived\_factor

# -- ----------------------------

# DROP TABLE IF EXISTS `derived\\\\\\\_factor`;

# CREATE TABLE `derived\\\\\\\_factor`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `derived\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '衍生因子代码',

#   `derived\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '衍生因子名称',

#   `base\\\\\\\_factors` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基础因子（逗号分隔）',

#   `weights` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '权重（逗号分隔）',

#   `formula` varchar(500) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '计算公式',

#   `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '描述',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建者',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL DEFAULT 'pending' COMMENT '状态',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `derived\\\\\\\_code`(`derived\\\\\\\_code`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '衍生因子表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of derived\_factor

# -- ----------------------------

# INSERT INTO `derived\\\\\\\_factor` VALUES (1, 'DF001', '综合动量因子', 'F001,F005', '0.6,0.4', '0.6\*动量因子+0.4\*波动率因子', '结合动量和波动率的综合技术因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `derived\\\\\\\_factor` VALUES (2, 'DF002', '价值质量因子', 'F002,F003', '0.5,0.5', '0.5\*价值因子+0.5\*质量因子', '结合价值和质量的综合基本面因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `derived\\\\\\\_factor` VALUES (3, 'DF003', '多因子组合', 'F001,F002,F003,F004', '0.25,0.25,0.25,0.25', '0.25\*(动量+价值+质量+规模)', '经典多因子模型组合', 'admin', 'pending', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `derived\\\\\\\_factor` VALUES (4, 'F996', '996', 'F001', '0.6,0.4', '价格变化率计算', '基于价格动量的技术分析因子，用于捕捉价格趋势996', 'admin', 'pending', '2025-06-30 14:58:38', '2025-06-30 14:58:38');

# INSERT INTO `derived\\\\\\\_factor` VALUES (5, '555', '555', 'F008', '0.6,0.4', '资产负债率', '基于555财务杠杆的因子，用于分析公司财务结构', 'admin', 'pending', '2025-07-06 13:09:46', '2025-07-06 13:09:46');

# 

# -- ----------------------------

# -- Table structure for factor

# -- ----------------------------

# DROP TABLE IF EXISTS `factor`;

# CREATE TABLE `factor`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `factor\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '因子代码',

#   `factor\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '因子名称',

#   `factor\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '因子类型',

#   `factor\\\\\\\_category` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '因子分类',

#   `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '因子描述',

#   `data\\\\\\\_source` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '数据来源',

#   `calculation\\\\\\\_method` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '计算方法',

#   `tags` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '因子标签',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `factor\\\\\\\_code`(`factor\\\\\\\_code`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 9 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '因子表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of factor

# -- ----------------------------

# INSERT INTO `factor` VALUES (1, 'F001', '动量因子', '动量因子', '技术因子', '基于价格动量的技术分析因子，用于捕捉价格趋势996', 'Wind', '价格变化率计算', '动量,技术分析,趋势', '2024-01-01 10:00:00', '2025-06-30 14:51:35');

# INSERT INTO `factor` VALUES (2, 'F002', '价值因子', '价值因子', '基本面因子', '基于估值指标的基本面因子，用于识别被低估的股票', 'CSMAR', 'PE、PB等估值指标', '价值,基本面,估值', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor` VALUES (3, 'F003', '质量因子', '质量因子', '基本面因子', '基于财务质量的基本面因子，用于识别高质量公司', 'Wind', 'ROE、ROA等财务指标', '质量,基本面,财务', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor` VALUES (4, 'F004', '规模因子', '规模因子', '基本面因子', '基于公司规模的基本面因子，小盘股通常具有超额收益', 'CSMAR', '市值计算', '规模,基本面,市值', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor` VALUES (5, 'F005', '波动率因子', '风险因子', '技术因子', '基于价格波动率的风险因子，用于风险控制', 'Wind', '历史波动率计算', '波动率,风险,技术分析', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor` VALUES (6, 'F006', '流动性因子', '流动性因子', '技术因子', '基于交易流动性的技术因子，用于流动性分析', 'Wind', '换手率、成交量', '流动性,技术分析,交易', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor` VALUES (7, 'F007', '盈利因子', '盈利因子', '基本面因子', '基于盈利能力的因子，用于识别盈利能力强公司', 'Wind', '净利润增长率', '盈利,基本面,增长', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor` VALUES (8, 'F008', '杠杆因子', '杠杆因子', '基本面因子', '基于财务杠杆的因子，用于分析公司财务结构', 'Wind', '资产负债率', '杠杆,基本面,财务', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor` VALUES (9, '3333', '3333', '成长因子', '基本面因子', '3333', '东方财富', '3333', '3333', '2025-07-06 13:25:41', '2025-07-06 13:25:41');

# 

# -- ----------------------------

# -- Table structure for factor\_tree

# -- ----------------------------

# DROP TABLE IF EXISTS `factor\\\\\\\_tree`;

# CREATE TABLE `factor\\\\\\\_tree`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `tree\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '树代码',

#   `tree\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '树名称',

#   `tree\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '树类型',

#   `parent\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '父节点代码',

#   `node\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '节点代码',

#   `node\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '节点名称',

#   `node\\\\\\\_level` int NOT NULL COMMENT '节点层级',

#   `sort\\\\\\\_order` int NOT NULL COMMENT '排序',

#   `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '描述',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 8 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '因子树表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of factor\_tree

# -- ----------------------------

# INSERT INTO `factor\\\\\\\_tree` VALUES (1, 'TREE001', '因子分类树', '分类树', NULL, 'ROOT', '因子根节点', 0, 1, '因子分类的根节点', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor\\\\\\\_tree` VALUES (2, 'TREE001', '因子分类树', '分类树', 'ROOT', 'TECH', '技术因子', 1, 1, '技术分析类因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor\\\\\\\_tree` VALUES (3, 'TREE001', '因子分类树', '分类树', 'ROOT', 'FUND', '基本面因子', 1, 2, '基本面分析类因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor\\\\\\\_tree` VALUES (4, 'TREE001', '因子分类树', '分类树', 'ROOT', 'MACRO', '宏观因子', 1, 3, '宏观经济类因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor\\\\\\\_tree` VALUES (5, 'TREE001', '因子分类树', '分类树', 'TECH', 'MOMENTUM', '动量因子', 2, 1, '价格动量相关因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor\\\\\\\_tree` VALUES (6, 'TREE001', '因子分类树', '分类树', 'TECH', 'VOLATILITY', '波动率因子', 2, 2, '价格波动率相关因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor\\\\\\\_tree` VALUES (7, 'TREE001', '因子分类树', '分类树', 'FUND', 'VALUE', '价值因子', 2, 1, '估值相关因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `factor\\\\\\\_tree` VALUES (8, 'TREE001', '因子分类树', '分类树', 'FUND', 'QUALITY', '质量因子', 2, 2, '财务质量相关因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# 

# -- ----------------------------

# -- Table structure for fund

# -- ----------------------------

# DROP TABLE IF EXISTS `fund`;

# CREATE TABLE `fund`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `fund\\\\\\\_code` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NOT NULL COMMENT '基金名称',

#   `fund\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '基金类型',

#   `fund\\\\\\\_company` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '基金公司',

#   `fund\\\\\\\_manager` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '基金经理',

#   `net\\\\\\\_value` decimal(10, 4) NULL DEFAULT NULL COMMENT '净值',

#   `total\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '总收益率',

#   `risk\\\\\\\_level` int NULL DEFAULT NULL COMMENT '风险等级',

#   `tags` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL COMMENT '基金标签',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `fund\\\\\\\_code`(`fund\\\\\\\_code`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 10 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_0900\_ai\_ci COMMENT = '基金表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of fund

# -- ----------------------------

# INSERT INTO `fund` VALUES (1, '000001', '华夏成长混合', '混合型基金', '华夏基金管理有限公司', '张坤', 1.2345, 23.4500, 3, '成长型,混合型,股票投资', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund` VALUES (2, '000002', '易方达消费行业股票', '股票型基金', '易方达基金管理有限公司', '萧楠', 2.1567, 15.6700, 4, '消费行业,股票型,白酒股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund` VALUES (3, '000003', '嘉实增长混合', '混合型基金', '嘉实基金管理有限公司', '刘彦春', 1.8901, 18.9000, 3, '增长型,混合型,科技股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund` VALUES (4, '000004', '南方稳健成长混合', '混合型基金', '南方基金管理有限公司', '王宗合', 1.5678, 12.3400, 3, '稳健型,混合型,价值投资', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund` VALUES (5, '000005', '博时主题行业混合', '混合型基金', '博时基金管理有限公司', '谢治宇', 1.7890, 16.7800, 4, '主题投资,混合型,行业轮动', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund` VALUES (6, '000006', '华夏债券A', '债券型基金', '华夏基金管理有限公司', '张坤', 1.1234, 8.9000, 2, '债券型,低风险,固定收益', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund` VALUES (7, '000007', '易方达货币A', '货币型基金', '易方达基金管理有限公司', '萧楠', 1.0001, 2.5000, 1, '货币型,超低风险,现金管理', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund` VALUES (8, '000008', '嘉实沪深300ETF', '指数型基金', '嘉实基金管理有限公司', '刘彦春', 1.4567, 10.2300, 3, '指数型,ETF,沪深300', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund` VALUES (9, '000009', '南方中证500ETF', '指数型基金', '南方基金管理有限公司', '王宗合', 1.2345, 9.8700, 3, '指数型,ETF,中证500', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund` VALUES (10, '000010', '博时黄金ETF', '商品型基金', '博时基金管理有限公司', '谢治宇', 1.6789, 5.6700, 4, '商品型,ETF,黄金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# 

# -- ----------------------------

# -- Table structure for fund\_company

# -- ----------------------------

# DROP TABLE IF EXISTS `fund\\\\\\\_company`;

# CREATE TABLE `fund\\\\\\\_company`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `company\\\\\\\_code` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NOT NULL COMMENT '公司代码',

#   `company\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NOT NULL COMMENT '公司名称',

#   `company\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '公司类型',

#   `establishment\\\\\\\_date` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '成立日期',

#   `registered\\\\\\\_capital` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '注册资本',

#   `tags` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL COMMENT '公司标签',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `company\\\\\\\_code`(`company\\\\\\\_code`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_0900\_ai\_ci COMMENT = '基金公司表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of fund\_company

# -- ----------------------------

# INSERT INTO `fund\\\\\\\_company` VALUES (1, 'C001', '华夏基金管理有限公司', '公募基金', '1998-04-09', '2.38亿元', '大型基金公司,股票型基金,债券型基金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund\\\\\\\_company` VALUES (2, 'C002', '易方达基金管理有限公司', '公募基金', '2001-04-17', '1.2亿元', '大型基金公司,指数基金,混合型基金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund\\\\\\\_company` VALUES (3, 'C003', '嘉实基金管理有限公司', '公募基金', '1999-03-25', '1.5亿元', '大型基金公司,货币基金,债券型基金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund\\\\\\\_company` VALUES (4, 'C004', '南方基金管理有限公司', '公募基金', '1998-03-06', '3亿元', '大型基金公司,股票型基金,混合型基金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund\\\\\\\_company` VALUES (5, 'C005', '博时基金管理有限公司', '公募基金', '1998-07-13', '1亿元', '大型基金公司,指数基金,债券型基金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# 

# -- ----------------------------

# -- Table structure for fund\_manager

# -- ----------------------------

# DROP TABLE IF EXISTS `fund\\\\\\\_manager`;

# CREATE TABLE `fund\\\\\\\_manager`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `manager\\\\\\\_code` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NOT NULL COMMENT '经理代码',

#   `manager\\\\\\\_name` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NOT NULL COMMENT '经理姓名',

#   `company` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '所属公司',

#   `experience` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '从业经验',

#   `avg\\\\\\\_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '平均收益率',

#   `tags` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL COMMENT '经理标签',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `manager\\\\\\\_code`(`manager\\\\\\\_code`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_0900\_ai\_ci COMMENT = '基金经理表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of fund\_manager

# -- ----------------------------

# INSERT INTO `fund\\\\\\\_manager` VALUES (1, 'M001', '张坤', '易方达基金管理有限公司', '10年', 15.5000, '价值投资,蓝筹股,长期投资', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund\\\\\\\_manager` VALUES (2, 'M002', '刘彦春', '景顺长城基金管理有限公司', '12年', 18.2000, '成长投资,消费股,医药股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund\\\\\\\_manager` VALUES (3, 'M003', '萧楠', '易方达基金管理有限公司', '8年', 12.8000, '消费投资,白酒股,家电股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund\\\\\\\_manager` VALUES (4, 'M004', '王宗合', '鹏华基金管理有限公司', '9年', 14.6000, '价值投资,银行股,地产股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `fund\\\\\\\_manager` VALUES (5, 'M005', '谢治宇', '兴证全球基金管理有限公司', '11年', 16.3000, '均衡投资,科技股,消费股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# 

# -- ----------------------------

# -- Table structure for portfolio

# -- ----------------------------

# DROP TABLE IF EXISTS `portfolio`;

# CREATE TABLE `portfolio`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合名称',

#   `portfolio\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '组合类型',

#   `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '组合描述',

#   `risk\\\\\\\_level` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '风险等级',

#   `target\\\\\\\_return` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '目标收益率',

#   `max\\\\\\\_drawdown` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '最大回撤限制',

#   `strategies` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '使用的策略（逗号分隔）',

#   `asset\\\\\\\_allocation` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '资产配置（JSON格式）',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建者',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '草稿' COMMENT '状态',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 7 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '组合产品表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of portfolio

# -- ----------------------------

# INSERT INTO `portfolio` VALUES (1, 'PF001', '稳健增长组合', '混合型', '适合稳健型投资者的混合资产配置组合', '中风险', '8%', '15%', '价值投资,动量策略', '{\\"股票\\":60,\\"债券\\":30,\\"货币\\":10}', '张三', '活跃', '2024-01-15 10:00:00', '2024-01-15 10:00:00');

# INSERT INTO `portfolio` VALUES (2, 'PF002', '积极进取组合', '股票型', '适合积极型投资者的股票配置组合', '高风险', '12%', '25%', '成长投资,量化策略', '{\\"股票\\":80,\\"债券\\":15,\\"货币\\":5}', '李四', '活跃', '2024-01-16 14:30:00', '2024-01-16 14:30:00');

# INSERT INTO `portfolio` VALUES (3, 'PF003', '保守收益组合', '债券型', '适合保守型投资者的债券配置组合', '低风险', '5%', '8%', '久期管理,信用策略', '{\\"债券\\":70,\\"货币\\":25,\\"股票\\":5}', '王五', '活跃', '2024-01-17 09:15:00', '2024-01-17 09:15:00');

# INSERT INTO `portfolio` VALUES (4, 'PF004', '指数增强组合', '指数型', '基于宽基指数的增强配置组合', '中风险', '10%', '18%', '指数增强,因子策略', '{\\"股票\\":75,\\"债券\\":20,\\"货币\\":5}', '张三', '暂停', '2024-01-18 16:45:00', '2024-01-18 16:45:00');

# INSERT INTO `portfolio` VALUES (5, 'PF005', 'FOF精选组合', 'FOF型', '基金中的基金配置组合996', '中风险', '9%', '16%', '基金筛选,动态配置', '{\\"FOF\\":60,\\"股票\\":25,\\"债券\\":15}', '李四', '草稿', '2024-01-19 11:20:00', '2025-06-30 15:14:51');

# INSERT INTO `portfolio` VALUES (6, '007', '007', '007', '007', '低风险', '12%', '15%', '', '', NULL, '活跃', '2025-06-30 15:15:30', '2025-06-30 15:15:30');

# INSERT INTO `portfolio` VALUES (7, '996996', '996996', '996996', '996996', '低风险', '12%', '15%', '', '', 'admin', '活跃', '2025-06-30 15:20:46', '2025-06-30 15:20:46');

# 

# -- ----------------------------

# -- Table structure for portfolio\_analysis

# -- ----------------------------

# DROP TABLE IF EXISTS `portfolio\\\\\\\_analysis`;

# CREATE TABLE `portfolio\\\\\\\_analysis`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `analysis\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '分析代码',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '组合名称',

#   `analysis\\\\\\\_period` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '分析周期',

#   `total\\\\\\\_return` double NULL DEFAULT NULL COMMENT '总收益率',

#   `annual\\\\\\\_return` double NULL DEFAULT NULL COMMENT '年化收益率',

#   `max\\\\\\\_drawdown` double NULL DEFAULT NULL COMMENT '最大回撤',

#   `sharpe\\\\\\\_ratio` double NULL DEFAULT NULL COMMENT '夏普比率',

#   `volatility` double NULL DEFAULT NULL COMMENT '波动率',

#   `beta` double NULL DEFAULT NULL COMMENT '贝塔系数',

#   `alpha` double NULL DEFAULT NULL COMMENT '阿尔法系数',

#   `risk\\\\\\\_analysis` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '风险分析',

#   `performance\\\\\\\_analysis` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '绩效分析',

#   `recommendations` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '建议',

#   `analyst` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '分析师',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `analysis\\\\\\\_code`(`analysis\\\\\\\_code`) USING BTREE,

#   INDEX `portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   CONSTRAINT `portfolio\\\\\\\_analysis\\\\\\\_ibfk\\\\\\\_1` FOREIGN KEY (`portfolio\\\\\\\_code`) REFERENCES `portfolio` (`portfolio\\\\\\\_code`) ON DELETE RESTRICT ON UPDATE RESTRICT

# ) ENGINE = InnoDB AUTO\_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '组合分析表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of portfolio\_analysis

# -- ----------------------------

# INSERT INTO `portfolio\\\\\\\_analysis` VALUES (1, 'ANL001', 'PF001', '稳健增长组合', '1年', 8.5, 8.5, 12.3, 1.2, 15.2, 0.85, 2.1, '风险控制良好，回撤在合理范围内', '表现稳定，符合预期目标', '建议保持当前配置，关注市场变化', '张三', '2024-01-20 10:00:00', '2024-01-20 10:00:00');

# INSERT INTO `portfolio\\\\\\\_analysis` VALUES (2, 'ANL002', 'PF001', '稳健增长组合', '6个月', 4.2, 8.4, 8.7, 1.1, 14.8, 0.82, 1.8, '短期风险可控，波动率适中', '近期表现良好，超额收益稳定', '可适当增加权益配置', '张三', '2024-01-20 10:00:00', '2024-01-20 10:00:00');

# INSERT INTO `portfolio\\\\\\\_analysis` VALUES (3, 'ANL003', 'PF002', '积极进取组合', '1年', 15.8, 15.8, 22.1, 1.4, 25.6, 1.15, 3.2, '风险较高，但收益表现突出', '超额收益显著，夏普比率良好', '建议维持策略，注意风险控制', '李四', '2024-01-21 14:00:00', '2024-01-21 14:00:00');

# INSERT INTO `portfolio\\\\\\\_analysis` VALUES (4, 'ANL004', 'PF002', '积极进取组合', '3个月', 6.5, 26, 15.3, 1.3, 24.2, 1.12, 2.8, '短期波动较大，但收益可观', '季度表现优秀，动量效应明显', '可考虑增加防御性资产', '李四', '2024-01-21 14:00:00', '2024-01-21 14:00:00');

# INSERT INTO `portfolio\\\\\\\_analysis` VALUES (5, 'ANL005', 'PF003', '保守收益组合', '1年', 5.2, 5.2, 6.8, 0.9, 8.5, 0.45, 1.2, '风险极低，适合保守投资者', '收益稳定，符合预期', '建议保持配置，关注利率变化', '王五', '2024-01-22 09:00:00', '2024-01-22 09:00:00');

# INSERT INTO `portfolio\\\\\\\_analysis` VALUES (6, 'ANL006', 'PF004', '指数增强组合', '6个月', -2.1, -4.2, 18.5, 0.6, 20.1, 1.05, -1.5, '风险较高，超额收益为负', '表现不佳，需要策略调整', '建议重新评估策略有效性', '张三', '2024-01-23 16:00:00', '2024-01-23 16:00:00');

# 

# -- ----------------------------

# -- Table structure for portfolio\_config

# -- ----------------------------

# DROP TABLE IF EXISTS `portfolio\\\\\\\_config`;

# CREATE TABLE `portfolio\\\\\\\_config`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `config\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '配置代码',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '组合名称',

#   `asset\\\\\\\_class` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '资产类别',

#   `fund\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '基金名称',

#   `weight` double NULL DEFAULT NULL COMMENT '权重',

#   `rebalance\\\\\\\_rule` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '再平衡规则',

#   `stop\\\\\\\_loss\\\\\\\_rule` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '止损规则',

#   `take\\\\\\\_profit\\\\\\\_rule` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '止盈规则',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建者',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `config\\\\\\\_code`(`config\\\\\\\_code`) USING BTREE,

#   INDEX `portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   CONSTRAINT `portfolio\\\\\\\_config\\\\\\\_ibfk\\\\\\\_1` FOREIGN KEY (`portfolio\\\\\\\_code`) REFERENCES `portfolio` (`portfolio\\\\\\\_code`) ON DELETE RESTRICT ON UPDATE RESTRICT

# ) ENGINE = InnoDB AUTO\_INCREMENT = 12 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '组合配置表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of portfolio\_config

# -- ----------------------------

# INSERT INTO `portfolio\\\\\\\_config` VALUES (1, 'CFG001', 'PF001', '稳健增长组合', '股票', '000001', '华夏成长混合', 0.3, '季度再平衡', '单日跌幅超过5%', '累计收益超过15%', '张三', '2024-01-15 10:30:00', '2024-01-15 10:30:00');

# INSERT INTO `portfolio\\\\\\\_config` VALUES (2, 'CFG002', 'PF001', '稳健增长组合', '债券', '000002', '易方达债券A', 0.25, '季度再平衡', '单日跌幅超过2%', '累计收益超过8%', '张三', '2024-01-15 10:30:00', '2024-01-15 10:30:00');

# INSERT INTO `portfolio\\\\\\\_config` VALUES (3, 'CFG003', 'PF001', '稳健增长组合', '货币', '000003', '天弘余额宝', 0.1, '月度再平衡', '无', '无', '张三', '2024-01-15 10:30:00', '2024-01-15 10:30:00');

# INSERT INTO `portfolio\\\\\\\_config` VALUES (4, 'CFG004', 'PF002', '积极进取组合', '股票', '000004', '嘉实增长混合', 0.4, '月度再平衡', '单日跌幅超过7%', '累计收益超过20%', '李四', '2024-01-16 15:00:00', '2024-01-16 15:00:00');

# INSERT INTO `portfolio\\\\\\\_config` VALUES (5, 'CFG005', 'PF002', '积极进取组合', '股票', '000005', '富国天惠成长', 0.35, '月度再平衡', '单日跌幅超过7%', '累计收益超过20%', '李四', '2024-01-16 15:00:00', '2024-01-16 15:00:00');

# INSERT INTO `portfolio\\\\\\\_config` VALUES (6, 'CFG006', 'PF003', '保守收益组合', '债券', '000006', '工银瑞信债券', 0.45, '季度再平衡', '单日跌幅超过1%', '累计收益超过6%', '王五', '2024-01-17 09:45:00', '2024-01-17 09:45:00');

# INSERT INTO `portfolio\\\\\\\_config` VALUES (7, 'CFG007', 'PF003', '保守收益组合', '货币', '000007', '南方现金增利', 0.25, '月度再平衡', '无', '无', '王五', '2024-01-17 09:45:00', '2024-01-17 09:45:00');

# INSERT INTO `portfolio\\\\\\\_config` VALUES (10, '996', 'PF004', '996996', '996', '996', '996', 1, '996', '996', '996', NULL, '2025-06-30 15:42:15', '2025-06-30 15:42:15');

# INSERT INTO `portfolio\\\\\\\_config` VALUES (11, 'CFG1751349196800', '996996', '996996', '', '000007', '易方达货币A', 0, NULL, NULL, NULL, 'admin', '2025-07-01 13:53:16', '2025-07-01 13:53:16');

# INSERT INTO `portfolio\\\\\\\_config` VALUES (12, 'CFG1751509984612', '996996', '996996', '', '000002', '易方达消费行业股票', 0, NULL, NULL, NULL, 'admin', '2025-07-03 10:33:04', '2025-07-03 10:33:04');

# 

# -- ----------------------------

# -- Table structure for portfolio\_monitor

# -- ----------------------------

# DROP TABLE IF EXISTS `portfolio\\\\\\\_monitor`;

# CREATE TABLE `portfolio\\\\\\\_monitor`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `monitor\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '监控代码',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '组合名称',

#   `monitor\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '监控类型',

#   `alert\\\\\\\_condition` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '预警条件',

#   `alert\\\\\\\_threshold` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '预警阈值',

#   `alert\\\\\\\_action` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '预警动作',

#   `current\\\\\\\_value` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '当前值',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '活跃' COMMENT '监控状态',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建者',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `monitor\\\\\\\_code`(`monitor\\\\\\\_code`) USING BTREE,

#   INDEX `portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   CONSTRAINT `portfolio\\\\\\\_monitor\\\\\\\_ibfk\\\\\\\_1` FOREIGN KEY (`portfolio\\\\\\\_code`) REFERENCES `portfolio` (`portfolio\\\\\\\_code`) ON DELETE RESTRICT ON UPDATE RESTRICT

# ) ENGINE = InnoDB AUTO\_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '组合监控表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of portfolio\_monitor

# -- ----------------------------

# INSERT INTO `portfolio\\\\\\\_monitor` VALUES (1, 'MON001', 'PF001', '稳健增长组合', '风险监控', '最大回撤超过阈值', '15%', '自动减仓', '12.5%', '活跃', '张三', '2024-01-15 11:00:00', '2024-01-15 11:00:00');

# INSERT INTO `portfolio\\\\\\\_monitor` VALUES (2, 'MON002', 'PF001', '稳健增长组合', '绩效监控', '收益率低于目标', '6%', '发送预警邮件', '7.2%', '活跃', '张三', '2024-01-15 11:00:00', '2024-01-15 11:00:00');

# INSERT INTO `portfolio\\\\\\\_monitor` VALUES (3, 'MON003', 'PF002', '积极进取组合', '风险监控', '波动率超过阈值', '25%', '调整仓位', '22.3%', '活跃', '李四', '2024-01-16 15:30:00', '2024-01-16 15:30:00');

# INSERT INTO `portfolio\\\\\\\_monitor` VALUES (4, 'MON004', 'PF002', '积极进取组合', '再平衡监控', '权重偏离超过5%', '5%', '触发再平衡', '3.2%', '活跃', '李四', '2024-01-16 15:30:00', '2024-01-16 15:30:00');

# INSERT INTO `portfolio\\\\\\\_monitor` VALUES (5, 'MON005', 'PF003', '保守收益组合', '预警监控', '信用风险上升', 'BBB级', '降低久期', 'A级', '预警', '王五', '2024-01-17 10:00:00', '2024-01-17 10:00:00');

# INSERT INTO `portfolio\\\\\\\_monitor` VALUES (6, 'MON006', 'PF004', '指数增强组合', '绩效监控', '超额收益为负', '0%', '调整策略', '-1.2%', '暂停', '张三', '2024-01-18 17:00:00', '2024-01-18 17:00:00');

# 

# -- ----------------------------

# -- Table structure for strategy

# -- ----------------------------

# DROP TABLE IF EXISTS `strategy`;

# CREATE TABLE `strategy`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `strategy\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略代码',

#   `strategy\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略名称',

#   `strategy\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略类型',

#   `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '策略描述',

#   `factors` varchar(500) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '使用的因子（逗号分隔）',

#   `parameters` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '策略参数（JSON格式）',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建者',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '草稿' COMMENT '状态',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `strategy\\\\\\\_code`(`strategy\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_strategy\\\\\\\_code`(`strategy\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_strategy\\\\\\\_type`(`strategy\\\\\\\_type`) USING BTREE,

#   INDEX `idx\\\\\\\_strategy\\\\\\\_status`(`status`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '策略表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of strategy

# -- ----------------------------

# INSERT INTO `strategy` VALUES (1, 'ST001', '价值投资策略', '基本面分析', '基于公司基本面指标的价值投资策略，重点关注低估值、高ROE的优质公司', 'PE,ROE,PB,ROA', '{\\"pe\_threshold\\": 15, \\"roe\_threshold\\": 0.15, \\"pb\_threshold\\": 2.0}', '张三', '活跃', '2024-01-15 10:30:00', '2024-01-15 10:30:00');

# INSERT INTO `strategy` VALUES (2, 'ST002', '动量策略', '技术分析', '基于价格动量的技术分析策略，捕捉市场趋势', 'MA,MACD,RSI,KDJ', '{\\"ma\_period\\": 20, \\"momentum\_period\\": 10, \\"rsi\_threshold\\": 70}', '李四', '活跃', '2024-01-16 14:20:00', '2024-01-16 14:20:00');

# INSERT INTO `strategy` VALUES (3, 'ST003', '多因子策略', '量化策略', '综合多个因子的量化投资策略，平衡收益与风险', 'PE,PB,ROE,动量,波动率', '{\\"factor\_weights\\": {\\"pe\\": 0.2, \\"pb\\": 0.2, \\"roe\\": 0.2, \\"momentum\\": 0.2, \\"volatility\\": 0.2}}', '王五', '草稿', '2024-01-17 09:15:00', '2024-01-17 09:15:00');

# INSERT INTO `strategy` VALUES (4, 'ST004', '行业轮动策略', '混合策略', '基于行业景气度的轮动投资策略', '行业景气度,估值水平,资金流向', '{\\"rotation\_period\\": 30, \\"industry\_count\\": 5}', '张三', '暂停', '2024-01-18 16:45:00', '2024-01-18 16:45:00');

# INSERT INTO `strategy` VALUES (5, 'ST005', '低波动策略', '量化策略', '选择低波动率股票的投资策略，追求稳定收益996333', '波动率,夏普比率,最大回撤', '{\\"volatility\_threshold\\": 0.15, \\"sharpe\_threshold\\": 1.0}', '李四', '活跃', '2024-01-19 11:30:00', '2025-06-30 15:03:52');

# INSERT INTO `strategy` VALUES (6, '007', 'F007', '007', '007', '', '', 'admin', '活跃', '2025-06-30 15:07:15', '2025-06-30 15:07:33');

# 

# -- ----------------------------

# -- Table structure for strategy\_evaluation

# -- ----------------------------

# DROP TABLE IF EXISTS `strategy\\\\\\\_evaluation`;

# CREATE TABLE `strategy\\\\\\\_evaluation`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `evaluation\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '评估代码',

#   `strategy\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略代码',

#   `strategy\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略名称',

#   `evaluation\\\\\\\_period` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '评估周期',

#   `performance\\\\\\\_score` double NULL DEFAULT NULL COMMENT '绩效评分',

#   `risk\\\\\\\_score` double NULL DEFAULT NULL COMMENT '风险评分',

#   `stability\\\\\\\_score` double NULL DEFAULT NULL COMMENT '稳定性评分',

#   `overall\\\\\\\_score` double NULL DEFAULT NULL COMMENT '综合评分',

#   `evaluation\\\\\\\_result` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '评估结果',

#   `recommendations` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '建议',

#   `evaluator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '评估人',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `evaluation\\\\\\\_code`(`evaluation\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_evaluation\\\\\\\_strategy`(`strategy\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_evaluation\\\\\\\_period`(`evaluation\\\\\\\_period`) USING BTREE,

#   CONSTRAINT `strategy\\\\\\\_evaluation\\\\\\\_ibfk\\\\\\\_1` FOREIGN KEY (`strategy\\\\\\\_code`) REFERENCES `strategy` (`strategy\\\\\\\_code`) ON DELETE RESTRICT ON UPDATE RESTRICT

# ) ENGINE = InnoDB AUTO\_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '策略评估表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of strategy\_evaluation

# -- ----------------------------

# INSERT INTO `strategy\\\\\\\_evaluation` VALUES (1, 'EV001', 'ST001', '价值投资策略', '2023年度', 8.5, 7.8, 8.2, 8.2, '优秀', '策略表现稳定，建议继续执行并优化选股标准', '张三', '2024-01-23 10:00:00', '2024-01-23 10:00:00');

# INSERT INTO `strategy\\\\\\\_evaluation` VALUES (2, 'EV002', 'ST002', '动量策略', '2023年度', 7.8, 6.5, 7, 7.1, '良好', '收益表现良好，但风险控制需要加强', '李四', '2024-01-23 11:00:00', '2024-01-23 11:00:00');

# INSERT INTO `strategy\\\\\\\_evaluation` VALUES (3, 'EV003', 'ST003', '多因子策略', '2023年度', 9.2, 8.5, 8.8, 8.8, '优秀', '综合表现优异，建议扩大应用范围', '王五', '2024-01-23 12:00:00', '2024-01-23 12:00:00');

# INSERT INTO `strategy\\\\\\\_evaluation` VALUES (4, 'EV004', 'ST001', '价值投资策略', '2023年第四季度', 7.5, 8, 7.8, 7.8, '良好', '季度表现稳定，建议关注市场环境变化', '张三', '2024-01-23 13:00:00', '2024-01-23 13:00:00');

# INSERT INTO `strategy\\\\\\\_evaluation` VALUES (5, 'EV005', 'ST005', '低波动策略', '2023年下半年', 8.8, 9, 8.5, 8.8, '优秀', '风险控制出色，建议作为核心策略之一', '李四', '2024-01-23 14:00:00', '2024-01-23 14:00:00');

# 

# -- ----------------------------

# -- Table structure for strategy\_monitor

# -- ----------------------------

# DROP TABLE IF EXISTS `strategy\\\\\\\_monitor`;

# CREATE TABLE `strategy\\\\\\\_monitor`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `monitor\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '监控代码',

#   `strategy\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略代码',

#   `strategy\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '策略名称',

#   `monitor\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '监控类型',

#   `alert\\\\\\\_condition` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '预警条件',

#   `alert\\\\\\\_threshold` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '预警阈值',

#   `alert\\\\\\\_action` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '预警动作',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT '活跃' COMMENT '监控状态',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建者',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `monitor\\\\\\\_code`(`monitor\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_monitor\\\\\\\_strategy`(`strategy\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_monitor\\\\\\\_type`(`monitor\\\\\\\_type`) USING BTREE,

#   CONSTRAINT `strategy\\\\\\\_monitor\\\\\\\_ibfk\\\\\\\_1` FOREIGN KEY (`strategy\\\\\\\_code`) REFERENCES `strategy` (`strategy\\\\\\\_code`) ON DELETE RESTRICT ON UPDATE RESTRICT

# ) ENGINE = InnoDB AUTO\_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '策略监控表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of strategy\_monitor

# -- ----------------------------

# INSERT INTO `strategy\\\\\\\_monitor` VALUES (1, 'MT001', 'ST001', '价值投资策略', '绩效监控', '收益率低于阈值', '5%', '发送邮件通知', '活跃', '张三', '2024-01-22 10:00:00', '2024-01-22 10:00:00');

# INSERT INTO `strategy\\\\\\\_monitor` VALUES (2, 'MT002', 'ST002', '动量策略', '风险监控', '最大回撤超过阈值', '15%', '暂停策略执行', '活跃', '李四', '2024-01-22 11:00:00', '2024-01-22 11:00:00');

# INSERT INTO `strategy\\\\\\\_monitor` VALUES (3, 'MT003', 'ST003', '多因子策略', '绩效监控', '夏普比率低于阈值', '1.5', '调整因子权重', '活跃', '王五', '2024-01-22 12:00:00', '2024-01-22 12:00:00');

# INSERT INTO `strategy\\\\\\\_monitor` VALUES (4, 'MT004', 'ST001', '价值投资策略', '仓位监控', '持仓集中度过高', '30%', '分散投资', '预警', '张三', '2024-01-22 13:00:00', '2024-01-22 13:00:00');

# INSERT INTO `strategy\\\\\\\_monitor` VALUES (5, 'MT005', 'ST005', '低波动策略', '风险监控', '波动率超过阈值', '12%', '降低仓位', '暂停', '李四', '2024-01-22 14:00:00', '2024-01-22 14:00:00');

# 

# -- ----------------------------

# -- Table structure for style\_factor

# -- ----------------------------

# DROP TABLE IF EXISTS `style\\\\\\\_factor`;

# CREATE TABLE `style\\\\\\\_factor`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `style\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '风格因子代码',

#   `style\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '风格因子名称',

#   `style\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '风格类型',

#   `base\\\\\\\_factors` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基础因子（逗号分隔）',

#   `weights` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '权重（逗号分隔）',

#   `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '描述',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建者',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL DEFAULT 'pending' COMMENT '状态',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `style\\\\\\\_code`(`style\\\\\\\_code`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 4 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '风格投资因子表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of style\_factor

# -- ----------------------------

# INSERT INTO `style\\\\\\\_factor` VALUES (1, 'SF001', '成长风格因子', '成长风格', 'F007,F003', '0.6,0.4', '专注于成长型公司的风格因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `style\\\\\\\_factor` VALUES (2, 'SF002', '价值风格因子', '价值风格', 'F002,F004', '0.7,0.3', '专注于价值型公司的风格因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `style\\\\\\\_factor` VALUES (3, 'SF003', '平衡风格因子', '平衡风格', 'F002,F003,F007', '0.4,0.3,0.3', '平衡价值、质量和成长的风格因子', 'admin', 'pending', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# INSERT INTO `style\\\\\\\_factor` VALUES (4, 'SF004', '动量风格因子', '动量风格', 'F001,F006', '0.8,0.2', '专注于动量交易的风格因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

# 

# -- ----------------------------

# -- Table structure for trade\_analysis

# -- ----------------------------

# DROP TABLE IF EXISTS `trade\\\\\\\_analysis`;

# CREATE TABLE `trade\\\\\\\_analysis`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `analysis\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '分析代码',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合名称',

#   `analysis\\\\\\\_period` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '分析周期',

#   `total\\\\\\\_trades` int NOT NULL DEFAULT 0 COMMENT '总交易次数',

#   `total\\\\\\\_volume` double NOT NULL DEFAULT 0 COMMENT '总交易量',

#   `total\\\\\\\_amount` double NOT NULL DEFAULT 0 COMMENT '总交易金额',

#   `avg\\\\\\\_trade\\\\\\\_size` double NULL DEFAULT NULL COMMENT '平均交易规模',

#   `win\\\\\\\_rate` double NULL DEFAULT NULL COMMENT '胜率',

#   `profit\\\\\\\_loss` double NULL DEFAULT NULL COMMENT '盈亏',

#   `slippage` double NULL DEFAULT NULL COMMENT '滑点',

#   `execution\\\\\\\_quality` double NULL DEFAULT NULL COMMENT '执行质量',

#   `performance\\\\\\\_analysis` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '绩效分析',

#   `risk\\\\\\\_analysis` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '风险分析',

#   `recommendations` text CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL COMMENT '建议',

#   `analyst` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '分析师',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `analysis\\\\\\\_code`(`analysis\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_analysis\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_analysis\\\\\\\_period`(`analysis\\\\\\\_period`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_analysis\\\\\\\_analyst`(`analyst`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_analysis\\\\\\\_create\\\\\\\_time`(`create\\\\\\\_time`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '交易分析表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of trade\_analysis

# -- ----------------------------

# INSERT INTO `trade\\\\\\\_analysis` VALUES (1, 'ANA20241201001', 'PORT001', '稳健成长组合', '月度', 25, 2500000, 2500000, 100000, 68, 150000, 0.15, 85.5, '组合表现稳健，超额收益明显，主要受益于选股策略的有效性', '风险控制良好，最大回撤控制在合理范围内', '建议继续持有核心仓位，适当增加防御性配置', '分析师A', '2024-12-01 16:00:00', '2024-12-01 16:00:00');

# INSERT INTO `trade\\\\\\\_analysis` VALUES (2, 'ANA20241201002', 'PORT002', '积极进取组合', '月度', 35, 3500000, 3500000, 100000, 62, 200000, 0.25, 78, '组合收益较高但波动较大，适合风险承受能力较强的投资者', '风险水平较高，需要密切关注市场变化', '建议适当降低仓位，增加风险对冲工具', '分析师B', '2024-12-01 16:30:00', '2024-12-01 16:30:00');

# INSERT INTO `trade\\\\\\\_analysis` VALUES (3, 'ANA20241201003', 'PORT003', '价值投资组合', '月度', 20, 2000000, 2000000, 100000, 75, 120000, 0.1, 90, '价值投资策略表现优异，长期收益稳定', '风险控制优秀，回撤控制良好', '建议保持当前策略，继续寻找价值投资机会', '分析师C', '2024-12-01 17:00:00', '2024-12-01 17:00:00');

# INSERT INTO `trade\\\\\\\_analysis` VALUES (4, 'ANA20241201004', 'PORT001', '稳健成长组合', '季度', 75, 7500000, 7500000, 100000, 70, 450000, 0.18, 82, '季度表现符合预期，策略执行到位', '季度风险指标在合理范围内', '建议继续执行现有策略，关注市场变化', '分析师A', '2024-12-01 17:30:00', '2024-12-01 17:30:00');

# INSERT INTO `trade\\\\\\\_analysis` VALUES (5, 'ANA20241201005', 'PORT002', '积极进取组合', '季度', 105, 10500000, 10500000, 100000, 65, 600000, 0.3, 75, '季度收益较高但波动较大，需要优化风险控制', '季度风险水平偏高，需要调整', '建议优化仓位配置，加强风险控制', '分析师B', '2024-12-01 18:00:00', '2024-12-01 18:00:00');

# 

# -- ----------------------------

# -- Table structure for trade\_execution

# -- ----------------------------

# DROP TABLE IF EXISTS `trade\\\\\\\_execution`;

# CREATE TABLE `trade\\\\\\\_execution`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `execution\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '执行代码',

#   `order\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '订单代码',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合名称',

#   `fund\\\\\\\_code` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金名称',

#   `execution\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '执行类型',

#   `execution\\\\\\\_amount` double NULL DEFAULT NULL COMMENT '执行金额',

#   `execution\\\\\\\_quantity` double NULL DEFAULT NULL COMMENT '执行数量',

#   `execution\\\\\\\_price` double NULL DEFAULT NULL COMMENT '执行价格',

#   `execution\\\\\\\_status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL DEFAULT '待执行' COMMENT '执行状态',

#   `execution\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '执行时间',

#   `broker` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '券商',

#   `account\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '账户代码',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建者',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `execution\\\\\\\_code`(`execution\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_execution\\\\\\\_order\\\\\\\_code`(`order\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_execution\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_execution\\\\\\\_status`(`execution\\\\\\\_status`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_execution\\\\\\\_create\\\\\\\_time`(`create\\\\\\\_time`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '交易执行表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of trade\_execution

# -- ----------------------------

# INSERT INTO `trade\\\\\\\_execution` VALUES (1, 'EXE20241201001', 'ORD20241201001', 'PORT001', '稳健成长组合', '000001', '华夏成长混合', '市价单', 100000, 50000, 2, '已执行', '2024-12-01 09:35:00', '中信证券', 'ACC001', '张三', '2024-12-01 09:35:00', '2024-12-01 09:35:00');

# INSERT INTO `trade\\\\\\\_execution` VALUES (2, 'EXE20241201002', 'ORD20241201003', 'PORT001', '稳健成长组合', '000003', '嘉实增长混合', '限价单', 80000, 40000, 2, '已执行', '2024-12-01 14:25:00', '中信证券', 'ACC001', '张三', '2024-12-01 14:25:00', '2024-12-01 14:25:00');

# INSERT INTO `trade\\\\\\\_execution` VALUES (3, 'EXE20241201003', 'ORD20241201002', 'PORT002', '积极进取组合', '000002', '易方达消费行业', '市价单', 150000, 30000, 5, '待执行', NULL, '华泰证券', 'ACC002', '李四', '2024-12-01 10:20:00', '2024-12-01 10:20:00');

# INSERT INTO `trade\\\\\\\_execution` VALUES (4, 'EXE20241201004', 'ORD20241201004', 'PORT003', '价值投资组合', '000004', '富国天惠成长', '止损单', 200000, 100000, 2, '已取消', NULL, '国泰君安', 'ACC003', '王五', '2024-12-01 15:50:00', '2024-12-01 15:50:00');

# INSERT INTO `trade\\\\\\\_execution` VALUES (5, 'EXE20241201005', 'ORD20241201005', 'PORT002', '积极进取组合', '000005', '博时主题行业', '市价单', 120000, 60000, 2, '执行失败', NULL, '华泰证券', 'ACC002', '李四', '2024-12-01 16:35:00', '2024-12-01 16:35:00');

# 

# -- ----------------------------

# -- Table structure for trade\_monitor

# -- ----------------------------

# DROP TABLE IF EXISTS `trade\\\\\\\_monitor`;

# CREATE TABLE `trade\\\\\\\_monitor`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `monitor\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '监控代码',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合名称',

#   `monitor\\\\\\\_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '监控类型',

#   `monitor\\\\\\\_target` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '监控目标',

#   `alert\\\\\\\_condition` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '预警条件',

#   `alert\\\\\\\_threshold` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '预警阈值',

#   `alert\\\\\\\_action` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '预警动作',

#   `current\\\\\\\_value` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '当前值',

#   `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL DEFAULT '启用' COMMENT '监控状态',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建者',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `monitor\\\\\\\_code`(`monitor\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_monitor\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_monitor\\\\\\\_type`(`monitor\\\\\\\_type`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_monitor\\\\\\\_status`(`status`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_monitor\\\\\\\_create\\\\\\\_time`(`create\\\\\\\_time`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '交易监控表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of trade\_monitor

# -- ----------------------------

# INSERT INTO `trade\\\\\\\_monitor` VALUES (1, 'MON20241201001', 'PORT001', '稳健成长组合', '价格监控', '华夏成长混合', '价格下跌超过阈值', '5%', '发送预警邮件', '2.10', '启用', '张三', '2024-12-01 08:00:00', '2024-12-01 08:00:00');

# INSERT INTO `trade\\\\\\\_monitor` VALUES (2, 'MON20241201002', 'PORT002', '积极进取组合', '波动率监控', '易方达消费行业', '波动率超过阈值', '15%', '暂停交易', '12%', '启用', '李四', '2024-12-01 08:30:00', '2024-12-01 08:30:00');

# INSERT INTO `trade\\\\\\\_monitor` VALUES (3, 'MON20241201003', 'PORT003', '价值投资组合', '流动性监控', '富国天惠成长', '流动性不足', '100万', '调整持仓', '150万', '启用', '王五', '2024-12-01 09:00:00', '2024-12-01 09:00:00');

# INSERT INTO `trade\\\\\\\_monitor` VALUES (4, 'MON20241201004', 'PORT001', '稳健成长组合', '风险监控', '组合整体风险', 'VaR超过阈值', '3%', '减仓操作', '2.5%', '启用', '张三', '2024-12-01 09:15:00', '2024-12-01 09:15:00');

# INSERT INTO `trade\\\\\\\_monitor` VALUES (5, 'MON20241201005', 'PORT002', '积极进取组合', '收益监控', '组合收益率', '收益率低于阈值', '-5%', '重新评估', '-2%', '停用', '李四', '2024-12-01 10:00:00', '2024-12-01 10:00:00');

# 

# -- ----------------------------

# -- Table structure for trade\_order

# -- ----------------------------

# DROP TABLE IF EXISTS `trade\\\\\\\_order`;

# CREATE TABLE `trade\\\\\\\_order`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `order\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '订单代码',

#   `portfolio\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合代码',

#   `portfolio\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '组合名称',

#   `fund\\\\\\\_code` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金代码',

#   `fund\\\\\\\_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '基金名称',

#   `order\\\\\\\_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '订单类型（买入/卖出）',

#   `order\\\\\\\_amount` double NULL DEFAULT NULL COMMENT '订单金额',

#   `order\\\\\\\_quantity` double NULL DEFAULT NULL COMMENT '订单数量',

#   `order\\\\\\\_price` double NULL DEFAULT NULL COMMENT '订单价格',

#   `order\\\\\\\_status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL DEFAULT '待执行' COMMENT '订单状态',

#   `order\\\\\\\_reason` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '订单原因',

#   `strategy\\\\\\\_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NULL DEFAULT NULL COMMENT '策略代码',

#   `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建者',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_unicode\_ci NOT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `order\\\\\\\_code`(`order\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_order\\\\\\\_portfolio\\\\\\\_code`(`portfolio\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_order\\\\\\\_fund\\\\\\\_code`(`fund\\\\\\\_code`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_order\\\\\\\_status`(`order\\\\\\\_status`) USING BTREE,

#   INDEX `idx\\\\\\\_trade\\\\\\\_order\\\\\\\_create\\\\\\\_time`(`create\\\\\\\_time`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_unicode\_ci COMMENT = '交易订单表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of trade\_order

# -- ----------------------------

# INSERT INTO `trade\\\\\\\_order` VALUES (1, 'ORD20241201001', 'PORT001', '稳健成长组合', '000001', '华夏成长混合', '买入', 100000, 50000, 2, '已执行', '策略调仓', 'STR001', '张三', '2024-12-01 09:30:00', '2024-12-01 09:30:00');

# INSERT INTO `trade\\\\\\\_order` VALUES (2, 'ORD20241201002', 'PORT002', '积极进取组合', '000002', '易方达消费行业', '买入', 150000, 30000, 5, '待执行', '新增配置', 'STR002', '李四', '2024-12-01 10:15:00', '2024-12-01 10:15:00');

# INSERT INTO `trade\\\\\\\_order` VALUES (3, 'ORD20241201003', 'PORT001', '稳健成长组合', '000003', '嘉实增长混合', '卖出', 80000, 40000, 2, '已执行', '止盈操作', 'STR001', '张三', '2024-12-01 14:20:00', '2024-12-01 14:20:00');

# INSERT INTO `trade\\\\\\\_order` VALUES (5, 'ORD20241201005', 'PORT002', '积极进取组合', '000005', '博时主题行业', '买入', 120000, 60000, 2, '执行失败', '资金不足996', 'STR002', '李四', '2024-12-01 16:30:00', '2025-06-30 15:57:03');

# INSERT INTO `trade\\\\\\\_order` VALUES (6, '996', '996', '996', '996', '996', '买入', 996, 996, 996, '待执行', '996', '996', 'admin', '2025-06-30 16:00:02', '2025-06-30 16:00:02');

# 

# -- ----------------------------

# -- Table structure for user

# -- ----------------------------

# DROP TABLE IF EXISTS `user`;

# CREATE TABLE `user`  (

#   `id` bigint NOT NULL AUTO\_INCREMENT,

#   `username` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NOT NULL COMMENT '用户名',

#   `password` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NOT NULL COMMENT '密码',

#   `email` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '邮箱',

#   `phone` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '手机号',

#   `real\\\\\\\_name` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '真实姓名',

#   `create\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '创建时间',

#   `update\\\\\\\_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4\_0900\_ai\_ci NULL DEFAULT NULL COMMENT '更新时间',

#   PRIMARY KEY (`id`) USING BTREE,

#   UNIQUE INDEX `username`(`username`) USING BTREE

# ) ENGINE = InnoDB AUTO\_INCREMENT = 3 CHARACTER SET = utf8mb4 COLLATE = utf8mb4\_0900\_ai\_ci COMMENT = '用户表' ROW\_FORMAT = Dynamic;

# 

# -- ----------------------------

# -- Records of user

# -- ----------------------------

# INSERT INTO `user` VALUES (1, 'admin', '123456', 'admin@example.com', '13800138000', '管理员', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `user` VALUES (2, 'user1', '123456', 'user1@example.com', '13800138001', '张三', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# INSERT INTO `user` VALUES (3, 'user2', '123456', 'user2@example.com', '13800138002', '李四', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

# 

# SET FOREIGN\_KEY\_CHECKS = 1;

