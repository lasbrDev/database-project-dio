CREATE SCHEMA IF NOT EXISTS `universidade_db` DEFAULT CHARACTER SET utf8;

USE `universidade_db`;

-- Tabela enderecos
CREATE TABLE IF NOT EXISTS `enderecos` (
  `id_endereco` INT NOT NULL AUTO_INCREMENT,
  `logradouro` VARCHAR(100) NOT NULL,
  `numero` INT NOT NULL,
  `cep` VARCHAR(10) NOT NULL,
  `bairro` VARCHAR(45) NOT NULL,
  `cidade` VARCHAR(45) NOT NULL,
  `uf` CHAR(2) NOT NULL,
  PRIMARY KEY (`id_endereco`)
) ENGINE = InnoDB;

-- Tabela pessoas
CREATE TABLE IF NOT EXISTS `pessoas` (
  `id_pessoa` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(100) NOT NULL,
  `email` VARCHAR(100) NOT NULL,
  `endereco_id_endereco` INT NOT NULL,
  PRIMARY KEY (`id_pessoa`),
  INDEX `fk_pessoas_enderecos_idx` (`endereco_id_endereco` ASC),
  CONSTRAINT `fk_pessoas_enderecos`
    FOREIGN KEY (`endereco_id_endereco`)
    REFERENCES `enderecos` (`id_endereco`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION
) ENGINE = InnoDB;

-- Tabela alunos
CREATE TABLE IF NOT EXISTS `alunos` (
  `id_aluno` INT NOT NULL AUTO_INCREMENT,
  `matricula` VARCHAR(45) NOT NULL,
  `pessoa_id_pessoa` INT NOT NULL,
  PRIMARY KEY (`id_aluno`),
  INDEX `fk_alunos_pessoas_idx` (`pessoa_id_pessoa` ASC),
  CONSTRAINT `fk_alunos_pessoas`
    FOREIGN KEY (`pessoa_id_pessoa`)
    REFERENCES `pessoas` (`id_pessoa`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION
) ENGINE = InnoDB;

-- Tabela professores
CREATE TABLE IF NOT EXISTS `professores` (
  `id_professor` INT NOT NULL AUTO_INCREMENT,
  `registro` VARCHAR(45) NOT NULL,
  `pessoa_id_pessoa` INT NOT NULL,
  PRIMARY KEY (`id_professor`),
  INDEX `fk_professores_pessoas_idx` (`pessoa_id_pessoa` ASC),
  CONSTRAINT `fk_professores_pessoas`
    FOREIGN KEY (`pessoa_id_pessoa`)
    REFERENCES `pessoas` (`id_pessoa`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION
) ENGINE = InnoDB;

-- Tabela departamentos
CREATE TABLE IF NOT EXISTS `departamentos` (
  `id_departamento` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(45) NOT NULL,
  `campus` VARCHAR(45) NOT NULL,
  `professor_coordenador_id` INT NOT NULL,
  PRIMARY KEY (`id_departamento`),
  INDEX `fk_departamentos_professores_idx` (`professor_coordenador_id` ASC),
  CONSTRAINT `fk_departamentos_professores`
    FOREIGN KEY (`professor_coordenador_id`)
    REFERENCES `professores` (`id_professor`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION
) ENGINE = InnoDB;

-- Tabela cursos
CREATE TABLE IF NOT EXISTS `cursos` (
  `id_curso` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(45) NOT NULL,
  `departamento_id` INT NOT NULL,
  PRIMARY KEY (`id_curso`),
  INDEX `fk_cursos_departamentos_idx` (`departamento_id` ASC),
  CONSTRAINT `fk_cursos_departamentos`
    FOREIGN KEY (`departamento_id`)
    REFERENCES `departamentos` (`id_departamento`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION
) ENGINE = InnoDB;

-- Tabela disciplinas
CREATE TABLE IF NOT EXISTS `disciplinas` (
  `id_disciplina` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(100) NOT NULL,
  PRIMARY KEY (`id_disciplina`)
) ENGINE = InnoDB;

-- Tabela periodo
CREATE TABLE IF NOT EXISTS `periodos` (
  `id_periodo` INT NOT NULL AUTO_INCREMENT,
  `ano` VARCHAR(45) NULL,
  `semestre` VARCHAR(45) NULL,
  PRIMARY KEY (`id_periodo`)
) ENGINE = InnoDB;

-- Tabela oferta_disciplinas
CREATE TABLE IF NOT EXISTS `oferta_disciplinas` (
  `periodo_id_periodo` INT NOT NULL,
  `disciplina_id_disciplina` INT NOT NULL,
  `professor_id_professor` INT NOT NULL,
  PRIMARY KEY (`periodo_id_periodo`, `disciplina_id_disciplina`, `professor_id_professor`),
  INDEX `fk_oferta_disciplinas_periodos_idx` (`periodo_id_periodo` ASC),
  INDEX `fk_oferta_disciplinas_disciplinas_idx` (`disciplina_id_disciplina` ASC),
  INDEX `fk_oferta_disciplinas_professores_idx` (`professor_id_professor` ASC),
  CONSTRAINT `fk_oferta_disciplinas_periodos`
    FOREIGN KEY (`periodo_id_periodo`)
    REFERENCES `periodos` (`id_periodo`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_oferta_disciplinas_disciplinas`
    FOREIGN KEY (`disciplina_id_disciplina`)
    REFERENCES `disciplinas` (`id_disciplina`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_oferta_disciplinas_professores`
    FOREIGN KEY (`professor_id_professor`)
    REFERENCES `professores` (`id_professor`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION
) ENGINE = InnoDB;

-- Tabela aluno_matriculado_curso
CREATE TABLE IF NOT EXISTS `alunos_matriculados_cursos` (
  `aluno_id_aluno` INT NOT NULL,
  `curso_id_curso` INT NOT NULL,
  PRIMARY KEY (`aluno_id_aluno`, `curso_id_curso`),
  INDEX `fk_alunos_matriculados_cursos_alunos_idx` (`aluno_id_aluno` ASC),
  INDEX `fk_alunos_matriculados_cursos_cursos_idx` (`curso_id_curso` ASC),
  CONSTRAINT `fk_alunos_matriculados_cursos_alunos`
    FOREIGN KEY (`aluno_id_aluno`)
    REFERENCES `alunos` (`id_aluno`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_alunos_matriculados_cursos_cursos`
    FOREIGN KEY (`curso_id_curso`)
    REFERENCES `cursos` (`id_curso`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION
) ENGINE = InnoDB;

-- Tabela extensao
CREATE TABLE IF NOT EXISTS `extensoes` (
  `id_extensao` INT NOT NULL AUTO_INCREMENT,
  `nome` VARCHAR(100) NOT NULL,
  `area` VARCHAR(100) NOT NULL,
  `instituicao` VARCHAR(100) NOT NULL,
  PRIMARY KEY (`id_extensao`)
) ENGINE = InnoDB;

-- Tabela extensao_has_aluno
CREATE TABLE IF NOT EXISTS `extensoes_has_alunos` (
  `extensao_id_extensao` INT NOT NULL,
  `aluno_id_aluno` INT NOT NULL,
  PRIMARY KEY (`extensao_id_extensao`, `aluno_id_aluno`),
  INDEX `fk_extensoes_has_alunos_extensoes_idx` (`extensao_id_extensao` ASC),
  INDEX `fk_extensoes_has_alunos_alunos_idx` (`aluno_id_aluno` ASC),
  CONSTRAINT `fk_extensoes_has_alunos_extensoes`
    FOREIGN KEY (`extensao_id_extensao`)
    REFERENCES `extensoes` (`id_extensao`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_extensoes_has_alunos_alunos`
    FOREIGN KEY (`aluno_id_aluno`)
    REFERENCES `alunos` (`id_aluno`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION
) ENGINE = InnoDB;

-- Tabela financeiro
CREATE TABLE IF NOT EXISTS `financeiro` (
  `id_financeiro` INT NOT NULL AUTO_INCREMENT,
  `tipo` ENUM('Mensalidade', 'Salario') NOT NULL,
  `valor` DECIMAL(10, 2) NOT NULL,
  `pessoa_id` INT NOT NULL,
  PRIMARY KEY (`id_financeiro`),
  INDEX `fk_financeiro_pessoas_idx` (`pessoa_id` ASC),
  CONSTRAINT `fk_financeiro_pessoas`
    FOREIGN KEY (`pessoa_id`)
    REFERENCES `pessoas` (`id_pessoa`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION
) ENGINE = InnoDB;

-- Tabela Pre_Requisitos
CREATE TABLE IF NOT EXISTS `pre_requisitos` (
  `pre_requisitos_id` INT NOT NULL,
  PRIMARY KEY (`pre_requisitos_id`)
) ENGINE = InnoDB;

-- Tabela Pre_Requisitos_Disciplinas
CREATE TABLE IF NOT EXISTS `pre_requisitos_disciplinas` (
  `disciplina_id` INT NOT NULL,
  `pre_requisitos_id` INT NOT NULL,
  PRIMARY KEY (`disciplina_id`, `pre_requisitos_id`),
  INDEX `fk_pre_requisitos_disciplinas_pre_requisitos_idx` (`pre_requisitos_id` ASC),
  INDEX `fk_pre_requisitos_disciplinas_disciplinas_idx` (`disciplina_id` ASC),
  CONSTRAINT `fk_pre_requisitos_disciplinas_disciplinas`
    FOREIGN KEY (`disciplina_id`)
    REFERENCES `disciplinas` (`id_disciplina`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_pre_requisitos_disciplinas_pre_requisitos`
    FOREIGN KEY (`pre_requisitos_id`)
    REFERENCES `pre_requisitos` (`pre_requisitos_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION
) ENGINE = InnoDB;