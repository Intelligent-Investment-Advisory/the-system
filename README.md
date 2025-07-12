INSERT INTO `factor_tree` VALUES (1, 'TREE001', '因子分类树', '分类树', NULL, 'ROOT', '因子根节点', 0, 1, '因子分类的根节点', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor_tree` VALUES (2, 'TREE001', '因子分类树', '分类树', 'ROOT', 'TECH', '技术因子', 1, 1, '技术分析类因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor_tree` VALUES (3, 'TREE001', '因子分类树', '分类树', 'ROOT', 'FUND', '基本面因子', 1, 2, '基本面分析类因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor_tree` VALUES (4, 'TREE001', '因子分类树', '分类树', 'ROOT', 'MACRO', '宏观因子', 1, 3, '宏观经济类因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor_tree` VALUES (5, 'TREE001', '因子分类树', '分类树', 'TECH', 'MOMENTUM', '动量因子', 2, 1, '价格动量相关因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor_tree` VALUES (6, 'TREE001', '因子分类树', '分类树', 'TECH', 'VOLATILITY', '波动率因子', 2, 2, '价格波动率相关因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor_tree` VALUES (7, 'TREE001', '因子分类树', '分类树', 'FUND', 'VALUE', '价值因子', 2, 1, '估值相关因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');
INSERT INTO `factor_tree` VALUES (8, 'TREE001', '因子分类树', '分类树', 'FUND', 'QUALITY', '质量因子', 2, 2, '财务质量相关因子', '2024-01-01 10:00:00', '2024-01-01 10:00:00');

-- ----------------------------
-- Table structure for fund
-- ----------------------------
DROP TABLE IF EXISTS `fund`;
CREATE TABLE `fund`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `fund_code` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL COMMENT '基金名称',
  `fund_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '基金类型',
  `fund_company` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '基金公司',
  `fund_manager` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '基金经理',
  `net_value` decimal(10, 4) NULL DEFAULT NULL COMMENT '净值',
  `total_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '总收益率',
  `risk_level` int NULL DEFAULT NULL COMMENT '风险等级',
  `tags` text CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL COMMENT '基金标签',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `fund_code`(`fund_code`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 10 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_0900_ai_ci COMMENT = '基金表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of fund
-- ----------------------------
INSERT INTO `fund` VALUES (1, '000001', '华夏成长混合', '混合型基金', '华夏基金管理有限公司', '张坤', 1.2345, 23.4500, 3, '成长型,混合型,股票投资', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund` VALUES (2, '000002', '易方达消费行业股票', '股票型基金', '易方达基金管理有限公司', '萧楠', 2.1567, 15.6700, 4, '消费行业,股票型,白酒股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund` VALUES (3, '000003', '嘉实增长混合', '混合型基金', '嘉实基金管理有限公司', '刘彦春', 1.8901, 18.9000, 3, '增长型,混合型,科技股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund` VALUES (4, '000004', '南方稳健成长混合', '混合型基金', '南方基金管理有限公司', '王宗合', 1.5678, 12.3400, 3, '稳健型,混合型,价值投资', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund` VALUES (5, '000005', '博时主题行业混合', '混合型基金', '博时基金管理有限公司', '谢治宇', 1.7890, 16.7800, 4, '主题投资,混合型,行业轮动', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund` VALUES (6, '000006', '华夏债券A', '债券型基金', '华夏基金管理有限公司', '张坤', 1.1234, 8.9000, 2, '债券型,低风险,固定收益', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund` VALUES (7, '000007', '易方达货币A', '货币型基金', '易方达基金管理有限公司', '萧楠', 1.0001, 2.5000, 1, '货币型,超低风险,现金管理', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund` VALUES (8, '000008', '嘉实沪深300ETF', '指数型基金', '嘉实基金管理有限公司', '刘彦春', 1.4567, 10.2300, 3, '指数型,ETF,沪深300', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund` VALUES (9, '000009', '南方中证500ETF', '指数型基金', '南方基金管理有限公司', '王宗合', 1.2345, 9.8700, 3, '指数型,ETF,中证500', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund` VALUES (10, '000010', '博时黄金ETF', '商品型基金', '博时基金管理有限公司', '谢治宇', 1.6789, 5.6700, 4, '商品型,ETF,黄金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

-- ----------------------------
-- Table structure for fund_company
-- ----------------------------
DROP TABLE IF EXISTS `fund_company`;
CREATE TABLE `fund_company`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `company_code` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL COMMENT '公司代码',
  `company_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL COMMENT '公司名称',
  `company_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '公司类型',
  `establishment_date` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '成立日期',
  `registered_capital` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '注册资本',
  `tags` text CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL COMMENT '公司标签',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `company_code`(`company_code`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_0900_ai_ci COMMENT = '基金公司表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of fund_company
-- ----------------------------
INSERT INTO `fund_company` VALUES (1, 'C001', '华夏基金管理有限公司', '公募基金', '1998-04-09', '2.38亿元', '大型基金公司,股票型基金,债券型基金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund_company` VALUES (2, 'C002', '易方达基金管理有限公司', '公募基金', '2001-04-17', '1.2亿元', '大型基金公司,指数基金,混合型基金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund_company` VALUES (3, 'C003', '嘉实基金管理有限公司', '公募基金', '1999-03-25', '1.5亿元', '大型基金公司,货币基金,债券型基金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund_company` VALUES (4, 'C004', '南方基金管理有限公司', '公募基金', '1998-03-06', '3亿元', '大型基金公司,股票型基金,混合型基金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund_company` VALUES (5, 'C005', '博时基金管理有限公司', '公募基金', '1998-07-13', '1亿元', '大型基金公司,指数基金,债券型基金', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

-- ----------------------------
-- Table structure for fund_manager
-- ----------------------------
DROP TABLE IF EXISTS `fund_manager`;
CREATE TABLE `fund_manager`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `manager_code` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL COMMENT '经理代码',
  `manager_name` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NOT NULL COMMENT '经理姓名',
  `company` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '所属公司',
  `experience` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '从业经验',
  `avg_return` decimal(10, 4) NULL DEFAULT NULL COMMENT '平均收益率',
  `tags` text CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL COMMENT '经理标签',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `manager_code`(`manager_code`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 5 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_0900_ai_ci COMMENT = '基金经理表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of fund_manager
-- ----------------------------
INSERT INTO `fund_manager` VALUES (1, 'M001', '张坤', '易方达基金管理有限公司', '10年', 15.5000, '价值投资,蓝筹股,长期投资', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund_manager` VALUES (2, 'M002', '刘彦春', '景顺长城基金管理有限公司', '12年', 18.2000, '成长投资,消费股,医药股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund_manager` VALUES (3, 'M003', '萧楠', '易方达基金管理有限公司', '8年', 12.8000, '消费投资,白酒股,家电股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund_manager` VALUES (4, 'M004', '王宗合', '鹏华基金管理有限公司', '9年', 14.6000, '价值投资,银行股,地产股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `fund_manager` VALUES (5, 'M005', '谢治宇', '兴证全球基金管理有限公司', '11年', 16.3000, '均衡投资,科技股,消费股', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

-- ----------------------------
-- Table structure for portfolio
-- ----------------------------
DROP TABLE IF EXISTS `portfolio`;
CREATE TABLE `portfolio`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合名称',
  `portfolio_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '组合类型',
  `description` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '组合描述',
  `risk_level` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '风险等级',
  `target_return` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '目标收益率',
  `max_drawdown` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '最大回撤限制',
  `strategies` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '使用的策略（逗号分隔）',
  `asset_allocation` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '资产配置（JSON格式）',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建者',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '草稿' COMMENT '状态',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `portfolio_code`(`portfolio_code`) USING BTREE
) ENGINE = InnoDB AUTO_INCREMENT = 7 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '组合产品表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of portfolio
-- ----------------------------
INSERT INTO `portfolio` VALUES (1, 'PF001', '稳健增长组合', '混合型', '适合稳健型投资者的混合资产配置组合', '中风险', '8%', '15%', '价值投资,动量策略', '{\"股票\":60,\"债券\":30,\"货币\":10}', '张三', '活跃', '2024-01-15 10:00:00', '2024-01-15 10:00:00');
INSERT INTO `portfolio` VALUES (2, 'PF002', '积极进取组合', '股票型', '适合积极型投资者的股票配置组合', '高风险', '12%', '25%', '成长投资,量化策略', '{\"股票\":80,\"债券\":15,\"货币\":5}', '李四', '活跃', '2024-01-16 14:30:00', '2024-01-16 14:30:00');
INSERT INTO `portfolio` VALUES (3, 'PF003', '保守收益组合', '债券型', '适合保守型投资者的债券配置组合', '低风险', '5%', '8%', '久期管理,信用策略', '{\"债券\":70,\"货币\":25,\"股票\":5}', '王五', '活跃', '2024-01-17 09:15:00', '2024-01-17 09:15:00');
INSERT INTO `portfolio` VALUES (4, 'PF004', '指数增强组合', '指数型', '基于宽基指数的增强配置组合', '中风险', '10%', '18%', '指数增强,因子策略', '{\"股票\":75,\"债券\":20,\"货币\":5}', '张三', '暂停', '2024-01-18 16:45:00', '2024-01-18 16:45:00');
INSERT INTO `portfolio` VALUES (5, 'PF005', 'FOF精选组合', 'FOF型', '基金中的基金配置组合996', '中风险', '9%', '16%', '基金筛选,动态配置', '{\"FOF\":60,\"股票\":25,\"债券\":15}', '李四', '草稿', '2024-01-19 11:20:00', '2025-06-30 15:14:51');
INSERT INTO `portfolio` VALUES (6, '007', '007', '007', '007', '低风险', '12%', '15%', '', '', NULL, '活跃', '2025-06-30 15:15:30', '2025-06-30 15:15:30');
INSERT INTO `portfolio` VALUES (7, '996996', '996996', '996996', '996996', '低风险', '12%', '15%', '', '', 'admin', '活跃', '2025-06-30 15:20:46', '2025-06-30 15:20:46');

-- ----------------------------
-- Table structure for portfolio_analysis
-- ----------------------------
DROP TABLE IF EXISTS `portfolio_analysis`;
CREATE TABLE `portfolio_analysis`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `analysis_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '分析代码',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '组合名称',
  `analysis_period` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '分析周期',
  `total_return` double NULL DEFAULT NULL COMMENT '总收益率',
  `annual_return` double NULL DEFAULT NULL COMMENT '年化收益率',
  `max_drawdown` double NULL DEFAULT NULL COMMENT '最大回撤',
  `sharpe_ratio` double NULL DEFAULT NULL COMMENT '夏普比率',
  `volatility` double NULL DEFAULT NULL COMMENT '波动率',
  `beta` double NULL DEFAULT NULL COMMENT '贝塔系数',
  `alpha` double NULL DEFAULT NULL COMMENT '阿尔法系数',
  `risk_analysis` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '风险分析',
  `performance_analysis` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '绩效分析',
  `recommendations` text CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL COMMENT '建议',
  `analyst` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '分析师',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `analysis_code`(`analysis_code`) USING BTREE,
  INDEX `portfolio_code`(`portfolio_code`) USING BTREE,
  CONSTRAINT `portfolio_analysis_ibfk_1` FOREIGN KEY (`portfolio_code`) REFERENCES `portfolio` (`portfolio_code`) ON DELETE RESTRICT ON UPDATE RESTRICT
) ENGINE = InnoDB AUTO_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '组合分析表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of portfolio_analysis
-- ----------------------------
INSERT INTO `portfolio_analysis` VALUES (1, 'ANL001', 'PF001', '稳健增长组合', '1年', 8.5, 8.5, 12.3, 1.2, 15.2, 0.85, 2.1, '风险控制良好，回撤在合理范围内', '表现稳定，符合预期目标', '建议保持当前配置，关注市场变化', '张三', '2024-01-20 10:00:00', '2024-01-20 10:00:00');
INSERT INTO `portfolio_analysis` VALUES (2, 'ANL002', 'PF001', '稳健增长组合', '6个月', 4.2, 8.4, 8.7, 1.1, 14.8, 0.82, 1.8, '短期风险可控，波动率适中', '近期表现良好，超额收益稳定', '可适当增加权益配置', '张三', '2024-01-20 10:00:00', '2024-01-20 10:00:00');
INSERT INTO `portfolio_analysis` VALUES (3, 'ANL003', 'PF002', '积极进取组合', '1年', 15.8, 15.8, 22.1, 1.4, 25.6, 1.15, 3.2, '风险较高，但收益表现突出', '超额收益显著，夏普比率良好', '建议维持策略，注意风险控制', '李四', '2024-01-21 14:00:00', '2024-01-21 14:00:00');
INSERT INTO `portfolio_analysis` VALUES (4, 'ANL004', 'PF002', '积极进取组合', '3个月', 6.5, 26, 15.3, 1.3, 24.2, 1.12, 2.8, '短期波动较大，但收益可观', '季度表现优秀，动量效应明显', '可考虑增加防御性资产', '李四', '2024-01-21 14:00:00', '2024-01-21 14:00:00');
INSERT INTO `portfolio_analysis` VALUES (5, 'ANL005', 'PF003', '保守收益组合', '1年', 5.2, 5.2, 6.8, 0.9, 8.5, 0.45, 1.2, '风险极低，适合保守投资者', '收益稳定，符合预期', '建议保持配置，关注利率变化', '王五', '2024-01-22 09:00:00', '2024-01-22 09:00:00');
INSERT INTO `portfolio_analysis` VALUES (6, 'ANL006', 'PF004', '指数增强组合', '6个月', -2.1, -4.2, 18.5, 0.6, 20.1, 1.05, -1.5, '风险较高，超额收益为负', '表现不佳，需要策略调整', '建议重新评估策略有效性', '张三', '2024-01-23 16:00:00', '2024-01-23 16:00:00');

-- ----------------------------
-- Table structure for portfolio_config
-- ----------------------------
DROP TABLE IF EXISTS `portfolio_config`;
CREATE TABLE `portfolio_config`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `config_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '配置代码',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '组合名称',
  `asset_class` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '资产类别',
  `fund_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '基金代码',
  `fund_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '基金名称',
  `weight` double NULL DEFAULT NULL COMMENT '权重',
  `rebalance_rule` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '再平衡规则',
  `stop_loss_rule` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '止损规则',
  `take_profit_rule` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '止盈规则',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建者',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `config_code`(`config_code`) USING BTREE,
  INDEX `portfolio_code`(`portfolio_code`) USING BTREE,
  CONSTRAINT `portfolio_config_ibfk_1` FOREIGN KEY (`portfolio_code`) REFERENCES `portfolio` (`portfolio_code`) ON DELETE RESTRICT ON UPDATE RESTRICT
) ENGINE = InnoDB AUTO_INCREMENT = 12 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '组合配置表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of portfolio_config
-- ----------------------------
INSERT INTO `portfolio_config` VALUES (1, 'CFG001', 'PF001', '稳健增长组合', '股票', '000001', '华夏成长混合', 0.3, '季度再平衡', '单日跌幅超过5%', '累计收益超过15%', '张三', '2024-01-15 10:30:00', '2024-01-15 10:30:00');
INSERT INTO `portfolio_config` VALUES (2, 'CFG002', 'PF001', '稳健增长组合', '债券', '000002', '易方达债券A', 0.25, '季度再平衡', '单日跌幅超过2%', '累计收益超过8%', '张三', '2024-01-15 10:30:00', '2024-01-15 10:30:00');
INSERT INTO `portfolio_config` VALUES (3, 'CFG003', 'PF001', '稳健增长组合', '货币', '000003', '天弘余额宝', 0.1, '月度再平衡', '无', '无', '张三', '2024-01-15 10:30:00', '2024-01-15 10:30:00');
INSERT INTO `portfolio_config` VALUES (4, 'CFG004', 'PF002', '积极进取组合', '股票', '000004', '嘉实增长混合', 0.4, '月度再平衡', '单日跌幅超过7%', '累计收益超过20%', '李四', '2024-01-16 15:00:00', '2024-01-16 15:00:00');
INSERT INTO `portfolio_config` VALUES (5, 'CFG005', 'PF002', '积极进取组合', '股票', '000005', '富国天惠成长', 0.35, '月度再平衡', '单日跌幅超过7%', '累计收益超过20%', '李四', '2024-01-16 15:00:00', '2024-01-16 15:00:00');
INSERT INTO `portfolio_config` VALUES (6, 'CFG006', 'PF003', '保守收益组合', '债券', '000006', '工银瑞信债券', 0.45, '季度再平衡', '单日跌幅超过1%', '累计收益超过6%', '王五', '2024-01-17 09:45:00', '2024-01-17 09:45:00');
INSERT INTO `portfolio_config` VALUES (7, 'CFG007', 'PF003', '保守收益组合', '货币', '000007', '南方现金增利', 0.25, '月度再平衡', '无', '无', '王五', '2024-01-17 09:45:00', '2024-01-17 09:45:00');
INSERT INTO `portfolio_config` VALUES (10, '996', 'PF004', '996996', '996', '996', '996', 1, '996', '996', '996', NULL, '2025-06-30 15:42:15', '2025-06-30 15:42:15');
INSERT INTO `portfolio_config` VALUES (11, 'CFG1751349196800', '996996', '996996', '', '000007', '易方达货币A', 0, NULL, NULL, NULL, 'admin', '2025-07-01 13:53:16', '2025-07-01 13:53:16');
INSERT INTO `portfolio_config` VALUES (12, 'CFG1751509984612', '996996', '996996', '', '000002', '易方达消费行业股票', 0, NULL, NULL, NULL, 'admin', '2025-07-03 10:33:04', '2025-07-03 10:33:04');

-- ----------------------------
-- Table structure for portfolio_monitor
-- ----------------------------
DROP TABLE IF EXISTS `portfolio_monitor`;
CREATE TABLE `portfolio_monitor`  (
  `id` bigint NOT NULL AUTO_INCREMENT,
  `monitor_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '监控代码',
  `portfolio_code` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NOT NULL COMMENT '组合代码',
  `portfolio_name` varchar(100) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '组合名称',
  `monitor_type` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '监控类型',
  `alert_condition` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '预警条件',
  `alert_threshold` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '预警阈值',
  `alert_action` varchar(200) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '预警动作',
  `current_value` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '当前值',
  `status` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT '活跃' COMMENT '监控状态',
  `creator` varchar(50) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建者',
  `create_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '创建时间',
  `update_time` varchar(20) CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci NULL DEFAULT NULL COMMENT '更新时间',
  PRIMARY KEY (`id`) USING BTREE,
  UNIQUE INDEX `monitor_code`(`monitor_code`) USING BTREE,
  INDEX `portfolio_code`(`portfolio_code`) USING BTREE,
  CONSTRAINT `portfolio_monitor_ibfk_1` FOREIGN KEY (`portfolio_code`) REFERENCES `portfolio` (`portfolio_code`) ON DELETE RESTRICT ON UPDATE RESTRICT
) ENGINE = InnoDB AUTO_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '组合监控表' ROW_FORMAT = Dynamic;
