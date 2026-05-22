# Escopo do MVP

## Funcionalidades obrigatórias

### 1. Cadastro e login

- Cadastro de cliente
- Cadastro de advogado (sujeito a aprovação)
- Login para ambos os perfis

### 2. Validação de advogado (modelo híbrido)

- Advogado realiza o cadastro fornecendo documentos e informações
- Cadastro permanece pendente até aprovação humana
- Após aprovação, advogado passa a ter acesso ao matching

### 3. Disponibilidade controlada pelo advogado

- Advogado possui controle explícito sobre sua disponibilidade
- Botão para entrar no matching (ficar online)
- Botão para sair do matching (ficar offline)
- Apenas advogados online participam do disparo de chamados

### 4. Chamado sob demanda com matching por proximidade

- Cliente abre um chamado pela plataforma
- Sistema identifica o advogado online mais próximo geograficamente
- Chamado é disparado para esse advogado, no modelo de aplicativos de mobilidade
- Advogado pode aceitar ou recusar o chamado
- Em caso de recusa, o sistema dispara para o próximo advogado mais próximo

### 5. Remoção do advogado do matching após aceite

- Ao aceitar um chamado, o advogado é automaticamente removido do pool de matching
- Advogado só retorna ao pool após conclusão do atendimento ou ação explícita

### 6. Chat entre cliente e advogado

- Após aceite do chamado, é aberto canal de comunicação entre as partes
- Comunicação ocorre dentro da plataforma

---

## Plataforma de entrega

Aplicação web responsiva, acessível por navegadores em desktop e dispositivos móveis.

## Escopo geográfico

Atendimento apenas de Brasília - DF desde o lançamento do MVP.
