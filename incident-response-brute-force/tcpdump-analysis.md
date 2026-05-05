# 📊 TCPDump Packet Analysis – SYN Flood Incident

![tcpdump](https://img.shields.io/badge/Tool-tcpdump-green?style=flat)
![Network Analysis](https://img.shields.io/badge/Network-Packet_Analysis-blue?style=flat)

> Análise do tráfego de rede capturado durante um evento suspeito de negação de serviço (DoS). Este documento detalha os indicadores técnicos confirmando um ataque TCP SYN Flood.

---

## 🔍 Summary of Observations

A captura de pacotes revela um alto volume de handshakes TCP incompletos entre um único IP externo e o servidor web interno na porta 443 (HTTPS).

| Campo | Valor |
|---|---|
| **IP de origem (atacante)** | `203.0.113.0` |
| **IP de destino (servidor)** | `192.0.2.1` |
| **Porta alvo** | `443` (HTTPS) |
| **Porta de origem** | `54770` (consistente — indica automação ou spoofing) |
| **Flag observada** | `[SYN]` repetido sem `[ACK]` correspondente |

---

## 🚩 Key Indicators of Compromise (IOCs)

- 🔴 Alto volume de pacotes `[SYN]` do mesmo IP de origem
- 🔴 Ausência de pacotes `[ACK]` para completar o handshake
- 🔴 Mesma porta de origem (`54770`) usada consistentemente — indica spoofing ou automação
- 🔴 Tráfego sustentado ao longo de múltiplos segundos

---

## 🧪 Sample Log Entries

```
203.0.113.0 -> 192.0.2.1  TCP  54770→443  [SYN]
203.0.113.0 -> 192.0.2.1  TCP  54770→443  [SYN]
203.0.113.0 -> 192.0.2.1  TCP  54770→443  [SYN]
...
```

> Padrão típico de TCP SYN Flood: o atacante inicia múltiplas conexões mas nunca as completa.

---

## ⚙️ TCP Three-Way Handshake — Normal vs. Attack

**Normal:**
```
Client  →  [SYN]          →  Server
Client  ←  [SYN-ACK]      ←  Server
Client  →  [ACK]          →  Server  ✅ Connection established
```

**SYN Flood:**
```
Attacker  →  [SYN]        →  Server
Attacker  ←  [SYN-ACK]    ←  Server
Attacker  ✗  (no ACK)         Server ⏳ Half-open connection (resource allocated)
                                       ↓ Repeated × thousands
                                       ❌ Connection table full → DoS
```

---

## ⚠️ Technical Impact

| Consequência | Detalhe |
|---|---|
| 💾 **Alocação de recursos** | O servidor aloca memória para cada SYN recebido |
| ⏳ **Conexões half-open** | Sem ACK, conexões ficam abertas até o timeout |
| 📋 **Esgotamento da tabela** | A tabela de conexões se esgota, recusando novas conexões |
| 🚫 **Impacto ao usuário** | Timeouts e erros `504 Gateway Timeout` |

---

## 📌 Conclusion

O padrão e comportamento observados confirmam um ataque **TCP SYN Flood DoS**. O ataque foi provavelmente automatizado com o objetivo de esgotar os recursos do servidor e interromper a disponibilidade do serviço.

**Severidade:** 🔴 Alta  
**Confiança na conclusão:** ✅ Alta — padrão inequívoco nos logs

---

*Análise realizada como parte do Google Cybersecurity Professional Certificate.*
