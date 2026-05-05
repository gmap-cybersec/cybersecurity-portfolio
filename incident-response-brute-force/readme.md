# 🍴 Security Incident Report – YummyRecipesForMe.com

![Incident Response](https://img.shields.io/badge/Incident-Response-red?style=flat)
![Blue Team](https://img.shields.io/badge/Security-Blue_Team-blue?style=flat)
![Google Cybersecurity](https://img.shields.io/badge/Google-Cybersecurity_Certificate-4285F4?style=flat&logo=google)

> Simulação de um incidente real de segurança envolvendo ataque de força bruta e redirecionamento de malware em um site de receitas. O projeto documenta a investigação completa, análise de tráfego de rede e recomendações de resposta.

---

## 🕵️ Scenario

Um ex-funcionário insatisfeito realizou um ataque de força bruta para obter acesso administrativo ao site `yummyrecipesforme.com`.

**Cadeia de ataque:**

```
Brute Force → Admin Access → Source Code Modification
→ Malicious JS Injection → User Download Prompt
→ Redirect to greatrecipesforme.com → Malware Execution
```

| Etapa | Detalhe |
|---|---|
| 🔓 **Acesso inicial** | Brute force na conta administrativa |
| 💉 **Injeção** | JavaScript malicioso inserido no código-fonte |
| 🎣 **Redirecionamento** | Usuários enviados para `greatrecipesforme.com` |
| 🦠 **Payload** | Download e execução de malware nos dispositivos das vítimas |

---

## 🔍 Tools Used

- ✅ `tcpdump` — Captura e análise de tráfego de rede
- ✅ Browser Sandbox — Observação comportamental do malware
- ✅ Protocol Analysis — Identificação de padrões DNS e HTTP suspeitos
- ✅ Incident Documentation — Registro formal do incidente

---

## 📄 Files Included

- 📝 [`incident_report.md`](./incident_report.md) — Full security incident report
- 📊 [`tcpdump_analysis.md`](./tcpdump_analysis.md) — Annotated tcpdump logs and interpretation

---

## 🧠 Key Concepts Demonstrated

- ✅ Network Protocol Analysis (DNS, HTTP)
- ✅ Brute Force Attack Detection & Mitigation
- ✅ Malware Redirection Tracking
- ✅ Professional Incident Report Writing (EN)
- ✅ tcpdump Log Interpretation

---

## ⚠️ Disclaimer

> Este projeto é uma simulação educacional realizada como parte de um curso de cibersegurança. Todos os cenários, domínios e dados são fictícios e destinados exclusivamente a fins de aprendizado e portfólio.

---

## 🔒 Relevance

Este projeto demonstra habilidades práticas para atuação em:

`SOC Analyst` · `Incident Responder` · `Blue Team` · `DFIR` · `Threat Analyst`

---

*Projeto desenvolvido como parte do Google Cybersecurity Professional Certificate.*
