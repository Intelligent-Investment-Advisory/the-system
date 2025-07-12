DROP TABLE IF EXISTS `a3_timing_config`;
CREATE TABLE `a3_timing_config`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `fund_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金名称',
  `weight` decimal(10, 4) NOT NULL COMMENT '权重',
  `asset_class` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '资产类别',
  `timing_rules` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '择时规则JSON',
  `stop_loss` decimal(10, 4) NULL DEFAULT NULL COMMENT '止损线',
  `take_profit` decimal(10, 4) NULL DEFAULT NULL COMMENT '止盈线',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '活跃' COMMENT '状态：活跃、暂停',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  `updated_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) ON UPDATE CURRENT_TIMESTAMP(0) COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_fund_code`(`fund_code`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE
) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '择时组合配置表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a3_timing_config
-- ----------------------------

-- ----------------------------
-- Table structure for a3_timing_monitor
-- ----------------------------
DROP TABLE IF EXISTS `a3_timing_monitor`;
CREATE TABLE `a3_timing_monitor`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `monitor_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '监控类型：择时信号监控、绩效监控、风险监控',
  `monitor_date` date NOT NULL COMMENT '监控日期',
  `total_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '总收益率',
  `annual_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '年化收益率',
  `max_drawdown` decimal(10, 4) NULL DEFAULT NULL COMMENT '最大回撤',
  `sharpe_ratio` decimal(10, 4) NULL DEFAULT NULL COMMENT '夏普比率',
  `timing_accuracy` decimal(10, 4) NULL DEFAULT NULL COMMENT '择时准确率',
  `signal_count` int NULL DEFAULT NULL COMMENT '信号次数',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '正常' COMMENT '状态：正常、预警、异常',
  `alert_message` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '预警信息',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_monitor_date`(`monitor_date`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE
) ENGINE = InnoDB CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '择时组合监控表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a3_timing_monitor
-- ----------------------------

-- ----------------------------
-- Table structure for a3_timing_portfolio
-- ----------------------------
DROP TABLE IF EXISTS `a3_timing_portfolio`;
CREATE TABLE `a3_timing_portfolio`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合名称',
  `portfolio_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合类型：择时型',
  `timing_strategy` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '择时策略',
  `risk_level` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '风险等级：低风险、中风险、高风险',
  `target_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '目标收益率',
  `max_drawdown` decimal(10, 4) NULL DEFAULT NULL COMMENT '最大回撤',
  `strategy_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '策略代码',
  `asset_allocation` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '资产配置JSON',
  `timing_signals` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '择时信号JSON',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '草稿' COMMENT '状态：草稿、活跃、暂停',
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '组合描述',
  `created_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建人',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  `updated_by` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新人',
  `updated_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) ON UPDATE CURRENT_TIMESTAMP(0) COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_timing_strategy`(`timing_strategy`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE,
  INDEX `idx_created_time`(`created_time`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 2 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '择时组合表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a3_timing_portfolio
-- ----------------------------
INSERT INTO `a3_timing_portfolio` VALUES (1, 'A3_20250706192252', '996', '择时型', '技术分析', 'LOW', 0.0300, 0.0300, '996', NULL, '996', '草稿', '996', NULL, '2025-07-06 19:22:52', NULL, '2025-07-06 19:22:52');
INSERT INTO `a3_timing_portfolio` VALUES (2, 'A3_20250706193334', '555', '择时型', '基本面分析', '低风险', NULL, NULL, '555', NULL, NULL, '活跃', '555', NULL, '2025-07-06 19:33:34', NULL, '2025-07-06 19:43:07');

-- ----------------------------
-- Table structure for a4_holding_fund
-- ----------------------------
DROP TABLE IF EXISTS `a4_holding_fund`;
CREATE TABLE `a4_holding_fund`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `fund_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金名称',
  `holding_amount` decimal(15, 2) NOT NULL COMMENT '持仓金额',
  `holding_quantity` decimal(15, 4) NOT NULL COMMENT '持仓数量',
  `current_price` decimal(10, 4) NULL DEFAULT NULL COMMENT '当前价格',
  `cost_price` decimal(10, 4) NULL DEFAULT NULL COMMENT '成本价格',
  `weight` decimal(10, 4) NOT NULL COMMENT '权重',
  `profit_loss` decimal(15, 2) NULL DEFAULT NULL COMMENT '盈亏',
  `profit_loss_rate` decimal(10, 4) NULL DEFAULT NULL COMMENT '盈亏率',
  `asset_class` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '资产类别',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '持有' COMMENT '状态：持有、卖出',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  `updated_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) ON UPDATE CURRENT_TIMESTAMP(0) COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_fund_code`(`fund_code`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '持仓基金表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a4_holding_fund
-- ----------------------------
INSERT INTO `a4_holding_fund` VALUES (1, '666', '666', '666', 666.00, 666.0000, 666.0000, 666.0000, 666.0000, 666.00, 666.0000, '666', '持有', '2025-07-06 19:44:52', '2025-07-06 19:44:52');

-- ----------------------------
-- Table structure for a4_rebalance_history
-- ----------------------------
DROP TABLE IF EXISTS `a4_rebalance_history`;
CREATE TABLE `a4_rebalance_history`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `rebalance_date` date NOT NULL COMMENT '调仓日期',
  `rebalance_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '调仓类型：定期调仓、触发调仓、手动调仓',
  `fund_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金名称',
  `action_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '操作类型：买入、卖出、调整',
  `old_weight` decimal(10, 4) NULL DEFAULT NULL COMMENT '原权重',
  `new_weight` decimal(10, 4) NULL DEFAULT NULL COMMENT '新权重',
  `quantity_change` decimal(15, 4) NULL DEFAULT NULL COMMENT '数量变化',
  `amount_change` decimal(15, 2) NULL DEFAULT NULL COMMENT '金额变化',
  `reason` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '调仓原因',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '已完成' COMMENT '状态：待执行、执行中、已完成、失败',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_rebalance_date`(`rebalance_date`) USING BTREE,
  INDEX `idx_fund_code`(`fund_code`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '历史调仓表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a4_rebalance_history
-- ----------------------------
INSERT INTO `a4_rebalance_history` VALUES (1, '111', '2025-07-06', '111', '111', '111', '111', 111.0000, 111.0000, 111.0000, 111.00, '111', '已完成', '2025-07-06 19:45:23');

-- ----------------------------
-- Table structure for a4_strategy_return
-- ----------------------------
DROP TABLE IF EXISTS `a4_strategy_return`;
CREATE TABLE `a4_strategy_return`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `strategy_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略代码',
  `strategy_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略名称',
  `return_date` date NOT NULL COMMENT '收益日期',
  `daily_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '日收益率',
  `cumulative_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '累计收益率',
  `annual_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '年化收益率',
  `max_drawdown` decimal(10, 4) NULL DEFAULT NULL COMMENT '最大回撤',
  `sharpe_ratio` decimal(10, 4) NULL DEFAULT NULL COMMENT '夏普比率',
  `volatility` decimal(10, 4) NULL DEFAULT NULL COMMENT '波动率',
  `beta` decimal(10, 4) NULL DEFAULT NULL COMMENT '贝塔系数',
  `alpha` decimal(10, 4) NULL DEFAULT NULL COMMENT '阿尔法系数',
  `benchmark_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '基准收益率',
  `excess_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '超额收益',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_strategy_code`(`strategy_code`) USING BTREE,
  INDEX `idx_return_date`(`return_date`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '策略收益表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of a4_strategy_return
-- ----------------------------
INSERT INTO `a4_strategy_return` VALUES (1, '333', '333', '333', '2025-07-01', 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, 333.0000, '2025-07-06 19:46:21');

-- ----------------------------
-- Table structure for a4_today_trade
-- ----------------------------
DROP TABLE IF EXISTS `a4_today_trade`;
CREATE TABLE `a4_today_trade`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键ID',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `trade_date` date NOT NULL COMMENT '交易日期',
  `fund_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金名称',
  `trade_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '交易类型：买入、卖出',
  `trade_amount` decimal(15, 2) NOT NULL COMMENT '交易金额',
  `trade_quantity` decimal(15, 4) NOT NULL COMMENT '交易数量',
  `trade_price` decimal(10, 4) NULL DEFAULT NULL COMMENT '交易价格',
  `commission` decimal(10, 2) NULL DEFAULT NULL COMMENT '手续费',
  `trade_reason` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '交易原因',
  `strategy_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '策略代码',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '已成交' COMMENT '状态：待成交、已成交、已取消',
  `created_time` datetime(0) NULL DEFAULT CURRENT_TIMESTAMP(0) COMMENT '创建时间',
  PRIMARY KEY (`id`) USING BTREE,
  INDEX `idx_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_trade_date`(`trade_date`) USING BTREE,
  INDEX `idx_fund_code`(`fund_code`) USING BTREE,
  INDEX `idx_status`(`status`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '今日成交表' ROW_FORMAT = Dynamic;
