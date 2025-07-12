/*
 Navicat MySQL Data Transfer

 Source Server         : java
 Source Server Type    : MySQL
 Source Server Version : 80029
 Source Host           : localhost:3306
 Source Schema         : advisor

 Target Server Type    : MySQL
 Target Server Version : 80029
 File Encoding         : 65001

 Date: 03/07/2025 15:15:03
*/

SET NAMES utf8mb4;
SET FOREIGN_KEY_CHECKS = 0;

-- ----------------------------
-- Table structure for backtest
-- ----------------------------
DROP TABLE IF EXISTS `backtest`;
CREATE TABLE `backtest`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `backtest_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '回测代码',
  `strategy_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略代码',
  `strategy_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略名称',
  `start_date` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '回测开始日期',
  `end_date` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '回测结束日期',
  `total_return` double NULL DEFAULT NULL COMMENT '总收益率',
  `annual_return` double NULL DEFAULT NULL COMMENT '年化收益率',
  `max_drawdown` double NULL DEFAULT NULL COMMENT '最大回撤',
  `sharpe_ratio` double NULL DEFAULT NULL COMMENT '夏普比率',
  `volatility` double NULL DEFAULT NULL COMMENT '波动率',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '运行中' COMMENT '回测状态',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建者',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `backtest_code`(`backtest_code`) USING BTREE,
  INDEX `idx_backtest_strategy`(`strategy_code`) USING BTREE,
  INDEX `idx_backtest_status`(`status`) USING BTREE,
  CONSTRAINT `backtest_ibfk_1` FOREIGN KEY (`strategy_code`) REFERENCES `strategy` (`strategy_code`) ON DELETE RESTRICT ON UPDATE RESTRICT
) ENGINE = InnoDB AUTO_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '策略回测表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of backtest
-- ----------------------------
INSERT INTO `backtest` VALUES (1, 'BT001', 'ST001', '价值投资策略', '2023-01-01', '2023-12-31', 18.5, 18.5, -8.2, 1.85, 0.12, '已完成', '张三', '2024-01-20 10:00:00', '2024-01-20 10:00:00');
INSERT INTO `backtest` VALUES (2, 'BT002', 'ST002', '动量策略', '2023-01-01', '2023-12-31', 22.3, 22.3, -12.5, 1.78, 0.15, '已完成', '李四', '2024-01-20 11:00:00', '2024-01-20 11:00:00');
INSERT INTO `backtest` VALUES (3, 'BT003', 'ST003', '多因子策略', '2023-01-01', '2023-12-31', 25.8, 25.8, -10.1, 2.12, 0.13, '已完成', '王五', '2024-01-20 12:00:00', '2024-01-20 12:00:00');
INSERT INTO `backtest` VALUES (4, 'BT004', 'ST001', '价值投资策略', '2024-01-01', '2024-12-31', 5.2, 6.8, -3.5, 1.45, 0.08, '运行中', '张三', '2024-01-21 09:00:00', '2024-01-21 09:00:00');
INSERT INTO `backtest` VALUES (5, 'BT005', 'ST005', '低波动策略', '2023-06-01', '2023-12-31', 12.1, 24.2, -5.8, 2.05, 0.09, '已完成', '李四', '2024-01-21 14:00:00', '2024-01-21 14:00:00');

-- ----------------------------
-- Table structure for derived_factor
-- ----------------------------
DROP TABLE IF EXISTS `derived_factor`;
CREATE TABLE `derived_factor`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `derived_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '衍生因子代码',
  `derived_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '衍生因子名称',
  `base_factors` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基础因子（逗号分隔）',
  `weights` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '权重（逗号分隔）',
  `formula` varchar(500) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '计算公式',
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '描述',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建者',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'pending' COMMENT '状态',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `derived_code`(`derived_code`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 4 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '衍生因子表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of derived_factor
-- ----------------------------
INSERT INTO `derived_factor` VALUES (1, 'DF001', '综合动量因子', 'F001,F005', '0.6,0.4', '0.6*动量因子+0.4*波动率因子', '结合动量和波动率的综合技术因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `derived_factor` VALUES (2, 'DF002', '价值质量因子', 'F002,F003', '0.5,0.5', '0.5*价值因子+0.5*质量因子', '结合价值和质量的综合基本面因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `derived_factor` VALUES (3, 'DF003', '多因子组合', 'F001,F002,F003,F004', '0.25,0.25,0.25,0.25', '0.25*(动量+价值+质量+规模)', '经典多因子模型组合', 'admin', 'pending', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `derived_factor` VALUES (4, 'F996', '996', 'F001', '0.6,0.4', '价格变化率计算', '基于价格动量的技术分析因子，用于捕捉价格趋势996', 'admin', 'pending', '2025-06-30 14:58:38', '2025-06-30 14:58:38');

-- ----------------------------
-- Table structure for factor
-- ----------------------------
DROP TABLE IF EXISTS `factor`;
CREATE TABLE `factor`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `factor_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '因子代码',
  `factor_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '因子名称',
  `factor_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '因子类型',
  `factor_category` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '因子分类',
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '因子描述',
  `data_source` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '数据来源',
  `calculation_method` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '计算方法',
  `tags` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '因子标签',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `factor_code`(`factor_code`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 9 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '因子表' ROW_FORMAT = Dynamic;

