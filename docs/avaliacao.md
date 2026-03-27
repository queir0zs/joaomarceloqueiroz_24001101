# Avaliação — Engenharia de Software
**Sistema Integrado de Gestão de Farmácia — MVP Definido pelo Estudante**

Aluno: João Marcelo Queiroz Caldas
RA: 24001101
Data: 26/03/2026

---

# 1. Definição do MVP 
Explique claramente: Meu MVP cobre o processo de vendas integrado ao controle basico de estoque e cadastro de clientes.

- Dentro: Registro de vendas, consulta de produtos, verificar estoque, cadastro de cada cliente, geração de notas, emissão de comprovantes e atualização automatica de estoque.
- Fora: Compras com os fornecedores, contas a pagar, controle de usuario e relátorios privados.
- Escolhi isso por esse processo é o nucleo de funcionamnto da gestão de uma farmácia, e envolve integração com estoque e financeiro.

> Meu MVP serve a principio para um gerenciamento facil de vendas de balcao, muito util para uma farmacia desde de a seleção do produto até a finalização da compra.

---

# 2. Regras de Negócio (mínimo: 5)
Liste e descreva **cada RN** de forma clara.

**RN01 — Venda somento com estoque disponivel**
O sistema não deve permitir compra se não houver a quantidade desejada no estoque

**RN02 — Cadastro obrigatorio para certas medicações**  
Clientes devem estar cadastrados para retirar certos produtos especificos

**RN03 — Atualização automatica de estoque a todo momento**  
Após a realização de uma compra o estoque deve automaticamente alterar a quantidade em estoque

**RN04 — Geração automatica de contas a receber**  
Vendas a prazo devem gerar registros financeiros automaticamente

**RN05 — Produto deve existir no sistema**  
O sistema não ira permitir a venda de produtos caso ele não esteja cadastrado no sistema


---

# 3. Requisitos Funcionais (mínimo: 8)
Liste os requisitos funcionais do seu MVP.

**RF01 — Cadastro de clientes**  
**RF02 — Consultar cliente**  
**RF03 — Consultar produto no estoque**  
**RF04 — Registrar toda venda**  
**RF05 — verificar estoque automaticamente**  
**RF06 — Gerar contas a receber**  
**RF07 — Emitir comprovante de venda**  
**RF08 — Atualizar o estoque a todo momento automaticamente**
**RF09 — Validar receita medicas para certas medicações**  

---

# 🛡 4. Requisitos Não Funcionais (mínimo: 4)
Liste os RNFs do sistema conforme seu MVP.

**RNF01 — Desempenho do sistema**
O sistema deve responder em até 3 segundos

**RNF02 — Segurança do sistema**
Apenas usuarios com autorização podem acessar funcionabilidades específicas do sistema

**RNF03 — Confiabilidade** 
O sistema deve garantir certa segurança de dados de vendas e do estoque da farmacia

**RNF04 — Discponibilidade do sistema**
O sistema deve estar disponivel a todo momento enquanto a farmacia estiver funcionando

**RNF05 — Usabilidade simples**
O sistema deve ser simples e intuitivo para todos os atendentes
---

# 5. Casos de Uso (mínimo: 10)
UC01 - Realizar vendas,
UC02 - Consutlar produto,
UC03 - Verificar estoque,
UC04 - Cadastrar cliente,
UC05 - identificação de cliente,
UC06 - registrar vendas a longo prazo,
UC07 - Gerar contas a receber,
UC08 - Emitir comprovantes,
UC09 - Validar receitas,
UC10 - Atualização de estoque,
-----------------------------------------------------

**- relação entre atores e os casos de uso:**
**Atendente interage com:**
  UC01 - Realizar venda
  UC02 - Consultar produtos
  UC04 - Cadastrar clientes
  UC05 - identificação de clientes
  UC06 - Registar vendas a prazo

**Farmaceutico interage com:**
  UC09 - VAlidar receita

**Sistema interage com:**
  UC03 - Verificar estoque 
  UC07 - Gerar contas a receber
  UC08 - Emitir comprovantes
  UC10 - Atualizar estoque

**Includes:**
- Realizar venda -> Consultar produto
- Realizar venda -> Verificar estoque
- Realizar venda -> Emitir comprovante

**Extends:**
- Realizar venda -> Cadastrar cliente
- Realizar venda -> Registar venda a prazo
- Realizar venda -> Validar receitas


---

# 6. Documentação dos Casos de Uso
Para **cada caso de uso**, utilize o template abaixo:
---

## **UC01 — Realizar vendas**
**Ator(es): Atendente**  
**Descrição: Registar venda de prondutos ao cliente**  
**Pré-condições: Produto Cadastrado**  
**Pós-condições: Venda Registrada no sistema e estoque atualizado **

**Fluxo**
- Atendente inicia venda
- Sistema solicita produto
- Atendente informa o produto
- sistema verifica se há produto no sistema
- Atendente confirma venda
- Sistema finaliza venda

**Exceçoes**
-FA01 -> Produto sem estoque
-FA02 -> Cliente não cadastrado no sistema

**Include**
-Consultar produto

**Extend**
-Cadastrar cliente


## **UC02 — Consutlar produto**
**Ator(es): Atendente**  
**Descrição: Atendente busca produto no sistema**  
**Pré-condições: Sistema ativo**  
**Pós-condições: Produto exibido**  

**Fluxo**
- Atendente informa codigo do produto
- Sistema Busca produto
- Sistema exibe resultado dos produtos

**Exceçoes**
-FA01 -> Produto não encontrado no sistema
-FA02 -> Falha na busca de sistema

**Include**
- Verificar estoque

**Extend**
- Realizar venda

## **UC03 — Verificar estoque**
**Ator(es): Sistema**  
**Descrição: Verifica se há produto no sistema**  
**Pré-condições: Produto informado**  
**Pós-condições: Quantidade exibida no estoque** 

**Fluxo**
- Sistema consulta o estoque
- Sistema retorna a quantidade disponivel no estoque

**Exceçoes**
-FA01 -> Estoque insulficiente
-FA02 -> Produto inexistente no estoque

**Include**
-Consultar produto

**Extend**
-Realizar venda

## **UC04 — Cadastrar cliente**
**Ator(es): Atendente **  
**Descrição: Registrar novo cliente no sistema**  
**Pré-condições: Cliente não cadastrado no sistema**  
**Pós-condições: Dados de cliente salvo no sistema**  

**Fluxo**
- Atendente informa dados do cliente
- sistema validade informações
- sistema cria cadastro do cliente

**Exceçoes**
-FA01 -> Dados invalidade
-FA02 -> Cliente já cadastrado no sistema

**Include**
-Identificar cliente 

**Extend**
-Realizar venda

## **UC05 — identificação de cliente**
**Ator(es): Atendente**  
**Descrição: Localizar o cliente para associar a venda**  
**Pré-condições: Cliente existente no sistema**  
**Pós-condições: Cliente identificado**  

**Fluxo**
- Atendente informa nome ou CPF do cliente
- Sistema busca informações do cliente
- Sistema exibe dados do cliente

**Exceçoes**
-FA01 -> Cliente não encontrado
-FA02 -> Erro na consulta

**Include**
-Consultar produto

**Extend**
-Realizar venda


## **UC06 — registrar vendas a longo prazo**
**Ator(es): Atendente**  
**Descrição: Registrar venda com pagamentos futuros**  
**Pré-condições: Cliente cadastrado no sistema**  
**Pós-condições: Venda registrada como conta a receber** 

**Fluxo**
- Atendente seleciona venda a prazo
- sistema solicita dados de pagamento
- atendente informa vencimento
- sistema confirma venda a longo prazo

**Exceçoes**
-FA01 -> Cliente não cadastrado no sistema
-FA02 -> Data de vencimento invalida

**Include**
-Gerar conta a receber

**Extend**
-Realizar venda

## **UC07 — Gerar contas a receber**
**Ator(es): Sistema**  
**Descrição: Criar registro financeiro da venda a prazo**  
**Pré-condições: venda a prazo realizada**  
**Pós-condições: contra registrada no sistema** 

**Fluxo**
- Sistema recebe dados de venda
- sistema gera conta a receber
- sistema define vencimento e status da conta

**Exceçoes**
-FA01 -> Erro ao registrar conta a longo prazo
-FA02 -> Dados financeiros invalidos

**Include**
-registrar venda a prazo

**Extend**
-Emitir comprovante

## **UC08 — Emitir comprovantes**
**Ator(es): Sistema**  
**Descrição: Gerar comprovante de venda**  
**Pré-condições: Venda finalizada**  
**Pós-condições: Comprovante emitido**  

**Fluxo**
- Sistema gera comprovante
- Sistema exibe comprovante para impressão

**Exceçoes**
-FA01 -> Erro na emissão do comprovante
-FA02 -> Impressora indisponivel

**Include**
-Realizar venda

**Extend**
-Atualizar estoque

## **UC09 — Validar receitas**
**Ator(es): Farmacêutico**  
**Descrição: Validar receita médica para medicamentos controlados**  
**Pré-condições: Receita apresentada**  
**Pós-condições: Venda autorizada**  

**Fluxo**
- Farmacêutico analisa receita
- Farmacêutico validade dados da receita
- Sistema autoriza a venda de medicamentos controlados
- 
**Exceçoes**
-FA01 -> Receita invalida
-FA02 -> Receita vencidade

**Include**
-Consultar produto

**Extend**
-Realizar venda

## **UC10 — Atualização de estoque**
**Ator(es): Sistema**  
**Descrição: Atulizar quantidade de produtos no estoque após venda**  
**Pré-condições: Venda realizada**  
**Pós-condições: Estoque atualizado**

**Fluxo**
- Sistema reduz quantidade do produto vendido
- Sistema salva nova quantidade no estoque
- 
**Exceçoes**
-FA01 -> Erro na atualização
-FA02 -> Inconcistencia de dados

**Include**
-Verificar estoque 

**Extend**
-Realizar venda


@startuml
left to right direction

actor Atendente
actor Farmaceutico
actor Sistema

rectangle "Sistema de Gestão de Farmácia" {

  (Realizar Venda) as UC01
  (Consultar Produto) as UC02
  (Verificar Estoque) as UC03
  (Cadastrar Cliente) as UC04
  (Identificar Cliente) as UC05
  (Registrar Venda a Prazo) as UC06
  (Gerar Conta a Receber) as UC07
  (Emitir Comprovante) as UC08
  (Validar Receita) as UC09
  (Atualizar Estoque) as UC10

}

Atendente --> UC01
Atendente --> UC02
Atendente --> UC04
Atendente --> UC05
Atendente --> UC06

Farmaceutico --> UC09

Sistema --> UC03
Sistema --> UC07
Sistema --> UC08
Sistema --> UC10

UC01 ..> UC02 : <<include>>
UC01 ..> UC03 : <<include>>
UC01 ..> UC08 : <<include>>
UC01 ..> UC10 : <<include>>

UC06 ..> UC07 : <<include>>

UC04 ..> UC01 : <<extend>>
UC06 ..> UC01 : <<extend>>
UC09 ..> UC01 : <<extend>>
UC05 ..> UC01 : <<extend>>

@enduml

(não consegui fazer reproduziar a imagem, porem o codigo dá certo e faz o diagrama testei direto no site do plantuml)
