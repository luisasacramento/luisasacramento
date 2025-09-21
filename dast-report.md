# Relatório DAST – OWASP ZAP
**Data:** 21/09/2025  
**Ferramenta:** OWASP ZAP Full Scan (GitHub Actions)  
**Alvo testado:** https://staging.seuapp.test  

---

## Sumário
- **Total de achados:** 4
- **Severidade:**
  - High: 1
  - Medium: 2
  - Low: 1

---

## Evidências

### 1. [High] Endpoint exposto sem autenticação
- **URL:** https://staging.seuapp.test/api/admin  
- **Payload usado:** `curl -X GET https://staging.seuapp.test/api/admin`  
- **Resposta:** Dados sensíveis retornaram sem autenticação.  
- **Mitigação:** Restringir endpoint com autenticação JWT.

---

### 2. [Medium] Cookie inseguro
- **Descrição:** Cookie `SESSIONID` sem flag `HttpOnly`.  
- **Risco:** Pode ser acessado via JavaScript (susceptível a XSS).  
- **Mitigação:** Ativar flag `HttpOnly` e `Secure`.

---

### 3. [Medium] Diretório listado
- **URL:** https://staging.seuapp.test/static/  
- **Descrição:** Permite listar arquivos do diretório.  
- **Mitigação:** Desativar autoindex no servidor web.

---

### 4. [Low] Header de segurança ausente
- **Descrição:** Falta `Content-Security-Policy`.  
- **Mitigação:** Configurar headers de segurança no servidor.

---

## Conclusão
O endpoint `/api/admin` deve ser tratado imediatamente. Outros pontos podem ser corrigidos em sprint de hardening.
