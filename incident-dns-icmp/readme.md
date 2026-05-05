# 🌐 Cybersecurity Incident Report – DNS & ICMP Analysis

![Network Analysis](https://img.shields.io/badge/Network-DNS_&_ICMP-blue?style=flat)
![tcpdump](https://img.shields.io/badge/Tool-tcpdump-green?style=flat)
![Blue Team](https://img.shields.io/badge/Security-Blue_Team-blue?style=flat)
![Google Cybersecurity](https://img.shields.io/badge/Google-Cybersecurity_Certificate-4285F4?style=flat&logo=google)

> Exercício prático de análise de tráfego de rede com `tcpdump`, identificando uma falha de resolução DNS causada pela inacessibilidade da porta UDP 53.

---

## 🚨 Scenario

Múltiplos usuários relataram falha ao acessar `www.yummyrecipesforme.com`, recebendo o erro:

```
destination port unreachable
```

---

## 🔍 Key Findings

| Campo | Detalhe |
|---|---|
| **Protocolos envolvidos** | UDP (queries DNS) + ICMP (mensagens de erro) |
| **IP do servidor DNS** | `203.0.113.2` |
| **Porta afetada** | UDP `53` (DNS) |
| **Causa raiz** | Porta UDP 53 inacessível — servidor DNS indisponível ou bloqueado |

---

## 🔄 Attack / Failure Flow

```
User Request → DNS Query (UDP 53) → 203.0.113.2
                                          ↓
                              Port 53 Unreachable
                                          ↓
                         ICMP Error Message returned
                                          ↓
                     ❌ www.yummyrecipesforme.com unreachable
```

---

## 🧪 Investigation Method

- 📡 Captura de tráfego com `tcpdump`
- 🔍 Identificação de padrões UDP e ICMP nos logs
- 📋 Documentação formal do incidente com causa raiz e recomendações

---

## 📄 Files

```
/
├── incident-report.pdf     ← Full incident analysis
├── tcpdump-log.txt         ← Captured traffic used in the investigation
└── screenshots/            ← Visual evidence from the investigation
```

---

## 🧠 Skills Demonstrated

- ✅ Network Traffic Analysis (tcpdump)
- ✅ DNS & ICMP Protocol Understanding
- ✅ Root Cause Identification
- ✅ Incident Report Writing
- ✅ UDP/TCP Protocol Analysis

---

## 🔒 Relevance

Este projeto demonstra habilidades práticas para atuação em:

`SOC Analyst` · `Network Security Analyst` · `Blue Team` · `Incident Responder`

---

*Projeto desenvolvido como parte do Google Cybersecurity Professional Certificate.*
