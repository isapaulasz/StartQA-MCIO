# Aula 1: Qualidade de Software, muito além de encontrar bugs


## O que é qualidade de software

Qualidade não se limita a "funcionar": é garantir que o software funcione corretamente e entregue valor, atendendo às expectativas de quem usa.
- Não existe software com zero bugs; o objetivo é reduzir defeitos e riscos, não prometer ausência total.
- Satisfação do cliente é o resultado final da qualidade.
- Qualidade reduz custos (retrabalho, suporte, correções em produção) e aumenta a competitividade.
- O QA ajuda a garantir que o produto seja desenvolvido com qualidade desde o começo.

## Qualidade é multidimensional (ISO 25010)

A norma ISO 25010 organiza a qualidade de um produto de software em características. As que vimos em aula:

| Dimensão | Pergunta que ela responde |
| -------- | ----------------- |  
| Funcionalidade | O sistema faz o que deveria fazer? |
| Confiabilidade | Ele continua funcionando de forma estável? |
| Performance | Ele responde com rapidez, mesmo sob carga? |
| Segurança | Os dados e os acessos estão protegidos? |
| Usabilidade | É fácil e agradável de usar? |
| Acessibilidade | Pessoas com diferentes necessidades conseguem usar? |

A norma ainda inclui compatibilidade, manutenibilidade e portabilidade, que valem como pesquisa complementar.

## Ser QA

O trabalho de QA começa antes do código e continua depois da entrega. As responsabilidades vistas em aula:

1. Analisar requisitos
2. Identificar riscos
3. Definir estratégias de qualidade
4. Prevenir defeitos
5. Criar e executar testes
6. Comunicar evidências e resultados
7. Apoiar decisões e a melhoria contínua

O mindset de prevenção é o que mais melhora o trabalho: é mais barato evitar um defeito do que corrigi-lo depois.

## Testing, Quality Control e Quality Assurance

São conceitos relacionados, mas com focos diferentes, e não uma disputa de cargos.

| Conceito | Foco | Exemplo prático |
| -------- | ---- | ----------- |
| Testing (testes) | Atividades para descobrir problemas; execução, comportamento correto, validação de funcionalidades e registro de evidências | Executar o fluxo de cadastro e registrar o erro encontrado |
| Quality Control (QC) | Avaliar o produto e verificar a conformidade com critérios definidos | Checar se a entrega atende aos critérios de aceite |
| Quality Assurance (QA) | Práticas, processos, prevenção e melhoria | Revisar requisitos com o time antes do desenvolvimento |

Testar software é pensar qualidade, mas o olhar de QA é mais amplo: conecta produto, tecnologia e negócio.

## Mentalidade do analista de qualidade

O QA aprende a fazer boas perguntas. Cada postura tem a sua pergunta:

- Curiosidade: e se...? O que acontece quando...?
- Pensamento crítico: isso faz sentido?
- Visão de risco: o que pode dar errado?
- Olhar do cliente: como isso afeta quem usa?
- Olhar de negócio: se falhar, qual a consequência?

## Qualidade é responsabilidade de todos

No ciclo de vida do desenvolvimento (SDLC), cada papel contribui para a qualidade:

1. PO (Product Owner): define o que construir e por quê
2. UX: desenha a experiência de uso
3. Dev: constrói a solução
4. QA: avalia riscos, testa e comunica evidências
5. DevOps: cuida da entrega e da operação
6. Usuário: sente o resultado final

O QA pode atuar em todas essas etapas, não só no meio do caminho.

### O contexto muda o risco

A mesma falha pode ter consequências muito diferentes conforme o produto:

| Contexto | O que uma falha pode causar |
| -------- | --------------------- |
| Banco | Perda financeira, quebra de confiança, problemas legais |
| E-commerce | Vendas perdidas, carrinho abandonado |
| Streaming | Experiência ruim, cancelamento de assinatura |
| Saúde | Risco à vida e à privacidade de pacientes |

Por isso a estratégia de testes depende do contexto e do risco de cada produto.

## Ideias-chave para levar

- Qualidade é maior que "o sistema funciona".
- Qualidade é responsabilidade de todos.
- Testar é essencial, mas o QA pode atuar muito além dos testes.
- Qualidade impacta cliente, operação, tecnologia, negócio e marca.
- Pensar como QA é aprender a fazer boas perguntas e enxergar riscos.

## Perguntas para fixar

1. Qual a diferença entre testing, quality control e quality assurance, com um exemplo de cada?
2. Por que "zero bugs" não é um objetivo realista?
3. Dê um exemplo de falha igual com consequências diferentes em dois tipos de produto.
4. Qual das cinco posturas do QA (curiosidade, pensamento crítico, risco, cliente, negócio) você já usa no dia a dia?

## Glossário

| Termo | Definição |
| ----- | --------- |
| Bug | Fefeito visível no comportamento |
| Erro | Engano humano |
| Falha | O sistema se comporta de forma errada |
| Requisito | O que o sistema precisa fazer |


## Tarefa de casa

**Cenário**

> Uma empresa lançou uma promoção:
> 
> *"Clientes que comprarem acima de R$ 200 recebem 20% de desconto"*
> 
> No primeiro dia, alguns clientes reclamam que compras acima de R$ 200 não recebem o desconto.

**Discussão**

1. O que vocês perguntariam?

    <details>
    <summary><b>Resposta</b></summary>

    - R$ 200,00 exato entra? (maior que 200, ou maior ou igual a 200?)
    - O valor considerado é antes ou depois de frete, impostos e outros descontos?
    - O desconto vale para todos os produtos ou há exceções (itens já em promoção, categorias excluídas)?
    - Vale para todos os canais (app, site, loja física) e todos os clientes (novos, antigos, logados ou não)?
    - A promoção acumula com cupons? Qual o período de validade?
    - O desconto aparece no carrinho, no pagamento ou só na fatura?
    - Quais clientes reclamaram, e em que valores, canais e horários?

    </details>

2. O que pode dar errado?

    <details>
    <summary><b>Resposta</b></summary>

    - Erro de condição no código (usar > em vez de >=, ou comparar com o valor errado)
    - O desconto é calculado sobre o valor errado (por exemplo, depois do frete)
    - Arredondamento de centavos (R$ 200,00 virando R$ 199,99)
    - Diferença entre canais (a regra existe no site, mas não no app)
    - Conflito com outras promoções ou cupons
    - Falha de configuração: a promoção não foi ativada para todos
    - Cache ou atraso na atualização do carrinho

    </details>

3. O que vocês testariam?

    <details>
    <summary><b>Resposta</b></summary>

    - Valores-limite: R$ 199,99, R$ 200,00 e R$ 200,01
    - Valores bem acima e bem abaixo de 200
    - Combinações: vários itens, itens em promoção, uso de cupom, com e sem frete
    - Canais: app, site e outros
    - Tipos de cliente: novos, antigos, sem login
    - Aplicação do desconto: o cálculo (20%) está correto e aparece igual no carrinho, no pagamento e no comprovante?

    </details>

4. Quem pode ser impactado?

    <details>
    <summary><b>Resposta</b></summary>

    - Marketing e produto (a campanha perde efeito)
    - Financeiro (descontos concedidos errado ou cobranças incorretas)
    - Time de operações e vendas
    - Possivelmente o jurídico, se a promoção tiver sido divulgada e não for cumprida (por exemplo, questões de direito do consumidor)

    </details>

5. Qual o risco para o neǵocio?

    <details>
    <summary><b>Resposta</b></summary>

    - Perda de receita e de confiança na marca
    - Aumento de chamados no suporte e de reclamações públicas (redes sociais, Reclame Aqui)
    - Custo de corrigir e compensar clientes
    - Risco legal e de reputação por propaganda não cumprida
    - Prejuízo financeiro se o erro for o oposto (desconto dado a mais)

    </details>







