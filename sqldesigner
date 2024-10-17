-- ---
-- Globals
-- ---

-- SET SQL_MODE="NO_AUTO_VALUE_ON_ZERO";
-- SET FOREIGN_KEY_CHECKS=0;

-- ---
-- Table 'CULTURAS'
-- 
-- ---

DROP TABLE IF EXISTS `CULTURAS`;
		
CREATE TABLE `CULTURAS` (
  `ID_culturas` INTEGER NULL DEFAULT NULL,
  `tipo_planta` VARCHAR(32) NULL DEFAULT NULL,
  `tipo_solo` VARCHAR(32) NULL DEFAULT NULL,
  `qtd_agua_mensal` DOUBLE NULL DEFAULT NULL,
  `ph_ideal` DOUBLE NULL DEFAULT NULL,
  `qtd_fosforo_mensal` DOUBLE NULL DEFAULT NULL,
  `qtd_potassio_mensal` DOUBLE NULL DEFAULT NULL,
  `qtd_npk_mensal` VARCHAR NULL DEFAULT NULL,
  PRIMARY KEY (`ID_culturas`)
);

-- ---
-- Table 'SENSORES'
-- 
-- ---

DROP TABLE IF EXISTS `SENSORES`;
		
CREATE TABLE `SENSORES` (
  `ID_sensor` INTEGER NULL DEFAULT NULL,
  `tipo_sensor` VARCHAR(16) NULL DEFAULT NULL,
  `localizacao_sensor` VARCHAR(32) NULL DEFAULT NULL,
  `data_instalacao` DATE NULL DEFAULT NULL,
  PRIMARY KEY (`ID_sensor`)
);

-- ---
-- Table 'LEITURA_SENSOR'
-- 
-- ---

DROP TABLE IF EXISTS `LEITURA_SENSOR`;
		
CREATE TABLE `LEITURA_SENSOR` (
  `ID_leitura` INTEGER NULL AUTO_INCREMENT DEFAULT NULL,
  `ID_sensor_SENSORES` INTEGER NULL DEFAULT NULL,
  `valor_leitura` DOUBLE NULL DEFAULT NULL,
  `hora_leitura` TIME NULL DEFAULT NULL,
  `data_leitura` DATE NULL DEFAULT NULL,
  PRIMARY KEY (`ID_leitura`)
);

-- ---
-- Table 'AJUSTES'
-- 
-- ---

DROP TABLE IF EXISTS `AJUSTES`;
		
CREATE TABLE `AJUSTES` (
  `ID_ajuste` INTEGER NULL AUTO_INCREMENT DEFAULT NULL,
  `ID_plantacao_PLANTACAO` INTEGER NULL DEFAULT NULL,
  `ID_culturas_CULTURAS` INTEGER NULL DEFAULT NULL,
  `ID_leitura_LEITURA_SENSOR` INTEGER NULL DEFAULT NULL,
  `data_ajuste` TIME NULL DEFAULT NULL,
  `hora_ajuste` TIME NULL DEFAULT NULL,
  `agua_ajuste` DOUBLE NULL DEFAULT NULL,
  `ph_ajuste` DOUBLE NULL DEFAULT NULL,
  `fosforo_ajuste` DOUBLE NULL DEFAULT NULL,
  `potassio_ajuste` DOUBLE NULL DEFAULT NULL,
  `npk_ajuste` DOUBLE NULL DEFAULT NULL,
  PRIMARY KEY (`ID_ajuste`)
);

-- ---
-- Table 'RELATORIO'
-- 
-- ---

DROP TABLE IF EXISTS `RELATORIO`;
		
CREATE TABLE `RELATORIO` (
  `ID_relatorio` INTEGER NULL AUTO_INCREMENT DEFAULT NULL,
  `ID_culturas_CULTURAS` INTEGER NULL DEFAULT NULL,
  `ID_plantacao_PLANTACAO` INTEGER NULL DEFAULT NULL,
  `ID_ajuste_AJUSTES` INTEGER NULL DEFAULT NULL,
  PRIMARY KEY (`ID_relatorio`)
);

-- ---
-- Table 'PLANTACAO'
-- 
-- ---

DROP TABLE IF EXISTS `PLANTACAO`;
		
CREATE TABLE `PLANTACAO` (
  `ID_plantacao` INTEGER NULL AUTO_INCREMENT DEFAULT NULL,
  `ID_culturas_CULTURAS` INTEGER NULL DEFAULT NULL,
  `agua_consumida` DOUBLE NULL DEFAULT NULL,
  `ph_atual` DOUBLE NULL DEFAULT NULL,
  `fosforo_consumido` DOUBLE NULL DEFAULT NULL,
  `potassio_consumido` INTEGER NULL DEFAULT NULL,
  `npk_consumido` INTEGER NULL DEFAULT NULL,
  PRIMARY KEY (`ID_plantacao`)
);

-- ---
-- Foreign Keys 
-- ---

ALTER TABLE `LEITURA_SENSOR` ADD FOREIGN KEY (ID_sensor_SENSORES) REFERENCES `SENSORES` (`ID_sensor`);
ALTER TABLE `AJUSTES` ADD FOREIGN KEY (ID_plantacao_PLANTACAO) REFERENCES `PLANTACAO` (`ID_plantacao`);
ALTER TABLE `AJUSTES` ADD FOREIGN KEY (ID_culturas_CULTURAS) REFERENCES `CULTURAS` (`ID_culturas`);
ALTER TABLE `AJUSTES` ADD FOREIGN KEY (ID_leitura_LEITURA_SENSOR) REFERENCES `LEITURA_SENSOR` (`ID_leitura`);
ALTER TABLE `RELATORIO` ADD FOREIGN KEY (ID_culturas_CULTURAS) REFERENCES `CULTURAS` (`ID_culturas`);
ALTER TABLE `RELATORIO` ADD FOREIGN KEY (ID_plantacao_PLANTACAO) REFERENCES `PLANTACAO` (`ID_plantacao`);
ALTER TABLE `RELATORIO` ADD FOREIGN KEY (ID_ajuste_AJUSTES) REFERENCES `AJUSTES` (`ID_ajuste`);
ALTER TABLE `PLANTACAO` ADD FOREIGN KEY (ID_culturas_CULTURAS) REFERENCES `CULTURAS` (`ID_culturas`);

-- ---
-- Table Properties
-- ---

-- ALTER TABLE `CULTURAS` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `SENSORES` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `LEITURA_SENSOR` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `AJUSTES` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `RELATORIO` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;
-- ALTER TABLE `PLANTACAO` ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin;

-- ---
-- Test Data
-- ---

-- INSERT INTO `CULTURAS` (`ID_culturas`,`tipo_planta`,`tipo_solo`,`qtd_agua_mensal`,`ph_ideal`,`qtd_fosforo_mensal`,`qtd_potassio_mensal`,`qtd_npk_mensal`) VALUES
-- ('','','','','','','','');
-- INSERT INTO `SENSORES` (`ID_sensor`,`tipo_sensor`,`localizacao_sensor`,`data_instalacao`) VALUES
-- ('','','','');
-- INSERT INTO `LEITURA_SENSOR` (`ID_leitura`,`ID_sensor_SENSORES`,`valor_leitura`,`hora_leitura`,`data_leitura`) VALUES
-- ('','','','','');
-- INSERT INTO `AJUSTES` (`ID_ajuste`,`ID_plantacao_PLANTACAO`,`ID_culturas_CULTURAS`,`ID_leitura_LEITURA_SENSOR`,`data_ajuste`,`hora_ajuste`,`agua_ajuste`,`ph_ajuste`,`fosforo_ajuste`,`potassio_ajuste`,`npk_ajuste`) VALUES
-- ('','','','','','','','','','','');
-- INSERT INTO `RELATORIO` (`ID_relatorio`,`ID_culturas_CULTURAS`,`ID_plantacao_PLANTACAO`,`ID_ajuste_AJUSTES`) VALUES
-- ('','','','');
-- INSERT INTO `PLANTACAO` (`ID_plantacao`,`ID_culturas_CULTURAS`,`agua_consumida`,`ph_atual`,`fosforo_consumido`,`potassio_consumido`,`npk_consumido`) VALUES
-- ('','','','','','','');
