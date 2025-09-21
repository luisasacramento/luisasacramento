# Documentação do Pipeline de Segurança CI/CD

**Data:** 21/09/2025  
**Ferramentas integradas:** Semgrep (SAST), Snyk/Dependency-Check (SCA), OWASP ZAP (DAST).  
**Ambiente:** GitHub Actions.  

---

## Arquitetura do Pipeline
1. **CI (Build/Test):**
   - Rodar SAST (Semgrep) em cada commit/pull request.
   - Rodar SCA (Snyk/Dependency-Check) em cada commit/pull request.
   - Gerar relatórios (`semgrep.json`, `snyk.json` ou `dependency-check-report`).

2. **CD (Deploy em Staging):**
   - Após deploy em staging, executar DAST (OWASP ZAP).
   - Bloquear deploy se vulnerabilidades **High/Critical** forem detectadas.

3. **Monitoramento Contínuo:**
   - Gatilhos automáticos em `push` e `pull_request`.
   - Notificação via Slack/Email em caso de falha.
   - Artefatos armazenados nos workflows.

---

## Políticas de Segurança
- **Blocking:** Merge/Deploy bloqueado se `semgrep_high_count > 0` ou `snyk_high_count > 0`.  
- **Critical Patch:** Vulnerabilidades High/Critical devem ser corrigidas antes da release.  
- **Branch Protection:** Ativado em `main` para exigir status checks de segurança.

---

## Exemplo de Execução
- **Commit:** `abc123`  
- **Logs:** Workflow `Security CI/CD` executado com sucesso.  
- **Alertas:** 1 Critical (SAST), 1 High (SCA), 1 High (DAST).  
- **Ação:** Pipeline bloqueado até correção.

---

## Capturas de Evidência
- Screenshot de execução no GitHub Actions.  
- Arquivos `.json`/`.html` dos relatórios anexados.  
- Print da configuração de Branch Protection.

---

## Próximos Passos
1. Automatizar correções de dependências com **Dependabot**.  
2. Integrar relatórios no **dashboard Semgrep/Snyk**.  
3. Criar política de *Security Champions* no time de desenvolvimento.
