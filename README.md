# README — Plataforma de Atendimento Jurídico Sob Demanda (MVP)

> **Tipo:** Documento de visão do projeto  
> **Status:** Requirements concluídos — aguarda apenas validação jurídica regulatória antes dos ADRs  
> **Metodologia:** Spec-Driven Development com RPI Method (Requirements → Plan → Implementation)

---

## Sumário

1. [Visão geral](#visão-geral)
2. [Problema que o sistema resolve](#problema-que-o-sistema-resolve)
3. [Proposta de valor](#proposta-de-valor)
4. [Usuários e personas](#usuários-e-personas)
5. [Escopo do MVP](#escopo-do-mvp)
6. [Modelo de monetização](#modelo-de-monetização)
7. [Fora do escopo do MVP](#fora-do-escopo-do-mvp)
8. [Restrições técnicas e de projeto](#restrições-técnicas-e-de-projeto)
9. [Considerações regulatórias](#considerações-regulatórias)
10. [Pontos pendentes de definição](#pontos-pendentes-de-definição)
11. [Próximos passos](#próximos-passos)

---

## Visão geral

Plataforma web responsiva que conecta pessoas em necessidade de atendimento jurídico a advogados disponíveis e próximos geograficamente, no modelo de chamado sob demanda — inspirado em aplicativos de mobilidade urbana.

O MVP foca exclusivamente em **atendimentos presenciais** disparados sob demanda, com matching automático por proximidade.

---

## Problema que o sistema resolve

O projeto endereça um conjunto de dores comuns vividas por pessoas que precisam de atendimento jurídico mas não fazem parte de redes sociais ou profissionais que facilitam esse acesso:

1. **Falta de network** com profissionais da advocacia
2. **Ausência de um espaço centralizado** que reúna prestadores de serviços jurídicos
3. **Falta de referência de preço** para serviços emergenciais, levando a cobranças abusivas
4. **Dificuldade em encontrar profissionais próximos e acessíveis** no momento de necessidade
5. **Desconhecimento sobre a área jurídica adequada** para o problema enfrentado
6. **Necessidade de atendimento em região desconhecida**, sem rede local de contatos
7. **Situações de emergência** sem contatos disponíveis para ajudar

Do lado do advogado, o sistema resolve a dificuldade de encontrar clientes próximos que estejam dispostos a contratar serviços imediatos.

---

## Proposta de valor

O diferencial do produto está em duas frentes complementares:

- **Para o cliente:** facilidade de encontrar advogados dispostos a resolver seu problema, com proximidade geográfica e disponibilidade imediata.
- **Para o advogado:** facilidade de captar clientes geograficamente próximos que demandam serviços no momento.

A plataforma atua como camada de intermediação que reduz fricção entre as duas pontas.

---

## Usuários e personas

### Cliente

Pessoa física que enfrenta uma situação que demanda atendimento jurídico e que não possui rede de contatos ou conhecimento prévio para resolver o problema por conta própria. Caracteriza-se por:

- Não ter vivência prévia com serviços jurídicos
- Não ter conhecimento sobre qual tipo de profissional procurar
- Estar em situação onde precisa de resposta rápida

### Advogado

Profissional da advocacia regularmente inscrito na OAB, interessado em captar clientes próximos para atendimento imediato. Será submetido a processo de validação que inclui:

- Verificação do registro ativo na OAB
- Validação de especialidades
- Validação de tempo de experiência
- Validação de credenciais e formações
- Verificação de antecedentes (modelo similar a aplicativos de mobilidade)
- Validação documental para comprovação de integridade

### Administrador

Não haverá persona administrativa no MVP. A validação de cadastro de advogado é automatizada — sem aprovação humana envolvida (ver seção Escopo do MVP).

---

## Escopo do MVP

### Funcionalidades obrigatórias

**1. Cadastro e login**
- Cadastro de cliente
- Cadastro de advogado (sujeito a aprovação)
- Login para ambos os perfis

**2. Validação de advogado (automatizada)**
- Advogado realiza o cadastro fornecendo documentos e informações
- Validação ocorre no momento do cadastro via **selfie** + **consulta ao CNA (Conselho Nacional da Advocacia)**
- Aprovação automática ao término da validação; sem aprovação manual humana
- Após aprovação, advogado passa a ter acesso ao matching

**3. Disponibilidade controlada pelo advogado**
- Advogado possui controle explícito sobre sua disponibilidade
- Botão para entrar no matching (ficar online)
- Botão para sair do matching (ficar offline)
- Apenas advogados online participam do disparo de chamados

**4. Chamado sob demanda com matching por proximidade**
- Cliente abre um chamado pela plataforma
- Sistema identifica o advogado online mais próximo geograficamente (critério primário: **distância**)
- Em caso de empate de distância, o desempate é pelo **tempo online** (quem está online há mais tempo)
- Chamado é disparado para esse advogado, no modelo de aplicativos de mobilidade
- Advogado tem **30 segundos** para aceitar ou recusar; após o timeout, o sistema avança para o próximo
- Em caso de recusa ou timeout, o sistema dispara para o próximo advogado mais próximo
- O raio máximo de busca é de **10 km**; se nenhum advogado disponível for encontrado dentro desse raio, o chamado falha com mensagem ao cliente

**5. Remoção do advogado do matching após aceite**
- Ao aceitar um chamado, o advogado é automaticamente removido do pool de matching
- Advogado só retorna ao pool após conclusão do atendimento ou ação explícita

**6. Chat entre cliente e advogado**
- Após aceite do chamado, é aberto canal de comunicação entre as partes
- Comunicação ocorre dentro da plataforma

### Plataforma de entrega

Aplicação web responsiva, acessível por navegadores em desktop e dispositivos móveis.

### Escopo geográfico

Atendimento nacional desde o lançamento do MVP.

---

## Modelo de monetização

| Componente | Valor |
|---|---|
| Taxa base | R$ 25,00 |
| Taxa de deslocamento | R$ 2,50 por km percorrido pelo advogado até o cliente |

**Exemplo:** advogado percorre 5 km → R$ 25,00 + (5 × R$ 2,50) = **R$ 37,50**.

- O pagamento ocorre **fora da plataforma** no MVP — gateway de pagamentos está fora do escopo.
- A plataforma exibe o valor estimado de referência antes do aceite do chamado.
- O cálculo é baseado na distância entre a localização do advogado e o endereço do cliente no momento do chamado.

---

## Fora do escopo do MVP

As funcionalidades abaixo foram identificadas como desejáveis para versões futuras, mas estão explicitamente fora do MVP:

1. Gateway de pagamentos integrado à plataforma
2. Flexibilidade na precificação do serviço (ex.: "preço a negociar")
3. Atendimento remoto via vídeo chamada
4. Perfil verificado com benefícios pagos (modelo similar ao LinkedIn Premium)
5. Busca de profissionais cadastrados em outras regiões para casos não urgentes
6. Exibição de currículo completo do advogado com graduações e certificações
7. Seção de profissionais favoritos do cliente
8. Perfil expandido do advogado com tempo de profissão e quantidade de processos
9. Filtro e seleção por especialidade jurídica
10. Persona e área administrativa dedicada

---

## Restrições técnicas e de projeto

| Item | Definição |
|---|---|
| Plataforma | Aplicação web responsiva |
| Prazo | 3 meses para entrega do MVP |
| Equipe | 2 desenvolvedores |
| Apoio em desenvolvimento | Claude Code |
| Stack tecnológica | _PENDENTE_ — será definida em ADRs específicas |
| Infraestrutura | _PENDENTE_ — será definida em ADRs específicas |

---

## Considerações regulatórias

O exercício da advocacia no Brasil é regulado pela Ordem dos Advogados do Brasil. O **Provimento 205/2021 do Conselho Federal da OAB** estabelece restrições relevantes para plataformas digitais que intermedeiam serviços advocatícios.

> **PENDENTE DE ESPECIFICAÇÃO:** Análise jurídica do Provimento 205/2021 e seus impactos no modelo de negócio. Pontos a serem avaliados antes do lançamento incluem regras sobre captação de clientela, publicidade profissional e mercantilização da advocacia. A conformidade regulatória pode impactar diretamente o design de funcionalidades centrais do MVP.

> Link de referência: https://www.oab.org.br/leisnormas/legislacao/provimentos/205-2021

---

## Pontos pendentes de definição

### Conformidade regulatória

> **PENDENTE:** Análise do Provimento 205/2021 da OAB e seus impactos no modelo de negócio. Pontos a serem avaliados incluem regras sobre captação de clientela, publicidade profissional e mercantilização da advocacia.
>
> **Compromisso registrado:** realizar validação jurídica leve (1–2h com advogado especializado em ética da advocacia) antes do início do desenvolvimento. A análise pode impactar funcionalidades centrais como o modelo de matching, a exibição de valores e a comunicação entre as partes.

---

### Itens resolvidos pelo PO

| Decisão | Onde encontrar |
|---|---|
| Modelo de monetização | [Modelo de monetização](#modelo-de-monetização) |
| Validação de cadastro de advogado | [Escopo do MVP — item 2](#escopo-do-mvp) |
| Critérios de matching e fallback | [Escopo do MVP — item 4](#escopo-do-mvp) |

---

## Próximos passos

Seguindo o RPI Method e a metodologia Spec-Driven Development, os próximos passos do projeto são:

**1. Validação e fechamento dos pontos pendentes**  
A maioria dos pontos pendentes foi validada pelo PO. Resta apenas a conformidade regulatória: realizar validação jurídica leve (1–2h com advogado especializado em ética da advocacia) antes do início do desenvolvimento.

**2. Geração das ADRs (Architecture Decision Records)**  
Com o README validado, serão definidas as decisões arquiteturais estruturais — stack tecnológica, modelo de persistência, estratégia de geolocalização, abordagem de autenticação, infraestrutura de hospedagem, entre outras.

**3. Geração das Specs**  
Com README e ADRs consolidados, cada funcionalidade do escopo do MVP será detalhada em uma spec própria, descrevendo comportamento esperado, regras de negócio, contratos de interface e critérios de qualidade.

**4. Geração dos Guides**  
Documentação de apoio para o time, incluindo convenções de código, fluxo de contribuição e uso de LLMs durante o desenvolvimento.

**5. Geração das Tasks**  
Com as specs prontas, cada uma será decomposta em tasks executáveis com escopo fechado, critério de aceite e dependências declaradas.

---

*Documento gerado seguindo princípios de Spec-Driven Development e RPI Method para uso do time de desenvolvimento.*
