INSERT INTO `strategy_evaluation` VALUES (1, 'EV001', 'ST001', '价值投资策略', '2023年度', 8.5, 7.8, 8.2, 8.2, '优秀', '策略表现稳定，建议继续执行并优化选股标准', '张三', '2024-01-23 10:00:00', '2024-01-23 10:00:00');
INSERT INTO `strategy_evaluation` VALUES (2, 'EV002', 'ST002', '动量策略', '2023年度', 7.8, 6.5, 7, 7.1, '良好', '收益表现良好，但风险控制需要加强', '李四', '2024-01-23 11:00:00', '2024-01-23 11:00:00');
INSERT INTO `strategy_evaluation` VALUES (3, 'EV003', 'ST003', '多因子策略', '2023年度', 9.2, 8.5, 8.8, 8.8, '优秀', '综合表现优异，建议扩大应用范围', '王五', '2024-01-23 12:00:00', '2024-01-23 12:00:00');
INSERT INTO `strategy_evaluation` VALUES (4, 'EV004', 'ST001', '价值投资策略', '2023年第四季度', 7.5, 8, 7.8, 7.8, '良好', '季度表现稳定，建议关注市场环境变化', '张三', '2024-01-23 13:00:00', '2024-01-23 13:00:00');
INSERT INTO `strategy_evaluation` VALUES (5, 'EV005', 'ST005', '低波动策略', '2023年下半年', 8.8, 9, 8.5, 8.8, '优秀', '风险控制出色，建议作为核心策略之一', '李四', '2024-01-23 14:00:00', '2024-01-23 14:00:00');

-- ----------------------------
-- Table structure for strategy_monitor
-- ----------------------------
DROP TABLE IF EXISTS `strategy_monitor`;
CREATE TABLE `strategy_monitor`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `monitor_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '监控代码',
  `strategy_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略代码',
  `strategy_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略名称',
  `monitor_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '监控类型',
  `alert_condition` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '预警条件',
  `alert_threshold` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '预警阈值',
  `alert_action` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '预警动作',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '活跃' COMMENT '监控状态',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建者',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `monitor_code`(`monitor_code`) USING BTREE,
  INDEX `idx_monitor_strategy`(`strategy_code`) USING BTREE,
  INDEX `idx_monitor_type`(`monitor_type`) USING BTREE,
  CONSTRAINT `strategy_monitor_ibfk_1` FOREIGN KEY (`strategy_code`) REFERENCES `strategy` (`strategy_code`) ON DELETE RESTRICT ON UPDATE RESTRICT
) ENGINE = InnoDB AUTO_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '策略监控表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of strategy_monitor
-- ----------------------------
INSERT INTO `strategy_monitor` VALUES (1, 'MT001', 'ST001', '价值投资策略', '绩效监控', '收益率低于阈值', '5%', '发送邮件通知', '活跃', '张三', '2024-01-22 10:00:00', '2024-01-22 10:00:00');
INSERT INTO `strategy_monitor` VALUES (2, 'MT002', 'ST002', '动量策略', '风险监控', '最大回撤超过阈值', '15%', '暂停策略执行', '活跃', '李四', '2024-01-22 11:00:00', '2024-01-22 11:00:00');
INSERT INTO `strategy_monitor` VALUES (3, 'MT003', 'ST003', '多因子策略', '绩效监控', '夏普比率低于阈值', '1.5', '调整因子权重', '活跃', '王五', '2024-01-22 12:00:00', '2024-01-22 12:00:00');
INSERT INTO `strategy_monitor` VALUES (4, 'MT004', 'ST001', '价值投资策略', '仓位监控', '持仓集中度过高', '30%', '分散投资', '预警', '张三', '2024-01-22 13:00:00', '2024-01-22 13:00:00');
INSERT INTO `strategy_monitor` VALUES (5, 'MT005', 'ST005', '低波动策略', '风险监控', '波动率超过阈值', '12%', '降低仓位', '暂停', '李四', '2024-01-22 14:00:00', '2024-01-22 14:00:00');

-- ----------------------------
-- Table structure for style_factor
-- ----------------------------
DROP TABLE IF EXISTS `style_factor`;
CREATE TABLE `style_factor`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `style_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '风格因子代码',
  `style_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '风格因子名称',
  `style_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '风格类型',
  `base_factors` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基础因子（逗号分隔）',
  `weights` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '权重（逗号分隔）',
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '描述',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建者',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'pending' COMMENT '状态',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `style_code`(`style_code`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 4 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '风格投资因子表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of style_factor
-- ----------------------------
INSERT INTO `style_factor` VALUES (1, 'SF001', '成长风格因子', '成长风格', 'F007,F003', '0.6,0.4', '专注于成长型公司的风格因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `style_factor` VALUES (2, 'SF002', '价值风格因子', '价值风格', 'F002,F004', '0.7,0.3', '专注于价值型公司的风格因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `style_factor` VALUES (3, 'SF003', '平衡风格因子', '平衡风格', 'F002,F003,F007', '0.4,0.3,0.3', '平衡价值、质量和成长的风格因子', 'admin', 'pending', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `style_factor` VALUES (4, 'SF004', '动量风格因子', '动量风格', 'F001,F006', '0.8,0.2', '专注于动量交易的风格因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

-- ----------------------------
-- Table structure for trade_analysis
-- ----------------------------
DROP TABLE IF EXISTS `trade_analysis`;
CREATE TABLE `trade_analysis`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `analysis_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '分析代码',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合名称',
  `analysis_period` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '分析周期',
  `total_trades` int NOT NULL DEFAULT 0 COMMENT '总交易次数',
  `total_volume` double NOT NULL DEFAULT 0 COMMENT '总交易量',
  `total_amount` double NOT NULL DEFAULT 0 COMMENT '总交易金额',
  `avg_trade_size` double NULL DEFAULT NULL COMMENT '平均交易规模',
  `win_rate` double NULL DEFAULT NULL COMMENT '胜率',
  `profit_loss` double NULL DEFAULT NULL COMMENT '盈亏',
  `slippage` double NULL DEFAULT NULL COMMENT '滑点',
  `execution_quality` double NULL DEFAULT NULL COMMENT '执行质量',
  `performance_analysis` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '绩效分析',
  `risk_analysis` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '风险分析',
  `recommendations` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '建议',
  `analyst` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '分析师',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `analysis_code`(`analysis_code`) USING BTREE,
  INDEX `idx_trade_analysis_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_trade_analysis_period`(`analysis_period`) USING BTREE,
  INDEX `idx_trade_analysis_analyst`(`analyst`) USING BTREE,
  INDEX `idx_trade_analysis_create_time`(`create_time`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '交易分析表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of trade_analysis
-- ----------------------------
INSERT INTO `trade_analysis` VALUES (1, 'ANA20241201001', 'PORT001', '稳健成长组合', '月度', 25, 2500000, 2500000, 100000, 68, 150000, 0.15, 85.5, '组合表现稳健，超额收益明显，主要受益于选股策略的有效性', '风险控制良好，最大回撤控制在合理范围内', '建议继续持有核心仓位，适当增加防御性配置', '分析师A', '2024-12-01 16:00:00', '2024-12-01 16:00:00');
INSERT INTO `trade_analysis` VALUES (2, 'ANA20241201002', 'PORT002', '积极进取组合', '月度', 35, 3500000, 3500000, 100000, 62, 200000, 0.25, 78, '组合收益较高但波动较大，适合风险承受能力较强的投资者', '风险水平较高，需要密切关注市场变化', '建议适当降低仓位，增加风险对冲工具', '分析师B', '2024-12-01 16:30:00', '2024-12-01 16:30:00');
INSERT INTO `trade_analysis` VALUES (3, 'ANA20241201003', 'PORT003', '价值投资组合', '月度', 20, 2000000, 2000000, 100000, 75, 120000, 0.1, 90, '价值投资策略表现优异，长期收益稳定', '风险控制优秀，回撤控制良好', '建议保持当前策略，继续寻找价值投资机会', '分析师C', '2024-12-01 17:00:00', '2024-12-01 17:00:00');
INSERT INTO `trade_analysis` VALUES (4, 'ANA20241201004', 'PORT001', '稳健成长组合', '季度', 75, 7500000, 7500000, 100000, 70, 450000, 0.18, 82, '季度表现符合预期，策略执行到位', '季度风险指标在合理范围内', '建议继续执行现有策略，关注市场变化', '分析师A', '2024-12-01 17:30:00', '2024-12-01 17:30:00');
INSERT INTO `trade_analysis` VALUES (5, 'ANA20241201005', 'PORT002', '积极进取组合', '季度', 105, 10500000, 10500000, 100000, 65, 600000, 0.3, 75, '季度收益较高但波动较大，需要优化风险控制', '季度风险水平偏高，需要调整', '建议优化仓位配置，加强风险控制', '分析师B', '2024-12-01 18:00:00', '2024-12-01 18:00:00');

-- ----------------------------
-- Table structure for trade_execution
-- ----------------------------
DROP TABLE IF EXISTS `trade_execution`;
CREATE TABLE `trade_execution`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `execution_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '执行代码',
  `order_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '订单代码',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合名称',
  `fund_code` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金名称',
  `execution_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '执行类型',
  `execution_amount` double NULL DEFAULT NULL COMMENT '执行金额',
  `execution_quantity` double NULL DEFAULT NULL COMMENT '执行数量',
  `execution_price` double NULL DEFAULT NULL COMMENT '执行价格',
  `execution_status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '待执行' COMMENT '执行状态',
  `execution_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '执行时间',
  `broker` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '券商',
  `account_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '账户代码',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建者',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `execution_code`(`execution_code`) USING BTREE,
  INDEX `idx_trade_execution_order_code`(`order_code`) USING BTREE,
  INDEX `idx_trade_execution_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_trade_execution_status`(`execution_status`) USING BTREE,
  INDEX `idx_trade_execution_create_time`(`create_time`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '交易执行表' ROW_FORMAT = Dynamic;
