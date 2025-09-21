# Relatório SCA – Dependências de Terceiros
**Data:** 21/09/2025  
**Ferramenta:** Snyk (GitHub Actions)  
**Objetivo:** Detectar bibliotecas vulneráveis e desatualizadas.

---

## Sumário
- **Total de dependências analisadas:** 42  
- **Vulnerabilidades:** 3 (1 High, 2 Medium)

---

## Achados

| Severidade | Biblioteca      | Versão Atual | CVE         | Descrição                         | Versão Sugerida |
|------------|----------------|--------------|-------------|-----------------------------------|-----------------|
| High       | `lodash`       | 4.17.15      | CVE-2021-23337 | Prototype Pollution               | >= 4.17.21      |
| Medium     | `axios`        | 0.19.0       | CVE-2020-28168 | SSRF Vulnerability                | >= 0.21.1       |
| Medium     | `spring-core`  | 5.2.0.RELEASE| CVE-2020-5421 | Data Binding RCE                  | >= 5.2.3        |

---

## Plano de Ação
1. Atualizar `lodash` imediatamente (High).  
2. Planejar atualização de `axios` e `spring-core` em próxima release.  
3. Adotar ferramenta de monitoramento contínuo (Snyk/Dependabot).
