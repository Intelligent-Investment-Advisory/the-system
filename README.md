DROP TABLE IF EXISTS `b1_strategy_audit`;
CREATE TABLE `b1_strategy_audit`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `strategy_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '策略组合名称',
  `strategy_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '类型（策略/FOF）',
  `submitter` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '提交人',
  `submit_time` datetime(0) NOT NULL COMMENT '提交时间',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '审核状态（待审核/已上架/驳回）',
  `audit_opinion` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '审核意见',
  `audit_user` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '审核人',
  `audit_time` datetime(0) NULL DEFAULT NULL COMMENT '审核时间',
  PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '策略组合上架审核表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of b1_strategy_audit
-- ----------------------------
INSERT INTO `b1_strategy_audit` VALUES (1, '996', '996', '996', '2025-07-07 19:12:53', '已上架', '996', '996', '2025-07-07 19:13:02');

-- ----------------------------
-- Table structure for b2_portfolio_position
-- ----------------------------
DROP TABLE IF EXISTS `b2_portfolio_position`;
CREATE TABLE `b2_portfolio_position`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `portfolio_id` bigint NOT NULL COMMENT '组合ID',
  `fund_code` varchar(30) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金名称',
  `position_ratio` decimal(8, 4) NOT NULL COMMENT '持仓比例',
  `update_time` datetime(0) NOT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '组合产品持仓表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of b2_portfolio_position
-- ----------------------------
INSERT INTO `b2_portfolio_position` VALUES (1, 1, '996', '996', 0.0112, '2025-07-07 19:17:11');

-- ----------------------------
-- Table structure for b3_trade_instruction
-- ----------------------------
DROP TABLE IF EXISTS `b3_trade_instruction`;
CREATE TABLE `b3_trade_instruction`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `instruction_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '指令类型（买入/卖出）',
  `fund_code` varchar(30) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '基金名称',
  `amount` decimal(16, 2) NOT NULL COMMENT '金额',
  `trader` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '交易员',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '状态（待执行/已完成/已撤销）',
  `create_time` datetime(0) NOT NULL COMMENT '创建时间',
  `execute_time` datetime(0) NULL DEFAULT NULL COMMENT '执行时间',
  `remark` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '备注',
  PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '交易指令表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of b3_trade_instruction
-- ----------------------------
INSERT INTO `b3_trade_instruction` VALUES (1, '买入', '996', '996', 996.00, '996', '已完成', '2025-07-07 19:21:12', '2025-07-07 19:21:15', '996');

-- ----------------------------
-- Table structure for b4_error_handle
-- ----------------------------
DROP TABLE IF EXISTS `b4_error_handle`;
CREATE TABLE `b4_error_handle`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `error_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '差错类型',
  `description` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '差错描述',
  `create_time` datetime(0) NULL DEFAULT NULL COMMENT '创建时间',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '状态',
  PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '差错处理表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of b4_error_handle
-- ----------------------------
INSERT INTO `b4_error_handle` VALUES (1, '996', '996', '2025-07-07 19:27:17', '待处理');

-- ----------------------------
-- Table structure for b5_quick_action
-- ----------------------------
DROP TABLE IF EXISTS `b5_quick_action`;
CREATE TABLE `b5_quick_action`  (
  `id` bigint NOT NULL AUTO_INCREMENT COMMENT '主键',
  `audit_id` bigint NOT NULL COMMENT '关联审核ID',
  `action_type` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '操作类型（下单/驳回）',
  `operator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '操作人',
  `action_time` datetime(0) NOT NULL COMMENT '操作时间',
  PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 1 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '一键操作表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of b5_quick_action
-- ----------------------------
INSERT INTO `b5_quick_action` VALUES (1, 996, '996', '996', '2025-07-07 19:33:24');

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
) ENGINE = InnoDB AUTO_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '策略回测表' ROW_FORMAT = Dynamic;

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
) ENGINE = InnoDB AUTO_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '衍生因子表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of derived_factor
-- ----------------------------
INSERT INTO `derived_factor` VALUES (1, 'DF001', '综合动量因子', 'F001,F005', '0.6,0.4', '0.6*动量因子+0.4*波动率因子', '结合动量和波动率的综合技术因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `derived_factor` VALUES (2, 'DF002', '价值质量因子', 'F002,F003', '0.5,0.5', '0.5*价值因子+0.5*质量因子', '结合价值和质量的综合基本面因子', 'admin', 'active', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `derived_factor` VALUES (3, 'DF003', '多因子组合', 'F001,F002,F003,F004', '0.25,0.25,0.25,0.25', '0.25*(动量+价值+质量+规模)', '经典多因子模型组合', 'admin', 'pending', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `derived_factor` VALUES (4, 'F996', '996', 'F001', '0.6,0.4', '价格变化率计算', '基于价格动量的技术分析因子，用于捕捉价格趋势996', 'admin', 'pending', '2025-06-30 14:58:38', '2025-06-30 14:58:38');
INSERT INTO `derived_factor` VALUES (5, '555', '555', 'F008', '0.6,0.4', '资产负债率', '基于555财务杠杆的因子，用于分析公司财务结构', 'admin', 'pending', '2025-07-06 13:09:46', '2025-07-06 13:09:46');

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

-- ----------------------------
-- Records of factor
-- ----------------------------
INSERT INTO `factor` VALUES (1, 'F001', '动量因子', '动量因子', '技术因子', '基于价格动量的技术分析因子，用于捕捉价格趋势996', 'Wind', '价格变化率计算', '动量,技术分析,趋势', '2024-01-01 10:00:00', '2025-06-30 14:51:35');
INSERT INTO `factor` VALUES (2, 'F002', '价值因子', '价值因子', '基本面因子', '基于估值指标的基本面因子，用于识别被低估的股票', 'CSMAR', 'PE、PB等估值指标', '价值,基本面,估值', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor` VALUES (3, 'F003', '质量因子', '质量因子', '基本面因子', '基于财务质量的基本面因子，用于识别高质量公司', 'Wind', 'ROE、ROA等财务指标', '质量,基本面,财务', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor` VALUES (4, 'F004', '规模因子', '规模因子', '基本面因子', '基于公司规模的基本面因子，小盘股通常具有超额收益', 'CSMAR', '市值计算', '规模,基本面,市值', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor` VALUES (5, 'F005', '波动率因子', '风险因子', '技术因子', '基于价格波动率的风险因子，用于风险控制', 'Wind', '历史波动率计算', '波动率,风险,技术分析', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor` VALUES (6, 'F006', '流动性因子', '流动性因子', '技术因子', '基于交易流动性的技术因子，用于流动性分析', 'Wind', '换手率、成交量', '流动性,技术分析,交易', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor` VALUES (7, 'F007', '盈利因子', '盈利因子', '基本面因子', '基于盈利能力的因子，用于识别盈利能力强公司', 'Wind', '净利润增长率', '盈利,基本面,增长', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor` VALUES (8, 'F008', '杠杆因子', '杠杆因子', '基本面因子', '基于财务杠杆的因子，用于分析公司财务结构', 'Wind', '资产负债率', '杠杆,基本面,财务', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor` VALUES (9, '3333', '3333', '成长因子', '基本面因子', '3333', '东方财富', '3333', '3333', '2025-07-06 13:25:41', '2025-07-06 13:25:41');

-- ----------------------------
-- Table structure for factor_tree
-- ----------------------------
DROP TABLE IF EXISTS `factor_tree`;
CREATE TABLE `factor_tree`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `tree_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '树代码',
  `tree_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '树名称',
  `tree_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '树类型',
  `parent_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '父节点代码',
  `node_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '节点代码',
  `node_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '节点名称',
  `node_level` int NOT NULL COMMENT '节点层级',
  `sort_order` int NOT NULL COMMENT '排序',
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '描述',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 8 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '因子树表' ROW_FORMAT = Dynamic;
