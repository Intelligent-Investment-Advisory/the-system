SET NAMES utf8mb4;
SET FOREIGN_KEY_CHECKS = 0;

-- ----------------------------
-- Table structure for a1_fof_config
-- ----------------------------
DROP TABLE IF EXISTS `a1_fof_config`;
CREATE TABLE `a1_fof_config`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `fund_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金名称',
  `weight` decimal(10, 4) NOT NULL COMMENT '权重',
  `asset_class` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '资产类别',
  `rebalance_frequency` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '再平衡频率',
  `stop_loss` decimal(10, 4) NULL DEFAULT NULL COMMENT '止损线',
  `take_profit` decimal(10, 4) NULL DEFAULT NULL COMMENT '止盈线',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '活跃' COMMENT '状态：活跃、暂停',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  `updated_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) ON UPDATE CURRENT_TIMESTAMP(0) COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_fund_code`(`fund_code`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE
) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = 'FOF组合配置表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a1_fof_config
-- ----------------------------

-- ----------------------------
-- Table structure for a1_fof_monitor
-- ----------------------------
DROP TABLE IF EXISTS `a1_fof_monitor`;
CREATE TABLE `a1_fof_monitor`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `monitor_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '监控类型：风险监控、绩效监控、再平衡监控',
  `monitor_date` date NOT NULL COMMENT '监控日期',
  `total_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '总收益率',
  `annual_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '年化收益率',
  `max_drawdown` decimal(10, 4) NULL DEFAULT NULL COMMENT '最大回撤',
  `sharpe_ratio` decimal(10, 4) NULL DEFAULT NULL COMMENT '夏普比率',
  `volatility` decimal(10, 4) NULL DEFAULT NULL COMMENT '波动率',
  `beta` decimal(10, 4) NULL DEFAULT NULL COMMENT '贝塔系数',
  `alpha` decimal(10, 4) NULL DEFAULT NULL COMMENT '阿尔法系数',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '正常' COMMENT '状态：正常、预警、异常',
  `alert_message` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '预警信息',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_monitor_date`(`monitor_date`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE
) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = 'FOF组合监控表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a1_fof_monitor
-- ----------------------------

-- ----------------------------
-- Table structure for a1_fof_portfolio
-- ----------------------------
DROP TABLE IF EXISTS `a1_fof_portfolio`;
CREATE TABLE `a1_fof_portfolio`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合名称',
  `portfolio_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合类型：FOF',
  `risk_level` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '风险等级：低风险、中风险、高风险',
  `target_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '目标收益率',
  `max_drawdown` decimal(10, 4) NULL DEFAULT NULL COMMENT '最大回撤',
  `strategy_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '策略代码',
  `asset_allocation` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '资产配置JSON',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '草稿' COMMENT '状态：草稿、活跃、暂停',
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '组合描述',
  `created_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建人',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  `updated_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新人',
  `updated_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) ON UPDATE CURRENT_TIMESTAMP(0) COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE,
  INDEX `idx_created_time`(`created_time`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 2 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = 'FOF组合表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a1_fof_portfolio
-- ----------------------------
INSERT INTO `a1_fof_portfolio` VALUES (2, '444', '444', 'FOF', '低风险', 44.0000, 44.0000, '444', '44', '草稿', '44', '44', '2025-07-06 20:01:28', NULL, '2025-07-06 20:01:28');

-- ----------------------------
-- Table structure for a2_index_config
-- ----------------------------
DROP TABLE IF EXISTS `a2_index_config`;
CREATE TABLE `a2_index_config`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `fund_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金名称',
  `weight` decimal(10, 4) NOT NULL COMMENT '权重',
  `asset_class` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '资产类别',
  `rebalance_frequency` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '再平衡频率',
  `tracking_error_limit` decimal(10, 4) NULL DEFAULT NULL COMMENT '跟踪误差限制',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '活跃' COMMENT '状态：活跃、暂停',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  `updated_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) ON UPDATE CURRENT_TIMESTAMP(0) COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_fund_code`(`fund_code`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE
) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '指数组合配置表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a2_index_config
-- ----------------------------

-- ----------------------------
-- Table structure for a2_index_monitor
-- ----------------------------
DROP TABLE IF EXISTS `a2_index_monitor`;
CREATE TABLE `a2_index_monitor`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `monitor_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '监控类型：跟踪误差监控、绩效监控、再平衡监控',
  `monitor_date` date NOT NULL COMMENT '监控日期',
  `total_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '总收益率',
  `index_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '指数收益率',
  `tracking_error` decimal(10, 4) NULL DEFAULT NULL COMMENT '跟踪误差',
  `information_ratio` decimal(10, 4) NULL DEFAULT NULL COMMENT '信息比率',
  `beta` decimal(10, 4) NULL DEFAULT NULL COMMENT '贝塔系数',
  `alpha` decimal(10, 4) NULL DEFAULT NULL COMMENT '阿尔法系数',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '正常' COMMENT '状态：正常、预警、异常',
  `alert_message` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '预警信息',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_monitor_date`(`monitor_date`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE
) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '指数组合监控表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a2_index_monitor
-- ----------------------------

-- ----------------------------
-- Table structure for a2_index_portfolio
-- ----------------------------
DROP TABLE IF EXISTS `a2_index_portfolio`;
CREATE TABLE `a2_index_portfolio`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合名称',
  `portfolio_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合类型：指数型',
  `index_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '指数代码',
  `index_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '指数名称',
  `risk_level` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '风险等级：低风险、中风险、高风险',
  `target_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '目标收益率',
  `tracking_error` decimal(10, 4) NULL DEFAULT NULL COMMENT '跟踪误差',
  `strategy_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '策略代码',
  `asset_allocation` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '资产配置JSON',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '草稿' COMMENT '状态：草稿、活跃、暂停',
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '组合描述',
  `created_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建人',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  `updated_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新人',
  `updated_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) ON UPDATE CURRENT_TIMESTAMP(0) COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_index_code`(`index_code`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE,
  INDEX `idx_created_time`(`created_time`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 2 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '指数组合表' ROW_FORMAT = Dynamic;

-- ----------------------------
