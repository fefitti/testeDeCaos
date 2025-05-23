# 🧪 Manual Prático: Teste de Caos (Chaos Testing)

## 🔍 O que é o Teste de Caos?

O **Teste de Caos** é uma técnica que injeta falhas controladas em um sistema para observar seu comportamento diante de imprevistos. O objetivo é **garantir a resiliência** do sistema em situações inesperadas.

---

## 🎯 Objetivo

- Avaliar a **resiliência** do sistema.
- Identificar **pontos fracos** antes que causem falhas em produção.
- Testar se o sistema responde **corretamente a falhas**.

---

## 🛠️ Como Aplicar o Teste de Caos

### 1. Estabeleça o comportamento esperado (estado estável)
Defina como o sistema **deve funcionar normalmente**.  
Exemplo: "O endpoint `/usuarios` deve responder em menos de 1 segundo".

### 2. Escolha o componente a ser testado
Exemplos:
- Servidor de aplicação
- Banco de dados
- Rede
- Serviço externo

### 3. Defina o experimento
Decida qual falha será simulada:
- Parada de um serviço (ex: matar processo)
- Latência de rede
- Perda de conexão com o banco de dados

### 4. Monitore o sistema
Utilize ferramentas de **logs, métricas e alertas** para acompanhar o comportamento do sistema.

### 5. Execute o teste
Aplique a falha no ambiente de teste (ou produção com controle).

### 6. Analise os resultados
- O sistema se recuperou?
- Os alertas funcionaram?
- Houve impacto nos usuários?

### 7. Aja com base nos resultados
- Corrija falhas identificadas
- Melhore os mecanismos de tolerância a falhas

---

## ⚠️ Boas Práticas

- **Comece com falhas pequenas** e controladas.
- Nunca teste em produção sem **controle e rollback**.
- Utilize ferramentas como:
  - [Chaos Monkey (Netflix)](https://github.com/Netflix/chaosmonkey)
  - [Gremlin](https://www.gremlin.com/)
  - [Chaos Mesh](https://chaos-mesh.org/)

---

## 💡 Exemplo Prático

### Cenário

Sistema com:
- Backend em Node.js
- Banco de dados PostgreSQL
- Hospedagem em servidor Linux

### Objetivo

Testar o comportamento da API quando o banco de dados falha.

### Passo a Passo

1. **Comportamento esperado**:
   - A API responde corretamente nos endpoints `/produtos` e `/usuarios`.

2. **Simulação de falha**:
   ```bash
   sudo systemctl stop postgresql
   ```

3. **Durante o teste**:
   - Verifique os logs da API
   - Teste os endpoints: retornam erro? A aplicação trava?

4. **Recuperação**:
   ```bash
   sudo systemctl start postgresql
   ```

5. **Resultados esperados**:
   - A API deve capturar o erro e retornar resposta amigável
   - A aplicação deve continuar operando para outros serviços

---

## ✅ Conclusão

Chaos Testing é uma prática essencial para sistemas modernos que exigem **alta disponibilidade**.  
Testes regulares ajudam a prever e corrigir falhas antes que causem impacto real.

---

> 💬 *"A verdadeira resiliência é construída com falhas controladas e aprendizados constantes."*
