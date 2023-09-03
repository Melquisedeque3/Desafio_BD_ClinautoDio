# Desafio_BD_ClinautoDio
Entrega do desafio do curso Potência Tech powered by iFood | Ciência de Dados - Modelagem de dados

======================================= Entendendo o cenário ======================================

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

=================================== Criando o Banco de dados ===================================

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

=================================== ===================================
