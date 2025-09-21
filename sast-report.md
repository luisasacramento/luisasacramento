# Relatório SAST – Semgrep
**Data:** 21/09/2025  
**Ferramenta:** Semgrep (CI/CD GitHub Actions)  
**Objetivo:** Identificar vulnerabilidades de código-fonte antes do build.

---

## Sumário
- **Total de achados:** 6  
- **Severidade:**
  - Critical: 1
  - High: 2
  - Medium: 2
  - Low: 1

---

## Vulnerabilidades Encontradas

| Severidade | Arquivo         | Linha | Regra          | Descrição                        | Correção Sugerida                                   |
|------------|-----------------|-------|----------------|----------------------------------|----------------------------------------------------|
| Critical   | `src/auth.py`   | 45    | `python.eval`  | Uso inseguro de `eval()`         | Substituir por parser seguro ou lógica controlada. |
| High       | `src/db.py`     | 112   | `sql-injection`| Query SQL concatenada diretamente| Usar parâmetros preparados (ex.: cursor.execute(...))|
| High       | `src/app.py`    | 78    | `xss-reflected`| Saída não sanitizada no HTML      | Sanitizar com biblioteca de templates.             |
| Medium     | `src/utils.py`  | 21    | `hardcoded-key`| Chave API em string literal       | Mover chave para variáveis de ambiente seguras.    |
| Medium     | `src/config.py` | 10    | `debug-mode`   | Aplicação em debug ativado        | Desativar debug em produção.                       |
| Low        | `src/app.py`    | 200   | `print-debug`  | Uso de `print()` para log         | Substituir por logger configurado.                 |

---

## Recomendações Gerais
- Revisar funções inseguras (`eval`, `exec`).
- Implementar variáveis de ambiente para credenciais.
- Sanitizar dados antes de enviar ao front-end.
- Desativar **debug mode** em produção.
