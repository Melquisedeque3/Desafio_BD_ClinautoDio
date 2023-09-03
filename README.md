# Desafio_BD_ClinautoDio
Entrega do desafio do curso Potência Tech powered by iFood | Ciência de Dados - Modelagem de dados

============================== Entendendo o cenário ==============================

-- A ideia é criar uma oficina de serviços automotivos que tenha a melhor interação com os clientes fazendo a manutenão em carros de forma agil, eficiente proporcionando ao 
cliente a melhor experiência possível. Esses objetivos são mensuradoe e atingidos atravéz do uso de tecnologias que proporcionam a melhor tomada de decisão com base nos dados.

1 - Ao chegar na oficina, o cliente é identificado por câmeras de segurança que ao lê a placa do carro inicia a seguinte rotina:

  1.1 Cliente não cadastrado:
	
   * Manobrista conduz o cliente ao setor administrativo onde será feiro o devido cadastro e verificação do serviço a ser feito,
  1.2 Cliente caastrado:
     
   * Manobrista colhe informação do serviço, passa ao cliente uma estimativa de tempo da entrega do veículo e o conduz a sala de espera enquanto o carro é levado para manutenção.
     
  1.3 Cliente cadastrado e agendado:
    
   * Manobrista conduz cliente a sala de espera e o carro vai para setor de manutenção, nesse caso, no agendamento (site ou alicativo da ofcina) já foi passado ao cliente o tempo de espera a depender do serviço que será realizado.
     
  1.4 Serviços móveis:
	
   * Ainda é possível fazer atendimentos fora da oficina:
      
      1º caso - Manobrista pega e leva o carro na casa do cliente
     
      2º caso - Equipe móvel faz serviços rápidos na casa do cliente, ou no local que o carro der defeito.

-- Na oficina, o gerente controla a demanda de serviço mantendo 20% dos mecânicos em alerta para serviços de cliente não agendados e o restante, atendendo aos casos já agendados.

-- Todos os dados são coletados através do cadastro do cliente presencialmente na oficina, no site/App da oficina.

=================================== Criando o Banco de dados =================================

-- Observando o cenário acima citado, criei um esborço com as seguintes tabelas:

* Cliente:
	
 IdCliente VARCHAR (30) 

 CPF VARCHAR (11) 

 Cel VARCHAR (10) 

 Endereço VARCHAR (40) 

 CarroIdNome 

* Carro:

IdCarro VARCHAR (10)
	
Marca VARCHAR (10)
	
Modelo VARCHAR (10)
	 
Ano INT
	
Cor VARCHAR (10)
	 
FOREY KEY  

* Serviço:

IdServico

Tipo  VARCHAR (30)

Descrição VARCHAR (60)

Tempo FLOAT

Valor FLOAT 

* OS:

IdNome

CarroIdNome

Garantia  VARCHAR (15)

* Equipe:

IdCargo

Setor VARCHAR (15)

Cargo  VARCHAR (20)

* Pagamento:

-- Fiz algumas alterações incerindo na tabela OS as chaves primárias CliensteIdCliente e CarroIdCarro para poder fazer as devidas consultas com SQL.



IdPagamento

Valor FLOAT

F.Pagamento ENUM ()Dinheiro/Cartão)/PIX 

=============================== Testando Banco ===============================
-- Criei algumas consultas básicas para observar como o banco se comportava, após 
algumas alterações para corrigir as chaves estrangeiras, as consultas funcionaram 
melhor do que esperado.
=============================== Consultas ===================================
-- Carro-> Cliente
SELECT Cliente.Nome AS NomeCliente, Carro.Modelo AS ModeloCarro
FROM OS
JOIN Cliente ON OS.ClienteIdCliente = Cliente.IdCliente
JOIN Carro ON OS.CarroIdCarro = Carro.IdCarro;

Onix - Jair Mesias
Acord - João Doria
Belina - Pablo Vitar
Fusca - Dj Kevinho
Corolla - Marina Silva
-- Carro-> Cliente -> Servico
SELECT Cliente.Nome AS NomeCliente, Carro.Modelo AS ModeloCarro, Servico.Descricao AS Servico
FROM OS
JOIN Cliente ON OS.ClienteIdCliente = Cliente.IdCliente
JOIN Carro ON OS.CarroIdCarro = Carro.IdCarro
JOIN Servico ON OS.IdServico = Servico.IdServico;

Jair Mesias - Onix - Reparo
João Doria - Acord - Substituição de peça
Pablo Vitar - Belina - Retoque
Dj Kevinho - Fusca - Substituição de peça
Marina Silva - Corolla - Substituição de peça
-- Cliente e carro ->  Modelo e Cor -> Seriço e Preço
SELECT Cliente.Nome AS NomeCliente, Cliente.CPF AS CPF, 
Carro.Modelo AS ModeloCarro, Carro.Cor AS Cor,
Servico.Descricao AS Servico, Servico.Valor AS Preço
FROM OS
JOIN Cliente ON OS.ClienteIdCliente = Cliente.IdCliente
JOIN Carro ON OS.CarroIdCarro = Carro.IdCarro
JOIN Servico ON OS.IdServico = Servico.IdServico;

Jair Mesias - 12345678903 - Onix - Branco - Reparo - 70.1
João Doria - 12345678902 - Acord - Vermelho - Substituição de peça - 100
Pablo Vitar - 12345678906 - Belina - P.fosco - Retoque - 300
Dj Kevinho - 12345678905 - Fusca - Pretinho - Substituição de peça - 325
Marina Silva - 12345678901 - Corolla - Branco - Substituição de peça - 3.05 

================================ Considerações ==================================
-- Acredito ter cumprido todos os requisitos do  desafio, os conhecimenos adiquiridos 
valeram cada tentativa frustrada, erro de nas intruções SQL, programas que não funcionaram,
enfim, todo trabalho foi ecompensado com o resultado encontrado. Fico a disposição para dúvidas, sugestões ou demais contatos.


== Melquisedeque Oliveira =======================================================
