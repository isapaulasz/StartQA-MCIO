# Aula 2: Do requisito à produção, QA no ciclo de desenvolvimento

## Quando começa a qualidade?

Quanto mais cedo o QA entra no ciclo, menor o custo de retrabalho. Existe o paradigma de que o QA só entra depois do desenvolvimento, mas o ideal é que ele participe desde o início, já no pensamento dos requisitos. É nesse período que os cenários de teste começam a ser pensados.

Esse é o cenário ideal, mas não acontece em todas as empresas.

>**Spoiler**: a qualidade não começa quando o QA chega para testar. O QA entra desde o requisito, e isso evita problemas como:

- Cenários esquecidos: o QA conhece os requisitos e as regras de negócio
- Arquitetura com risco: o QA olha para o risco do negócio
- Retrabalho muito caro: corrigir tarde custa mais

## SDLC e onde o QA entra

O SDLC (Software Development Life Cycle) é o ciclo de vida de desenvolvimento de software. A maioria das empresas junta etapas ou muda o nome delas, mas a lógica é a mesma. Em cada etapa, o QA tem uma atuação e uma pergunta central.

| Etapa | Foco de qualidade | Onde o QA entra | Pergunta de QA (slides) |
| ----- | ----------------- | ----------- | ------------------ |
| 1. Planejamento e descoberta |Qualidade em todo o ciclo  |Questiona valor e risco  | Qual problema estamos resolvendo? Como saberemos se deu certo? |
| 2. Requisitos e critérios de aceite | Padrões e boas práticas | Remove ambiguidade | Até quando? Pedido já pago? CEP inválido? Outro país? |
| 3. Análise, design e arquitetura | Segurança e conformidade | Avalia fluxos e exceções | Quais sistemas recebem o novo endereço? O fluxo é seguro e acessível? |
| 4. Desenvolvimento | Revisões e validações | Colabora e antecipa falhas | Os cenários e critérios estão alinhados com o Dev? |
| 5. Testes e QA | Revisões e validações | Faz testes e gera evidências | O que validar? |
| 6. Deploy e entrega | Métricas e monitoramento | Protege e entrega | Estamos seguros para liberar? |
| 7. Operação, manutenção e feedback | Qualidade focada no usuário Aprende com os dados | O que escapou? Por quê? |

QA não testa em produção. Na etapa 7, o QA observa e aprende com dados reais (erros, logs, alertas, feedback), mas não usa o ambiente de produção como ambiente de teste.

## Exemplo: alterar o endereço de entrega

A mesma história gera perguntas diferentes em cada etapa do SDLC. O exemplo da aula é um e-commerce, com a história: *"Eu, como cliente, quero alterar meu endereço para receber meu pedido corretamente."*

1. **Planejamento e descoberta**: o QA ajuda a entender o problema e os riscos do que está sendo proposto.
    - Perguntas: quem precisa alterar o endereço? Em que momento isso é permitido? Qual problema estamos resolvendo? Existe impacto financeiro ou fraude? Como saberemos se deu certo?
    - Contribuições: refinar hipóteses, identificar riscos cedo, trazer cenários reais de uso, questionar regras incompletas e conectar qualidade ao valor.
    - Resultado: menos surpresa depois e mais clareza sobre problema, público, restrições e riscos antes de investir em implementação.

2. **Requisitos e critérios de aceite**: um bom requisito reduz interpretações diferentes.
    - Requisito: "Cliente pode alterar o endereço."
    - Perguntas: até quando? Pedido já pago? CEP inválido? Outro país? Há confirmação? Atualiza todos os sistemas?
    - Critérios claros são a base para desenvolvimento, testes e aceite.

3. **Análise, design e arquitetura**: antes do código, já existem decisões que podem facilitar ou quebrar a experiência.
    - Experiência: o usuário entende o que pode alterar? Recebe mensagens claras? Existe confirmação antes de salvar?
    - Integrações: quais sistemas recebem o novo endereço? O que acontece se uma integração falhar? Há consistência entre canais?
    - Não funcional: o fluxo é acessível? É seguro? Funciona em diferentes dispositivos? Há requisitos de performance?

4. **Desenvolvimento**: a colaboração durante a implementação reduz o ciclo "desenvolve, testa, devolve".
    - Antes: alinhar cenários e critérios, revisar riscos e dependências, combinar a estratégia de testes.
    - Durante: tirar dúvidas rapidamente, explorar cenários com o Dev, apoiar testes de unidade e API, preparar dados e ambiente.
    - Ganho: feedback mais rápido, menos retrabalho, defeitos encontrados mais perto da origem e maior confiança.

5. **Testes e QA**: testar continua essencial, mas agora chega apoiado por todo o trabalho anterior. O que validar:
    - Caminho principal: alterar e salvar o endereço
    - Regras: quando pode e quando não pode alterar
    - Exceções: CEP inválido, integração indisponível
    - Integração: propagação entre sistemas
    - Experiência: mensagens, mobile, acessibilidade
    - Regressão: o que já funcionava continua funcionando?

6. **Deploy e entrega**: a pergunta deixa de ser só "passou nos testes?" e vira "estamos seguros para liberar?". Verifica-se: critérios de saída atendidos, riscos conhecidos e aceitos, evidências disponíveis, plano de rollback e monitoramento preparado. A qualidade apoia a decisão, mas não "assina" sozinha a responsabilidade pelo release.

7. **Operação, manutenção e feedback**: o usuário real mostra comportamentos e contextos que nenhum ambiente reproduz 100%.
    - Observar: erros e incidentes, logs e alertas, performance, feedback do usuário.
    - Aprender: o que escapou? Por quê? Qual risco não vimos? Qual teste ou processo precisa evoluir?
    - Melhorar: atualizar cenários, fortalecer a automação, ajustar critérios, evitar recorrência.

## Qualidade é um ciclo de feedback

Cada etapa do SDLC produz informações que melhoram as decisões da seguinte, e o QA conecta esses feedbacks. O ciclo passa por quatro movimentos: **descobrir, construir, aprender e validar.**

A qualidade é responsabilidade do time inteiro: cada área tem um papel essencial, e juntas entregam valor com qualidade. O melhor cenário não é "o QA garante a qualidade", e sim "o time constrói qualidade".

## Do QA gargalo ao QA enabler

A forma de atuar do QA muda o fluxo do time inteiro.

|  | QA como etapa final | QA de ponta a ponta |
| - | ------------------ | ------------- |
| Fluxo | O Dev termina e o QA recebe | O QA participa cedo |
| Riscos | Aparecem no fim |Aparecem antes |
| Feedback | Lento, com retrabalho concentrado no final | Contínuo, com prevenção |
| Papel do QA | Gargalo | Enabler (quem habilita o time) |

### O custo da descoberta tardia

Quanto mais tarde um defeito é descoberto, maior tende a ser o impacto. A cadeia de consequências vai de retrabalho para atraso, depois operação, cliente e, por fim, reputação. Encontrar cedo previne custo e exposição.

### Shift-left

Esse movimento de antecipar os testes tem nome: shift-left, que é testar e pensar em qualidade mais cedo no ciclo. Ele será aprofundado na Aula 11.


## Ideias-chave para levar

- A qualidade começa no requisito, e não quando o código chega para testar.
- Quanto mais cedo o QA entra, menor o custo de retrabalho.
- Em cada etapa do SDLC, o QA faz perguntas diferentes sobre a mesma funcionalidade.
- Requisitos claros reduzem interpretações diferentes e servem de base para desenvolvimento, testes e aceite.
- A qualidade é um ciclo de feedback, e o time inteiro a constrói.
- O QA ponta a ponta é enabler, e não gargalo.
- Descobrir defeitos tarde custa mais: shift-left é antecipar a qualidade.
- A qualidade apoia a decisão de liberar, mas não assume sozinha a responsabilidade pelo release.

## Perguntas para fixar

1. Por que o QA deve entrar já no requisito, e não só na etapa de testes?
2. Dê duas perguntas de QA para a etapa de requisitos de "Cliente pode alterar o endereço".
3. Qual a diferença entre QA gargalo e QA enabler?
4. Por que "passou nos testes" não basta para decidir liberar uma entrega?
5. O que significa shift-left e por que ele reduz custo?

## Glossário rápido

| Termo | Definição |
| ----- | --------- |
| Critério de aceite | Condição que a funcionalidade precisa cumprir para ser aceita |
| Critério de saída | Condição para liberar uma entrega |
| Rollback | Voltar à versão anterior se algo der errado |
| Regressão | Verificar que o que já funcionava continua funcionando |


## Tarefa de Casa

**Desafio:** em que momento você faria essa pergunta?

1. Quem realmente precisa dessa funcionalidade?
    <details>
        <summary><b>Resposta</b></summary>
        1. Planejamento e descoberta

    </details>
2. E se o CEP não existir?
    <details>
        <summary><b>Resposta</b></summary>
        2. Requisitos e critérios de aceite
    </details>
3. Como saberemos que todos os sistemas atualizaram?
    <details>
        <summary><b>Resposta</b></summary>
        5. Testes e QA
    </details>
4. Qual mensagem aparece se falhar?
    <details>
        <summary><b>Resposta</b></summary>
        3. Análise, design e arquitetura
    </details>
5. Como voltamos atrás se o deploy der problema?
    <details>
        <summary><b>Resposta</b></summary>
        6. Deploy e entrega
    </details>
6. Como saberemos em produção se aumentaram os erros?
    <details>
        <summary><b>Resposta</b></summary>
        7. Operação, manutenção e feedback
    </details>