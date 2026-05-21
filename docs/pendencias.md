# Pontos Pendentes de Definição

Os itens abaixo foram identificados durante o discovery e precisam ser definidos antes do início da fase de Plan (ADRs e Specs).

---

## Modelo de monetização e precificação

> **PENDENTE:** Definir a lógica de precificação do serviço que seja atrativa para cliente, advogado e plataforma. A direção inicial considerada envolve um modelo previsível para ambas as partes (ex.: taxa de deslocamento + valor base), evitando que cliente ou advogado sejam surpreendidos quanto ao valor. Como o gateway de pagamentos está fora do MVP, o pagamento ocorrerá fora da plataforma, mas o sistema pode exibir valores de referência. **Definir antes da escrita das specs.**

---

## Operacionalização da aprovação de cadastros

> **PENDENTE:** Definir quem e como aprovará os cadastros de advogados, dado que não há persona administrativa formalizada no MVP. Possíveis abordagens: aprovação manual por um dos fundadores, integração com fontes externas que automatizam parte da validação, ou criação de área administrativa mínima.

---

## Critério de desempate e fallback no matching

> **PENDENTE:** Em caso de empate de proximidade ou recusa em cadeia, definir critérios secundários de matching (ex.: tempo desde a última aceitação, avaliação histórica, ordem aleatória).

---

## Conformidade regulatória

> **PENDENTE:** Conforme detalhado em [Considerações Regulatórias](regulatorio.md).
