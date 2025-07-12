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
) ENGINE = InnoDB AUTO_INCREMENT = 6 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '交易监控表' ROW_FORMAT = Dynamic;

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
) ENGINE = InnoDB AUTO_INCREMENT = 7 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci COMMENT = '交易订单表' ROW_FORMAT = Dynamic;

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
) ENGINE = InnoDB AUTO_INCREMENT = 4 CHARACTER SET = utf8mb4 COLLATE = utf8mb4_0900_ai_ci COMMENT = '用户表' ROW_FORMAT = Dynamic;

-- ----------------------------
-- Records of user
-- ----------------------------
INSERT INTO `user` VALUES (1, 'admin', '123456', 'admin@example.com', '13800138000', '管理员', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `user` VALUES (2, 'user1', '123456', 'user1@example.com', '13800138001', '张三', '2024-01-01 00:00:00', '2024-01-01 00:00:00');
INSERT INTO `user` VALUES (3, 'user2', '123456', 'user2@example.com', '13800138002', '李四', '2024-01-01 00:00:00', '2024-01-01 00:00:00');

SET FOREIGN_KEY_CHECKS = 1;
