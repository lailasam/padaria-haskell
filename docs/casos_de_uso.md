# 🧍🏻‍♀️ Casos de Uso - Dream Bakery

Este documento detalha as interações dos usuários com o sistema.

---

## 🔐 Módulo 1: Autenticação e Gestão de Usuários

### UC01: Efetuar login

**Descrição:**
Permite que o usuário acesse as áreas restritas do sistema de acordo com suas permissões.

**Atores:**
Gerente, padeiro, vendedor.

**Pré-condições:**
O usuário deve estar cadastrado no sistema.

**Pós-condições:**
Sessão autenticada iniciada; acesso liberado ao menu principal.

**Fluxo principal:**
1. O usuário acessa a tela de login.
2. O usuário insere e-mail.
3. O usuário insere a senha.
4. O usuário clica em "Entrar".
5. O usuário visualiza o dashboard principal.

**Fluxo de exceções:**
FE01 – Credenciais inválidas
O usuário insere o email e a senha e clica em "Entrar", mas visualiza a mensagem "Credenciais inválidas" e permanece na tela de login. 

**Regras de negócio:**
RN01: Somente um usuário cadastrado consegue acessar a área restrita do sistema.

### UC02: Efetuar logout

**Descrição:**
Permite que o usuário finalize sua sessão no sistema.

**Atores:**
Gerente, padeiro, vendedor.

**Pré-condições:**
O usuário deve estar logado no sistema.

**Pós-condições:**
Sessão finalizada; usuário é redirecionado para a tela de login.

**Fluxo principal:**
1. O usuário clica no menu lateral.
2. O usuário clica em "Sair".
3. O usuário clica em "Confirmar".
4. O usuário é redirecionado para a tela de login.

**Fluxo alternativo:**
FA01 – Usuário deseja cancelar o logout
O usuário clica em "Sair", mas desiste antes de confirmar. Ao visualizar a tela de confirmação, clica em "Cancelar" e permanece na tela anterior.

### UC03: Cadastrar usuário

**Descrição:**
Permite cadastrar um novo usuário no sistema.

**Atores:**
Gerente.

**Pré-condições:**
O usuário do tipo gerente deve estar autenticado no sistema.

**Pós-condições:**
Um novo registro de usuário é criado no banco de dados.

**Fluxo principal:**
1. O gerente acessa a tela de "Gestão de Usuários".
2. O gerente clica em "Novo Usuário".
3. O gerente preenche os dados pessoais.
4. O gerente seleciona o Perfil.
5. O gerente clica em "Salvar".

**Fluxo alternativo:**
FA01 – Cancelar cadastro
O gerente clica em "Cancelar" a qualquer momento e retorna à lista de usuários sem salvar os dados.

**Fluxo de exceções:**
FE01 – Email já cadastrado
Se o e-mail inserido já existir no sistema, é exibida a mensagem "Este e-mail já está em uso" e o salvamento é impedido.

FE02 – CPF já cadastrado
Se o CPF inserido já existir no sistema, é exibida a mensagem "Este CPF já está em uso" e o salvamento é impedido.

FE03 – Campos obrigatórios em branco
O gerente tenta salvar o novo usuário deixando campos obrigatórios em branco. A mensagem "Todos os campos obrigatórios devem ser preenchidos" é exibida e o salvamento é impedido.

**Regras de negócio:**
RN02: Os emails cadastrados devem ser únicos.
RN03: Os CPFs cadastrados devem ser únicos.
RN04: Somente os gerentes podem cadastrar novos usuários.

### UC04: Editar perfil de usuário

**Descrição:**
Permite alterar dados de um usuário existente no sistema.

**Atores:**
Gerente, padeiro, vendedor.

**Pré-condições:**
O usuário deve estar autenticado no sistema.

**Pós-condições:**
Os dados do usuário são atualizados.

**Fluxo principal:**
1. O usuário acessa a tela de edição de perfil.
2. O usuário altera os dados desejados.
3. O usuário clica em "Salvar".

**Fluxo alternativo:**
FA01 – Cancelar edição
O usuário clica em "Cancelar" antes da confirmação e permanece na tela de edição.

**Regras de negócio:**
RN05: Somente os gerentes podem editar perfis de usuários que não sejam o seu próprio.

### UC05: Deletar perfil de usuário

**Descrição:**
Permite deletar um cadastro de usuário do sistema.

**Atores:**
Gerente, padeiro, vendedor.

**Pré-condições:**
O usuário deve estar autenticado no sistema.

**Pós-condições:**
Um perfil de usuário é inativado.

**Fluxo principal:**
1. O usuário acessa tela de perfil.
2. O usuário clica em "Deletar".
3. O usuário clica em "Confirmar".
4. O usuário é redirecionado para a tela de login.

**Fluxo alternativo:**
FA01 – Cancelar deleção
O usuário clica em "Cancelar" antes da confirmação e permanece na tela de perfil.

**Regras de negócio:**
RN06: Somente os gerentes podem deletar um perfil que não seja o seu próprio.

### UC06: Visualizar perfil de usuário

**Descrição:**
Permite visualizar o perfil de um usuário do sistema.

**Atores:**
Gerente, padeiro, vendedor.

**Pré-condições:**
O usuário deve estar autenticado no sistema.

**Pós-condições:**
Informações de um usuário são exibidas.

**Fluxo principal:**
1. O usuário acessa tela de perfil.
2. O usuário visualiza informações.

**Regras de negócio:**
RN06: Somente os gerentes podem visualizar dados pessoais de outros usuários.

---
## 🍞 Módulo 2: Gestão de produtos

## UC07: Cadastrar produto
## UC08: Editar produto
## UC09: Inativar produto
## UC10: Visualizar catálogo de produtos
---
## 🧂 Módulo 3: Gestão de ingredientes

## UC07: Cadastrar ingrediente
## UC08: Editar ingrediente
## UC09: Inativar ingrediente
## UC10: Visualizar estoque de ingredientes
---
## 👨‍🍳 Módulo 4: Gestão de Receitas e Custos

## UC15: Definir ficha técnica da receita 
## UC16: Editar ficha técnica
## UC17: Visualizar cálculo automático de custo de produção
---
## 📦 Módulo 5: Produção e Inventário

## UC18: Registrar entrada de mercadoria
## UC19: Registrar lote de produção
## UC20: Registrar perda ou desperdício
---
## 🛒 Módulo 6: Ponto de Venda

## UC21: Abrir caixa 
## UC22: Realizar venda
## UC23: Cancelar venda
## UC24: Fechar caixa
---
## 📊 Módulo 7: Relatórios Gerenciais

## UC25: Gerar relatório de vendas por período
## UC26: Gerar relatório de produção e desperdício
## UC27: Visualizar insights de lucratividade e tendências
