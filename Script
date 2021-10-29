USE EstrelaDaMorte

CREATE TABLE Planetas(
	IdPlaneta int NOT NULL,
	Nome varchar(50) NOT NULL,
	Rotacao float NOT NULL,
	Orbita float NOT NULL,
	Diametro float NOT NULL,
	Clima varchar(50) NOT NULL,
	Populacao int NOT NULL
)
GO -- indicar que o final de uma instrução e começo de outro
ALTER TABLE Planetas ADD CONSTRAINT PK_Planetas  PRIMARY KEY (IdPlaneta);

CREATE TABLE Naves(
	IdNave int NOT NULL,
	Nome varchar(100) NOT NULL,
	Modelo varchar(150) NOT NULL,
	Passageiros int NOT NULL,
	Carga float NOT NULL,
	Classe varchar(100) NOT NULL
)
GO
ALTER TABLE Naves ADD CONSTRAINT PK_Naves PRIMARY KEY (IdNave);

CREATE TABLE Pilotos(
	IdPiloto int NOT NULL,
	Nome varchar(200) NOT NULL,
	AnoNascimento varchar(150) NOT NULL,
	IdPlaneta int NOT NULL,
)
GO 
ALTER TABLE Pilotos ADD CONSTRAINT PK_Piloto PRIMARY KEY (IdPiloto);
GO
ALTER TABLE Pilotos ADD CONSTRAINT FK_Pilotos_Planetas FOREIGN KEY (IdPlaneta) --padrão de ir da onde você ta vindo para onde ta indo
REFERENCES Planetas (IdPlaneta)

CREATE TABLE PilotosNaves(
	IdPiloto int NOT NULL,
	IdNave int NOT NULL,
	FlagAutorizado bit NOT NULL
)
GO
ALTER TABLE PilotosNaves ADD CONSTRAINT PK_PilotosNaves PRIMARY KEY(IdPiloto, IdNave);
GO
ALTER TABLE PilotosNaves ADD CONSTRAINT FK_PilotosNaves_Pilotos FOREIGN KEY(IdPiloto)
REFERENCES Pilotos (IdPiloto)
GO
ALTER TABLE PilotosNaves ADD CONSTRAINT FK_PilotosNaves_Naves FOREIGN KEY (IdNave)
REFERENCES Naves (IdNave)
GO
ALTER TABLE PilotosNaves ADD CONSTRAINT DF_PilotosNaves_FlagAutorizado DEFAULT (1) FOR  FlagAutorizado -- primeira vez que inserir um registro ele será por padrão 1(true)

CREATE TABLE HistoricoViagens(
	IdNave int NOT NULL,
	IdPiloto int NOT NULL,
	DtSaida datetime NOT NULL,
	DtChegada datetime NULL -- Como a chegada só ocorre após um periodo ele deve aceitar nulo
)
GO

ALTER TABLE HistoricoViagens ADD CONSTRAINT FK_HistoricoViagens_PilotosNaves FOREIGN KEY (IdPiloto, IdNave)
REFERENCES PilotosNaves (IdPiloto, IdNave)
GO
ALTER TABLE HistoricoViagens CHECK CONSTRAINT FK_HistoricoViagens_PilotosNaves -- checkar se os registros estao sendo garantidos
