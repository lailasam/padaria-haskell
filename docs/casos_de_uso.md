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
- FE01 – Credenciais inválidas
  - O usuário insere o email e a senha e clica em "Entrar", mas visualiza a mensagem "Credenciais inválidas" e permanece na tela de login. 

**Regras de negócio:**
- RN01: Somente um usuário cadastrado consegue acessar a área restrita do sistema.

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
- FA01 – Usuário deseja cancelar o logout
  - O usuário clica em "Sair", mas desiste antes de confirmar. Ao visualizar a tela de confirmação, clica em "Cancelar" e permanece na tela anterior.

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
- FA01 – Cancelar cadastro
  - O gerente clica em "Cancelar" a qualquer momento e retorna à lista de usuários sem salvar os dados.

**Fluxo de exceções:**
- FE01 – Email já cadastrado
  - Se o e-mail inserido já existir no sistema, é exibida a mensagem "Este e-mail já está em uso" e o salvamento é impedido.

- FE02 – CPF já cadastrado
  - Se o CPF inserido já existir no sistema, é exibida a mensagem "Este CPF já está em uso" e o salvamento é impedido.

- FE03 – Campos obrigatórios em branco
  - O gerente tenta salvar o novo usuário deixando campos obrigatórios em branco. A mensagem "Todos os campos obrigatórios devem ser preenchidos" é exibida e o salvamento é impedido.

**Regras de negócio:**
- RN02: Os emails cadastrados devem ser únicos.
- RN03: Os CPFs cadastrados devem ser únicos.
- RN04: Somente os gerentes podem cadastrar novos usuários.

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
- FA01 – Cancelar edição
  - O usuário clica em "Cancelar" antes da confirmação e permanece na tela de edição.

**Regras de negócio:**
- RN05: Somente os gerentes podem editar perfis de usuários que não sejam o seu próprio.

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
- FA01 – Cancelar deleção
  - O usuário clica em "Cancelar" antes da confirmação e permanece na tela de perfil.

**Regras de negócio:**
- RN06: Somente os gerentes podem deletar um perfil que não seja o seu próprio.

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
- RN07: Somente os gerentes podem visualizar dados pessoais de outros usuários.

---
## 🍞 Módulo 2: Gestão de produtos

### UC07: Cadastrar produto

**Descrição:**
Permite ao gerente incluir novos itens que serão vendidos diretamente ao consumidor final.

**Atores:**
Gerente.

**Pré-condições:**
O usuário do tipo gerente deve estar autenticado no sistema.

**Pós-condições:**
Produto registrado com identificador único e disponível no catálogo.

**Fluxo principal:**
1. O gerente acessa a tela "Catálogo de Produtos".
2. O gerente clica em "Novo Produto".
3. O gerente preenche: Nome, Preço de Venda e código identificador.
4. O gerente clica em "Salvar".

**Fluxo alternativo:**
- FA01 – Cancelar cadastro
  - O gerente clica em "Cancelar" a qualquer momento e retorna ao catálogo de produtos.
  
**Fluxo de exceções:**
- FE01 – Identificador duplicado
  - O gerente tenta salvar o novo produto com um identificador existente, mas recebe a mensagem de erro "Identificador já cadastrado" e o salvamento é impedido.

- FE01 – Campos obrigatórios em branco
  - O gerente tenta salvar o novo produto com um campo obrigatório em branco, mas recebe a mensagem de erro "Todos os campos obrigatórios devem ser preenchidos" e o salvamento é impedido.
    
**Regras de negócio:**
- RN08: Somente os gerentes podem cadastrar novos produtos.
- RN09: O identificador deve seguir o padrão definido, para facilitar a busca rápida.
- RN10: Não deve ser permitido cadastrar produtos com preço igual ou inferior a zero.

### UC08: Editar produto

**Descrição:**
Permite a atualização de informações comerciais de um produto.

**Atores:**
Gerente.

**Pré-condições:**
O usuário do tipo gerente deve estar autenticado no sistema.

**Pós-condições:**
Informações do produto são atualizadas no catálogo.

**Fluxo principal:**
1. O gerente acessa a tela "Catálogo de Produtos".
2. O gerente clica em um produto da lista.
3. O gerente clica em "Editar".
4. O gerente altera os dados desejados.
5. O gerente clica em "Salvar".

**Fluxo alternativo:**
- FA01 – Cancelar edição
  - O gerente clica em "Cancelar" a qualquer momento e retorna ao catálogo de produtos.
    
**Regras de negócio:**
- RN11: Ao alterar o preço, o sistema deve registrar a data da alteração para histórico de preços.

### UC09: Inativar produto

**Descrição:**
Permite remover um produto da disponibilidade de venda sem excluir seus dados históricos.

**Atores:**
Gerente.

**Pré-condições:**
O usuário do tipo gerente deve estar autenticado no sistema.

**Pós-condições:**
Produto é inativado para venda.

**Fluxo principal:**
1. O gerente acessa a tela "Catálogo de Produtos".
2. O gerente clica em um produto da lista.
3. O gerente clica em "Inativar".
4. O gerente clica em "Confirmar".

**Fluxo alternativo:**
- FA01 – Cancelar inativação
  - O gerente clica em "Cancelar" a qualquer momento e retorna ao catálogo de produtos.
    
**Regras de negócio:**
- RN12: Um produto inativo não pode ser selecionado na tela de venda, mas continua aparecendo em relatórios de vendas passadas.

### UC10: Visualizar catálogo de produtos

**Descrição:**
Permite a consulta rápida de todos os itens disponíveis na padaria.

**Atores:**
Gerente, vendedor, padeiro.

**Pré-condições:**
O usuário deve estar autenticado no sistema.

**Pós-condições:**
Lista de produtos é exibida.

**Fluxo principal:**
1. O usuário acessa a tela "Catálogo de Produtos".
2. O usuário visualiza lista com todos os produtos.

**Fluxo alternativo:**
- FA01 – Cancelar inativação
  - O gerente clica em "Cancelar" a qualquer momento e retorna ao catálogo de produtos.

---
## 🧂 Módulo 3: Gestão de ingredientes

### UC11: Cadastrar ingrediente

**Descrição:**
Permite registrar as matérias-primas que serão utilizadas na produção.

**Atores:**
Gerente.

**Pré-condições:**
O usuário do tipo gerente deve estar autenticado no sistema.

**Pós-condições:**
Ingrediente disponível para ser vinculado a receitas e para registros de compra.

**Fluxo principal:**
1. O gerente acessa a tela de "Gestão de Insumos".
2. O gerente clica em "Novo Ingrediente".
3. O gerente preenche: Nome, Unidade de Medida e Estoque Mínimo.
4. O gerente clica em "Salvar".

**Fluxo alternativo:**
- FA01 – Cancelar cadastro
  - O gerente clica em "Cancelar" a qualquer momento e retorna à tela de gestão de insumos.
  
**Fluxo de exceções:**
- FE01 – Nome duplicado
  - Ao tentar cadastrar um ingrediente com nome já registrado, a mensagem "Nome já cadastrado" é exibida e o sistema impede o cadastro para evitar confusão no estoque.

- FE02 – Campos obrigatórios em branco
  - Ao tentar salvar o cadastro deixando campos obrigatórios em branco, a mensagem de erro "Todos os campos obrigatórios devem ser preenchidos" é exibida e o salvamento é impedido.

**Regras de negócio:**
- RN13: O sistema deve oferecer uma lista pré-definida de unidades de medida para manter a padronização e facilitar cálculos futuros.
- RN14: O valor do estoque mínimo deve ser obrigatoriamente maior ou igual a zero.
  
### UC12: Editar ingrediente

**Descrição:**
Permite alterar dados básicos do insumo ou ajustar o nível de estoque mínimo.

**Atores:**
Gerente.

**Pré-condições:**
O usuário do tipo gerente deve estar autenticado no sistema.

**Pós-condições:**
Informações do ingrediente atualizadas na tela de gestão de insumos.

**Fluxo principal:**
1. O gerente acessa a tela de "Gestão de Insumos".
2. O gerente clica em um ingrediente.
3. O gerente clica em "Editar".
4. O gerente altera os dados desejados.
5. O gerente clica em "Salvar".

**Fluxo alternativo:**
- FA01 – Cancelar edição
  - O gerente clica em "Cancelar" a qualquer momento e retorna à tela de gestão de insumos.

### UC13: Inativar ingrediente

**Descrição:**
Impede que um ingrediente seja usado em novas produções ou compras sem apagar seu histórico.

**Atores:**
Gerente.

**Pré-condições:**
O usuário do tipo gerente deve estar autenticado no sistema.

**Pós-condições:**
Informações do ingrediente atualizadas na tela de gestão de insumos.

**Fluxo principal:**
1. O gerente acessa a tela de "Gestão de Insumos".
2. O gerente clica em um ingrediente.
3. O gerente clica em "Inativar".
4. O gerente clica em "Confirmar".

**Fluxo alternativo:**
- FA01 – Cancelar inativação
  - O gerente clica em "Cancelar" a qualquer momento e retorna à tela de gestão de insumos.

**Regras de negócio:**
- RN15: Um ingrediente não pode ser excluído fisicamente se já houver registros de movimentação de estoque ou se ele estiver vinculado a uma receita ativa. Ele deve ser apenas "Inativado".
  
### UC14: Visualizar estoque de ingredientes

**Descrição:**
Permite a consulta das quantidades físicas disponíveis de cada matéria-prima.

**Atores:**
Gerente, padeiro.

**Pré-condições:**
O usuário deve estar autenticado no sistema.

**Pós-condições:**
Informações dos ingredientes disponíveis na tela de gestão de insumos.

**Fluxo principal:**
1. O usuário acessa a tela de "Gestão de Insumos".
2. O usuário visualiza lista de ingredientes.

**Regras de negócio:**
- RN16: Ingredientes cujo saldo atual seja menor ou igual ao estoque mínimo definido devem ser destacados visualmente para sinalizar necessidade de compra.
---
## 👨‍🍳 Módulo 4: Gestão de Receitas e Custos

### UC15: Definir ficha técnica da receita

**Descrição:**
Permite associar uma lista de ingredientes e suas respectivas quantidades a um produto.

**Atores:**
Padeiro.

**Pré-condições:**
O usuário do tipo padeiro deve estar autenticado no sistema; produtos e ingredientes já cadastrados.

**Pós-condições:**
Receita salva e vinculada ao produto; custo base calculado automaticamente.

**Fluxo principal:**
1. O padeiro acessa a tela de "Receitas".
2. O padeiro clica em "Nova receita".
3. O padeiro lista os ingredientes, quantidades e produto.
4. O padeiro clica em "Salvar".

**Fluxo alternativo:**
- FA01 – Cancelar cadastro de receita.
  - O padeiro clica em "Cancelar" a qualquer momento e retorna à tela de receitas.

  **Fluxo de exceções:**
- FE01 – Campos obrigatórios em branco
  - Ao tentar cadastrar uma receita deixando campos obrigatórios em branco, a mensagem de erro "Todos os campos obrigatórios devem ser preenchidos" aparece e o salvamento é impedido.
    
### UC16: Editar ficha técnica

**Descrição:**
Permite o ajuste das proporções caso haja mudança na qualidade do insumo ou no modo de preparo.

**Atores:**
Padeiro.

**Pré-condições:**
O usuário do tipo padeiro deve estar autenticado no sistema.

**Pós-condições:**
Informações da receita atualizadas.

**Fluxo principal:**
1. O padeiro acessa a tela de "Receitas".
2. O padeiro clica em uma receita.
3. O padeiro clica em "Editar".
4. O padeiro altera as informações desejadas.
5. O padeiro clica em "Salvar".

**Fluxo alternativo:**
- FA01 – Cancelar edição de receita.
  - O padeiro clica em "Cancelar" a qualquer momento e retorna à tela de receitas.
    
### UC17: Visualizar cálculo automático de custo de produção

**Descrição:**
Demonstração financeira do impacto da receita no caixa da padaria.

**Atores:**
Padeiro, gerente.

**Pré-condições:**
O usuário deve estar autenticado no sistema.

**Pós-condições:**
Custo de todos os produtos fica disponível.

**Fluxo principal:**
1. O usuário acessa a tela de "Receitas".
2. O usuário clica em uma receita.
3. O usuário visualiza o custo.
---
## 📦 Módulo 5: Produção e Inventário

### UC18: Registrar entrada de mercadoria

**Descrição:**
Registro de novos insumos que chegam dos fornecedores para abastecer o estoque.

**Atores:**
Padeiro, gerente.

**Pré-condições:**
O usuário deve estar autenticado no sistema.

**Pós-condições:**
Quantidade do insumo é atualizada.

**Fluxo principal:**
1. O usuário acessa a tela de "Gestão de Insumos".
2. O usuário clica em um ingrediente.
3. O usuário digita a quantidade recebida.
4. O usuário clica em "Salvar".

**Fluxo alternativo:**
- FA01 – Cancelar registro de novos insumos.
  - O usuário clica em "Cancelar" a qualquer momento e retorna à tela de gestão de insumos.

**Regras de negócio:**
- RN17: Apenas o Gerente pode editar o preço de custo, mas o Padeiro pode registrar a quantidade física recebida.

### UC19: Registrar lote de produção

**Descrição:**
O Padeiro informa o que produziu e o sistema gerencia a conversão de estoque.

**Atores:**
Padeiro.

**Pré-condições:**
O usuário do tipo padeiro deve estar autenticado no sistema; receita cadastrada; saldo de ingredientes em estoque.

**Pós-condições:**
Estoque de ingredientes diminui e estoque de produtos aumenta.

**Fluxo principal:**
1. O padeiro acessa a tela de "Catálogo de produtos".
2. O padeiro clica em um produto.
3. O padeiro digita a quantidade produzida.
4. O padeiro clica em "Salvar".

**Fluxo de exceções:**
- FE01 – Estoque insuficiente.
  - O usuário tenta realizar o registro estando com estoque insuficiente, então recebe a mensagem de erro "Estoque insuficiente" e o salvamento é impedido.

**Regras de negócio:**
- RN18: Toda produção deve gerar um registro de lote para rastreabilidade de validade.
- RN19: O lote de produção só é registrado se o estoque for suficiente.
  
### UC20: Registrar perda ou desperdício

**Descrição:**
Permite informar itens que não podem ser vendidos (queimados, estragados).

**Atores:**
Padeiro, vendedor.

**Pré-condições:**
O usuário deve estar autenticado no sistema; produto deve estar cadastrado.

**Pós-condições:**
Estoque de produtos diminui.

**Fluxo principal:**
1. O usuário acessa a tela de "Catálogo de produtos".
2. O usuário clica em um produto.
3. O usuário digita a quantidade desperdiçada.
4. O usuário clica em "Salvar".

**Fluxo de exceções:**
- FE01 – Quantidade desperdiçada maior que a produzida.
  - O usuário tenta registrar uma quantidade de produtos desperdiçados maior que a produzida, então recebe a mensagem de erro "Quantidade incompatível" e o salvamento é impedido.

**Regras de negócio:**
- RN20: A quantidade desperdiçada deve ser menor ou igual que o total produzido.
---
## 🛒 Módulo 6: Ponto de Venda

### UC21: Abrir caixa 

### UC22: Realizar venda
### UC23: Cancelar venda
### UC24: Fechar caixa
---
## 📊 Módulo 7: Relatórios Gerenciais

### UC25: Gerar relatório de vendas por período
### UC26: Gerar relatório de produção e desperdício
### UC27: Visualizar insights de lucratividade e tendências
