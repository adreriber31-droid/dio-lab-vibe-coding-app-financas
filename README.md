# 💸 App de Organização de Finanças Pessoais para Declaração de Ajuste Anual do Imposto de Renda com Vibe Coding

App criado com objetivo simples;
Registro automático: calcular lucro ou prejuízo a partir das notas de corretagem, já incluindo taxas e despesas.

Classificação inteligente: organizar transações com rateio proporcional das taxas entre ativos.

Apuração do imposto: mostrar o valor de IR a pagar ou compensar, conforme regras vigentes.

Detecção de inconsistências: identificar vendas antes da compra (short selling ou erro).

Assistente de economia: dicas práticas do “Agente Financeiro” para otimizar o ajuste anual.

Dashboard simples: resultados claros e personalizados com gráficos e indicadores

## 🎯 Desafio

Problema: Muitas pessoas não conseguem manter um controle financeiro para Declaração de Ajuste Anual do Imposto de Renda porque os aplicativos exigem muita entrada de dados manual, e a criação de tabelas complexas é visto como algo tedioso. 

Precisamos de uma solução que permita **controlar as finanças para Declaração Anual por meio de uma interação simples**, com **agentes de IA** capazes de criar **resultados como apuração para pagamento do imposto de renda através da apresentação dos dados das notas de corretagem de forma personalizados e automatizados**. Você deve utilizar as ideias de **Vibe Coding** e **MVP (Produto Mínimo Viável)** para desenvolver o **conceito de um aplicativo** que resolva o problema citado.


```txt
# Contexto
Quero criar um aplicativo de Organização de Finanças Pessoais que funcione por meio de conversas com o usuário.  
A ideia é facilitar o controle financeiro de forma simples e natural, sem formulários manuais ou planilhas complexas.

# Problema
Muitas pessoas desistem de controlar seus gastos porque os apps atuais exigem muita entrada manual e pouca personalização.  
Quero resolver isso com uma experiência de conversa e recomendações automáticas de economia.

# Público-Alvo
Pessoas que querem começar a organizar suas finanças de forma prática e sem complicação, principalmente iniciantes.

# Funcionalidades-Chave
1. Registrar gastos via chat em linguagem natural.  
2. Classificar automaticamente as transações.  
3. Definir e acompanhar metas financeiras.  
4. Receber dicas de economia do “Agente Financeiro”.  
5. Visualizar relatórios simples e personalizados.

# Entregável da IA
Gerar um plano de MVP com as principais telas, recursos necessários e um esboço de validação inicial.  
Usar tom educativo e linguagem acessível, em português.
```

### 3. Entregando o Desafio na DIO

Finalização do projeto criando um **repositório no GitHub** (sendo um **fork** deste).  
No README do meu repositório, inclui:

**Prompt final** (PRD) usado com a Copilot
```
# 📄 Product Requirements Document (PRD) – MVP App de Organização de Finanças Pessoais

## 1. Objetivo
Criar um aplicativo que facilite o controle financeiro para a declaração anual do Imposto de Renda, automatizando cálculos de lucro/prejuízo e imposto devido a partir das informações das notas de corretagem fornecidas pelo usuário. O sistema deve simplificar a experiência, evitando formulários manuais e planilhas complexas.

---

## 2. Escopo
- **Entrada:**  
  - Dados fornecidos pelo usuário via formulário simples.  
  - Arquivo CSV/Excel com colunas: *Ativo, Operação, Quantidade, Preço Unitário, Despesas Rateadas, Valor de Venda, Tipo de Operação*.  

- **Processamento:**  
  - Rateio proporcional das taxas entre ativos, conforme valor financeiro das operações.  
  - Cálculo do custo de aquisição incluindo despesas operacionais.  
  - Cálculo do resultado líquido (lucro/prejuízo).  
  - Identificação de vendas anteriores às compras:  
    - Se permitido → tratar como **short selling** (posição negativa até a compra).  
    - Se não permitido → sinalizar como **inconsistência**.  
  - Apuração do IR devido (15% swing trade, 20% day trade).  
  - Compensação de prejuízos: se o resultado consolidado do período for negativo ou zero, **não há IR a pagar**.  

- **Saída:**  
  - Relatório consolidado por ativo e período.  
  - Exportação em CSV/Excel.  
  - Dashboard com indicadores principais (lucro, prejuízo, despesas, IR).  
  - Recomendações automáticas de economia para o ajuste anual (via “Agente Financeiro”).

---

## 3. Público-Alvo
- Pessoas que querem começar a fazer elas mesmas sua declaração de ajuste anual do IR de forma prática e sem complicação.  
- Principalmente iniciantes que têm investimentos em bolsa de valores e precisam organizar notas de corretagem.

---

## 4. Funcionalidades-Chave
1. Registrar lucro ou prejuízo via fornecimento de dados das notas de corretagem.  
2. Classificar automaticamente as transações considerando o **rateio proporcional das taxas entre ativos**.  
3. Definir e acompanhar valor a ser pago de acordo com apuração e regras contábeis vigentes.  
4. Identificar transações onde a venda ocorre antes da compra (short selling ou erro de ordem).  
5. Receber dicas de economia do “Agente Financeiro” na hora de fazer o ajuste anual.  
6. Visualizar resultados simples e personalizados em dashboard.  

---

## 5. Fluxo de Processamento
1. Upload de arquivo CSV/Excel **ou** entrada manual dos dados.  
2. Validação dos campos.  
3. **Rateio das taxas** proporcional ao valor financeiro das operações.  
4. Cálculo do custo de aquisição:  
   \[
   C_{aquisição} = (Preço \cdot Quantidade) + Despesas\ Rateadas
   \]  
5. Cálculo do resultado líquido:  
   \[
   Resultado = Valor\ de\ Venda - C_{aquisição}
   \]  
6. Identificação de vendas anteriores às compras.  
7. Apuração do IR:  
   - Swing Trade → 15% sobre lucro líquido consolidado.  
   - Day Trade → 20% sobre lucro líquido consolidado.  
   - Se resultado consolidado ≤ 0 → IR = 0,00.  
8. Consolidação dos resultados e geração de relatório.  
9. Exibição de recomendações do “Agente Financeiro”.  

---

## 6. Exemplo de Relatório Simplificado

| Ativo | Operação | Quantidade | Preço Unitário | Valor Bruto | Taxas Rateadas | Custo Total | Valor de Venda | Resultado Líquido | IR Devido |
|-------|-----------|------------|----------------|-------------|----------------|-------------|----------------|-------------------|-----------|
| PETR4 | Compra    | 100        | 30,00          | 3.000,00    | 30,00          | 3.030,00    | -              | -                 | -         |
| PETR4 | Venda     | 100        | 32,00          | 3.200,00    | 30,00          | -           | 3.170,00       | +140,00           | 0,00      |
| VALE3 | Compra    | 50         | 70,00          | 3.500,00    | 10,00          | 3.510,00    | -              | -                 | -         |
| VALE3 | Venda     | 50         | 68,00          | 3.400,00    | 10,00          | -           | 3.390,00       | -120,00           | 0,00      |
| ITUB4 | Venda     | 200        | 25,00          | 5.000,00    | 60,00          | -           | 4.940,00       | +4.940,00         | 741,00    |

---

## 7. Mockup Textual – Dashboard com IR

### Indicadores Principais
- Lucro Líquido Total: +5.080,00  
- Prejuízo Líquido Total: –120,00  
- Resultado Consolidado: +4.960,00  
- Taxas Rateadas Totais: R$ 100,00  
- IR Devido: R$ 741,00  

### Gráficos
- Barras: Lucro/Prejuízo por ativo.  
- Pizza: Distribuição das taxas rateadas.  
- Linha do Tempo: Evolução mensal do resultado líquido e IR devido.  

### Recomendações do “Agente Financeiro”
- Sugestões de compensação de prejuízos em períodos futuros.  
- Alertas sobre vendas antes da compra (short selling).  
- Dicas de economia para reduzir imposto no ajuste anual.  

---

# 📊 Modelo de CSV – 5 Operações com Taxas Rateadas

```csv
Ativo,Operacao,Quantidade,PrecoUnitario,DespesasRateadas,ValorVenda,TipoOperacao
PETR4,Compra,100,30.00,30.00,,Swing Trade
PETR4,Venda,100,32.00,30.00,3200.00,Swing Trade
VALE3,Compra,50,70.00,10.00,,Day Trade
VALE3,Venda,50,68.00,10.00,3400.00,Day Trade
ITUB4,Venda,200,25.00,60.00,5000.00,Swing Trade
```

- Prints ou pequenos vídeos das interações com a IA;
- <img width="720" height="1600" alt="Screenshot_20260218-071834" src="https://github.com/user-attachments/assets/3bb67b67-09f2-48b6-8d68-e01e4ef5d8d8" />
<img width="720" height="1600" alt="Screenshot_20260218-071834" src="https://github.com/user-attachments/assets/3bb67b67-09f2-48b6-8d68-e01e4ef5d8d8" />
<img width="720" height="1600" alt="Screenshot_20260218-072119" src="https://github.com/user-attachments/assets/3c4c197e-6c13-4fe6-80ea-01078009f4cb" />

- Interações com a ferramenta Lovable:
1. Agente Financeiro:
 Persona: Consultor financeiro acessível, paciente e didático — como um "amigo que entende de IR".
Tom de voz:
Simples e direto — evita jargões; quando usa, explica entre parênteses
Encorajador — "Você está no caminho certo!", "Boa notícia: não há IR a pagar"
Proativo — não espera o usuário perguntar; oferece dicas automaticamente
Prudente — sempre recomenda consultar um contador para casos complexos

2. Fluxo de Telas:
Descrição das telas:
Tela	Função
Onboarding	Explica o app em 3 passos simples
Upload/Manual	Importar CSV ou registrar operação
Dashboard	6 cards KPI + gráficos + agente
Operações	Tabela detalhada com alertas
Detalhe	Info completa de uma operação
Exportar	Gerar CSV do relatório
Filtros	Por mês/ano e Swing/Day Trade

4. Plano de MVP:
5 Funcionalidades Principais
#	Funcionalidade	Status
1	Import CSV — upload e parsing automático de notas	✅ Implementado
2	Cálculo automático — lucro/prejuízo, rateio de taxas, IR	✅ Implementado
3	Dashboard visual — cards KPI + gráficos recharts	✅ Implementado
4	Agente Financeiro — recomendações automáticas	✅ Implementado
5	Exportar relatório — download CSV consolidado	✅ Implementado

Recursos necessários para evolução:
Lovable Cloud — persistência de dados e login de usuários
🔲 Formulário manual — entrada sem CSV
🔲 Filtros por período e tipo de operação
🔲 Onboarding guiado para primeiro acesso
Plano de validação:

Métrica principal: Usuário consegue importar CSV e entender o IR devido em < 2 min
Teste: 5 usuários reais importam seus dados e avaliam clareza do dashboard
Sucesso: 80%+ dos testadores entendem o resultado sem ajuda externa

https://lovable.dev/projects/723221d2-cbdb-4b5a-a0dd-b564da9175b8

<img width="720" height="1600" alt="Screenshot_20260219-230849" src="https://github.com/user-attachments/assets/9c98c6a0-815b-4b35-b11b-36717815c726" />
<img width="720" height="1600" alt="Screenshot_20260220-000818" src="https://github.com/user-attachments/assets/9ff5ed5d-66d7-4fdb-bd4b-cfb70d5c59d0" />
<img width="720" height="1600" alt="Screenshot_20260220-000832" src="https://github.com/user-attachments/assets/5a3ffcbe-1cd4-4004-aa97-cad0e59d9aea" />
<img width="720" height="1600" alt="Screenshot_20260220-000901" src="https://github.com/user-attachments/assets/def5145c-8086-4ab7-ad69-fdd8ef144d3c" />

- Um resumo do que o seu **App de Finanças Pessoais de Declaração do Ajuste Anual do Imposto de Renda** faz;
- Aplicabilidade das Funcionalidades
- Registro de resultados financeiros: Permite lançar automaticamente lucros ou prejuízos a partir das notas de corretagem, facilitando o controle contábil.  
- Classificação inteligente de transações: Organiza operações e distribui proporcionalmente taxas entre ativos, garantindo precisão nos cálculos.  - Gestão de obrigações fiscais: Define e acompanha valores a pagar conforme regras contábeis vigentes, evitando erros na apuração.  
- Detecção de inconsistências: Identifica operações de venda antes da compra (short selling ou erros de ordem), prevenindo problemas futuros.  
- Apoio consultivo: Oferece dicas de economia do “Agente Financeiro” para otimizar o ajuste anual.  
- Visualização prática: Apresenta resultados em dashboards simples e personalizados, facilitando a análise rápida da situação financeira.
  
- Uma breve **reflexão sobre o processo**:
 Tive de fazer e refazer algumas vezes por não ter habilidade com as interações dos softwares.
 
  - O que funcionou bem?
  - Rapidez mas respostas e alternativas criativas que auxiliaram em muito a criação do app.
    
  - O que não funcionou como o esperado?
     Em um dos campos na base de cálculo havia um erro, que por um descuido, poderia ter passado:
    "Correção do exemplo
Na tabela que mostrei, coloquei IR Devido = 15,00 para PETR4 isoladamente.
Mas no dashboard consolidado, o correto seria:

Lucro Líquido Total: +100,00

Prejuízo Líquido Total: –180,00

Resultado Consolidado: –80,00

IR Devido: 0,00 (porque o prejuízo compensou o lucro)"

  - O que aprendeu sobre conversar com IAs?
  - Facilidade e rapidez quando solicitações sao feitas de forma clara.

> [!TIP]
> Publique seu repositório e compartilhe o link na plataforma da DIO!

> Sua entrega é a prova de que você domina o raciocínio de Vibe Coding, mesmo sem escrever uma única linha de código.

## 💬 Conclusão

Vibe Coding é sobre clareza, curiosidade e criatividade, não sobre perfeição técnica. O verdadeiro objetivo aqui é aprender a pensar junto com a IA, transformando ideias em conceitos reais e enxergando a tecnologia como uma extensão do seu raciocínio criativo. Cada interação é um experimento, quanto mais clara for sua intenção, mais surpreendente será o resultado.
