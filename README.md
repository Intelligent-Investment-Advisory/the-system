INSERT INTO `portfolio_monitor` VALUES (1, 'MON001', 'PF001', '稳健增长组合', '风险监控', '最大回撤超过阈值', '15%', '自动减仓', '12.5%', '活跃', '张三', '2024-01-15 11:00:00', '2024-01-15 11:00:00');
INSERT INTO `portfolio_monitor` VALUES (2, 'MON002', 'PF001', '稳健增长组合', '绩效监控', '收益率低于目标', '6%', '发送预警邮件', '7.2%', '活跃', '张三', '2024-01-15 11:00:00', '2024-01-15 11:00:00');
INSERT INTO `portfolio_monitor` VALUES (3, 'MON003', 'PF002', '积极进取组合', '风险监控', '波动率超过阈值', '25%', '调整仓位', '22.3%', '活跃', '李四', '2024-01-16 15:30:00', '2024-01-16 15:30:00');
INSERT INTO `portfolio_monitor` VALUES (4, 'MON004', 'PF002', '积极进取组合', '再平衡监控', '权重偏离超过5%', '5%', '触发再平衡', '3.2%', '活跃', '李四', '2024-01-16 15:30:00', '2024-01-16 15:30:00');
INSERT INTO `portfolio_monitor` VALUES (5, 'MON005', 'PF003', '保守收益组合', '预警监控', '信用风险上升', 'BBB级', '降低久期', 'A级', '预警', '王五', '2024-01-17 10:00:00', '2024-01-17 10:00:00');
INSERT INTO `portfolio_monitor` VALUES (6, 'MON006', 'PF004', '指数增强组合', '绩效监控', '超额收益为负', '0%', '调整策略', '-1.2%', '暂停', '张三', '2024-01-18 17:00:00', '2024-01-18 17:00:00');

-- ----------------------------
-- Table structure for strategy
-- ----------------------------
DROP TABLE IF EXISTS `strategy`;
CREATE TABLE `strategy`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `strategy_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略代码',
  `strategy_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略名称',
  `strategy_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略类型',
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '策略描述',
  `factors` varchar(500) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '使用的因子（逗号分隔）',
  `parameters` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '策略参数（JSON格式）',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建者',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '草稿' COMMENT '状态',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `strategy_code`(`strategy_code`) USING BTREE,
  INDEX `idx_strategy_code`(`strategy_code`) USING BTREE,
  INDEX `idx_strategy_type`(`strategy_type`) USING BTREE,
  INDEX `idx_strategy_status`(`status`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '策略表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of strategy
-- ----------------------------
INSERT INTO `strategy` VALUES (1, 'ST001', '价值投资策略', '基本面分析', '基于公司基本面指标的价值投资策略，重点关注低估值、高ROE的优质公司', 'PE,ROE,PB,ROA', '{\"pe_threshold\": 15, \"roe_threshold\": 0.15, \"pb_threshold\": 2.0}', '张三', '活跃', '2024-01-15 10:30:00', '2024-01-15 10:30:00');
INSERT INTO `strategy` VALUES (2, 'ST002', '动量策略', '技术分析', '基于价格动量的技术分析策略，捕捉市场趋势', 'MA,MACD,RSI,KDJ', '{\"ma_period\": 20, \"momentum_period\": 10, \"rsi_threshold\": 70}', '李四', '活跃', '2024-01-16 14:20:00', '2024-01-16 14:20:00');
INSERT INTO `strategy` VALUES (3, 'ST003', '多因子策略', '量化策略', '综合多个因子的量化投资策略，平衡收益与风险', 'PE,PB,ROE,动量,波动率', '{\"factor_weights\": {\"pe\": 0.2, \"pb\": 0.2, \"roe\": 0.2, \"momentum\": 0.2, \"volatility\": 0.2}}', '王五', '草稿', '2024-01-17 09:15:00', '2024-01-17 09:15:00');
INSERT INTO `strategy` VALUES (4, 'ST004', '行业轮动策略', '混合策略', '基于行业景气度的轮动投资策略', '行业景气度,估值水平,资金流向', '{\"rotation_period\": 30, \"industry_count\": 5}', '张三', '暂停', '2024-01-18 16:45:00', '2024-01-18 16:45:00');
INSERT INTO `strategy` VALUES (5, 'ST005', '低波动策略', '量化策略', '选择低波动率股票的投资策略，追求稳定收益996333', '波动率,夏普比率,最大回撤', '{\"volatility_threshold\": 0.15, \"sharpe_threshold\": 1.0}', '李四', '活跃', '2024-01-19 11:30:00', '2025-06-30 15:03:52');
INSERT INTO `strategy` VALUES (6, '007', 'F007', '007', '007', '', '', 'admin', '活跃', '2025-06-30 15:07:15', '2025-06-30 15:07:33');

-- ----------------------------
-- Table structure for strategy_evaluation
-- ----------------------------
DROP TABLE IF EXISTS `strategy_evaluation`;
CREATE TABLE `strategy_evaluation`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `evaluation_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '评估代码',
  `strategy_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略代码',
  `strategy_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略名称',
  `evaluation_period` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '评估周期',
  `performance_score` double NULL DEFAULT NULL COMMENT '绩效评分',
  `risk_score` double NULL DEFAULT NULL COMMENT '风险评分',
  `stability_score` double NULL DEFAULT NULL COMMENT '稳定性评分',
  `overall_score` double NULL DEFAULT NULL COMMENT '综合评分',
  `evaluation_result` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '评估结果',
  `recommendations` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '建议',
  `evaluator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '评估人',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `evaluation_code`(`evaluation_code`) USING BTREE,
  INDEX `idx_evaluation_strategy`(`strategy_code`) USING BTREE,
  INDEX `idx_evaluation_period`(`evaluation_period`) USING BTREE,
  CONSTRAINT `strategy_evaluation_ibfk_1` FOREIGN KEY (`strategy_code`) REFERENCES `strategy` (`strategy_code`) ON DELETE RESTRICT ON UPDATE RESTRICT
) ENGINE = InnoDB AUTO_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '策略评估表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of strategy_evaluation
-- ----------------------------
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
) ENGINE = InnoDB AUTO_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '策略监控表' ROW_FORMAT = Dynamic;

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
) ENGINE = InnoDB AUTO_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '交易执行表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of trade_execution
-- ----------------------------
INSERT INTO `trade_execution` VALUES (1, 'EXE20241201001', 'ORD20241201001', 'PORT001', '稳健成长组合', '000001', '华夏成长混合', '市价单', 100000, 50000, 2, '已执行', '2024-12-01 09:35:00', '中信证券', 'ACC001', '张三', '2024-12-01 09:35:00', '2024-12-01 09:35:00');
INSERT INTO `trade_execution` VALUES (2, 'EXE20241201002', 'ORD20241201003', 'PORT001', '稳健成长组合', '000003', '嘉实增长混合', '限价单', 80000, 40000, 2, '已执行', '2024-12-01 14:25:00', '中信证券', 'ACC001', '张三', '2024-12-01 14:25:00', '2024-12-01 14:25:00');
INSERT INTO `trade_execution` VALUES (3, 'EXE20241201003', 'ORD20241201002', 'PORT002', '积极进取组合', '000002', '易方达消费行业', '市价单', 150000, 30000, 5, '待执行', NULL, '华泰证券', 'ACC002', '李四', '2024-12-01 10:20:00', '2024-12-01 10:20:00');
INSERT INTO `trade_execution` VALUES (4, 'EXE20241201004', 'ORD20241201004', 'PORT003', '价值投资组合', '000004', '富国天惠成长', '止损单', 200000, 100000, 2, '已取消', NULL, '国泰君安', 'ACC003', '王五', '2024-12-01 15:50:00', '2024-12-01 15:50:00');
INSERT INTO `trade_execution` VALUES (5, 'EXE20241201005', 'ORD20241201005', 'PORT002', '积极进取组合', '000005', '博时主题行业', '市价单', 120000, 60000, 2, '执行失败', NULL, '华泰证券', 'ACC002', '李四', '2024-12-01 16:35:00', '2024-12-01 16:35:00');

-- ----------------------------
-- Table structure for trade_monitor
-- ----------------------------
DROP TABLE IF EXISTS `trade_monitor`;
CREATE TABLE `trade_monitor`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `monitor_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '监控代码',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合名称',
  `monitor_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '监控类型',
  `monitor_target` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '监控目标',
  `alert_condition` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '预警条件',
  `alert_threshold` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '预警阈值',
  `alert_action` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '预警动作',
  `current_value` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '当前值',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '启用' COMMENT '监控状态',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建者',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `monitor_code`(`monitor_code`) USING BTREE,
  INDEX `idx_trade_monitor_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_trade_monitor_type`(`monitor_type`) USING BTREE,
  INDEX `idx_trade_monitor_status`(`status`) USING BTREE,
  INDEX `idx_trade_monitor_create_time`(`create_time`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '交易监控表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of trade_monitor
-- ----------------------------
INSERT INTO `trade_monitor` VALUES (1, 'MON20241201001', 'PORT001', '稳健成长组合', '价格监控', '华夏成长混合', '价格下跌超过阈值', '5%', '发送预警邮件', '2.10', '启用', '张三', '2024-12-01 08:00:00', '2024-12-01 08:00:00');
INSERT INTO `trade_monitor` VALUES (2, 'MON20241201002', 'PORT002', '积极进取组合', '波动率监控', '易方达消费行业', '波动率超过阈值', '15%', '暂停交易', '12%', '启用', '李四', '2024-12-01 08:30:00', '2024-12-01 08:30:00');
INSERT INTO `trade_monitor` VALUES (3, 'MON20241201003', 'PORT003', '价值投资组合', '流动性监控', '富国天惠成长', '流动性不足', '100万', '调整持仓', '150万', '启用', '王五', '2024-12-01 09:00:00', '2024-12-01 09:00:00');
INSERT INTO `trade_monitor` VALUES (4, 'MON20241201004', 'PORT001', '稳健成长组合', '风险监控', '组合整体风险', 'VaR超过阈值', '3%', '减仓操作', '2.5%', '启用', '张三', '2024-12-01 09:15:00', '2024-12-01 09:15:00');
INSERT INTO `trade_monitor` VALUES (5, 'MON20241201005', 'PORT002', '积极进取组合', '收益监控', '组合收益率', '收益率低于阈值', '-5%', '重新评估', '-2%', '停用', '李四', '2024-12-01 10:00:00', '2024-12-01 10:00:00');

-- ----------------------------
-- Table structure for trade_order
-- ----------------------------
DROP TABLE IF EXISTS `trade_order`;
CREATE TABLE `trade_order`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `order_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '订单代码',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合名称',
  `fund_code` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金名称',
  `order_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '订单类型（买入/卖出）',
  `order_amount` double NULL DEFAULT NULL COMMENT '订单金额',
  `order_quantity` double NULL DEFAULT NULL COMMENT '订单数量',
  `order_price` double NULL DEFAULT NULL COMMENT '订单价格',
  `order_status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '待执行' COMMENT '订单状态',
  `order_reason` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '订单原因',
  `strategy_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '策略代码',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建者',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `order_code`(`order_code`) USING BTREE,
  INDEX `idx_trade_order_portfolio_code`(`portfolio_code`) USING BTREE,
  INDEX `idx_trade_order_fund_code`(`fund_code`) USING BTREE,
  INDEX `idx_trade_order_status`(`order_status`) USING BTREE,
  INDEX `idx_trade_order_create_time`(`create_time`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '交易订单表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of trade_order
-- ----------------------------
INSERT INTO `trade_order` VALUES (1, 'ORD20241201001', 'PORT001', '稳健成长组合', '000001', '华夏成长混合', '买入', 100000, 50000, 2, '已执行', '策略调仓', 'STR001', '张三', '2024-12-01 09:30:00', '2024-12-01 09:30:00');
INSERT INTO `trade_order` VALUES (2, 'ORD20241201002', 'PORT002', '积极进取组合', '000002', '易方达消费行业', '买入', 150000, 30000, 5, '待执行', '新增配置', 'STR002', '李四', '2024-12-01 10:15:00', '2024-12-01 10:15:00');
INSERT INTO `trade_order` VALUES (3, 'ORD20241201003', 'PORT001', '稳健成长组合', '000003', '嘉实增长混合', '卖出', 80000, 40000, 2, '已执行', '止盈操作', 'STR001', '张三', '2024-12-01 14:20:00', '2024-12-01 14:20:00');
INSERT INTO `trade_order` VALUES (5, 'ORD20241201005', 'PORT002', '积极进取组合', '000005', '博时主题行业', '买入', 120000, 60000, 2, '执行失败', '资金不足996', 'STR002', '李四', '2024-12-01 16:30:00', '2025-06-30 15:57:03');
INSERT INTO `trade_order` VALUES (6, '996', '996', '996', '996', '996', '买入', 996, 996, 996, '待执行', '996', '996', 'admin', '2025-06-30 16:00:02', '2025-06-30 16:00:02');

-- ----------------------------
-- Table structure for user
-- ----------------------------
DROP TABLE IF EXISTS `user`;
CREATE TABLE `user`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `username` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL COMMENT '用户名',
  `password` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL COMMENT '密码',
  `email` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '邮箱',
  `phone` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '手机号',
  `real_name` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '真实姓名',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `username`(`username`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 3 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_0900_ai_ci COMMENT = '用户表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of user
-- ----------------------------
INSERT INTO `user` VALUES (1, 'admin', '123456', 'admin@example.com', '13800138000', '管理员', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `user` VALUES (2, 'user1', '123456', 'user1@example.com', '13800138001', '张三', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `user` VALUES (3, 'user2', '123456', 'user2@example.com', '13800138002', '李四', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

SET FOREIGN_KEY_CHECKS = 1;
