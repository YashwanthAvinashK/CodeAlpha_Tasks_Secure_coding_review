[README.md](https://github.com/user-attachments/files/28739558/README.md)
# CodeAlpha_Tasks_Secure_coding_review
Secur# 🛡️ SecureAudit — AI-Powered Code Security Scanner

> An interactive, AI-powered static code analysis tool that performs deep security audits across multiple programming languages, maps findings to OWASP Top 10, and delivers actionable remediation guidance — all in the browser.

![SecureAudit Banner](https://img.shields.io/badge/Security-Audit%20Tool-4f46e5?style=for-the-badge&logo=shield&logoColor=white)
![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Claude AI](https://img.shields.io/badge/Powered%20by-Claude%20AI-orange?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

---

## 📸 Preview

```
┌─────────────────────────────────────────────────────────┐
│  🛡️ SecureAudit          AI-Powered Code Security Scanner │
├─────────────────────────────────────────────────────────┤
│  Language:  🐍 Python  ⚡ JS  🐘 PHP  ☕ Java  🔵 Go   │
├─────────────────────────────────────────────────────────┤
│  [ Code Editor — paste or use sample code ]             │
│                                                         │
│  [ 🔍 Run Security Audit ]                              │
├──────────────────┬──────────────────────────────────────┤
│   Security Score │  Executive Summary                   │
│       32 / 100   │  6 findings: 2 Critical, 3 High...  │
│   ● Critical Risk│                                      │
├─────────────────────────────────────────────────────────┤
│  🔴 Findings  │  🗂 OWASP Mapping  │  ✅ Best Practices │
├─────────────────────────────────────────────────────────┤
│  [1] 🔴 SQL Injection                    CRITICAL       │
│      Line 12 · Injection                               │
│      ▼ Expand for snippet, fix, CWE reference          │
└─────────────────────────────────────────────────────────┘
```

---

## ✨ Features

- **Multi-language support** — Python, JavaScript, PHP, Java, Go, SQL
- **AI-powered analysis** — Uses Claude Sonnet to detect real vulnerabilities
- **OWASP Top 10 mapping** — Every finding mapped to the 2021 standard
- **Severity scoring** — Critical / High / Medium / Low / Info classification
- **Remediation guidance** — Vulnerable snippet + corrected code for every finding
- **CWE references** — Industry-standard weakness identifiers
- **Security score gauge** — Visual 0–100 posture score
- **Best practices panel** — Language-specific secure coding recommendations
- **Sample vulnerable code** — Pre-loaded examples for each language to learn from

---

## 🔍 Vulnerability Categories Detected

| Category | Examples |
|---|---|
| **Injection** | SQL Injection (CWE-89), Command Injection (CWE-78), XXE |
| **Broken Auth** | Hardcoded credentials, weak JWT secrets, missing rate limits |
| **Crypto Failures** | MD5/SHA1 password hashing, plaintext secrets, no TLS |
| **XSS** | Reflected XSS, stored XSS, unescaped output (CWE-79) |
| **Insecure Design** | Path traversal (CWE-22), unrestricted file upload |
| **Deserialization** | Pickle, ObjectInputStream, unsafe `unserialize()` |
| **Data Exposure** | PII in logs, stack traces to client, unencrypted PII at rest |
| **Misconfiguration** | `phpinfo()`, debug mode, overly permissive DB grants |

---

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- An Anthropic API key → [Get one here](https://console.anthropic.com/)

### Installation

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/secureaudit.git
cd secureaudit

# Install dependencies
npm install

# Add your API key
cp .env.example .env
# Edit .env and add: VITE_ANTHROPIC_API_KEY=your_key_here

# Start the dev server
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### Build for Production

```bash
npm run build
npm run preview
```

---

## 🏗️ Project Structure

```
secureaudit/
├── src/
│   ├── App.jsx              # Root component
│   ├── components/
│   │   ├── SecurityAuditTool.jsx   # Main audit interface
│   │   ├── FindingCard.jsx          # Expandable vulnerability card
│   │   ├── ScoreGauge.jsx           # SVG security score ring
│   │   └── SeverityBadge.jsx        # Color-coded severity pill
│   ├── data/
│   │   └── sampleCode.js            # Vulnerable code samples per language
│   └── main.jsx
├── public/
├── .env.example
├── .github/
│   └── workflows/
│       └── deploy.yml       # GitHub Pages auto-deploy
├── package.json
└── README.md
```

---

## 🧠 How It Works

1. **You paste code** (or use a built-in sample) and select the language.
2. **The app calls Claude Sonnet** via the Anthropic API with a security-focused system prompt.
3. **Claude returns structured JSON** with findings, severity, OWASP mapping, and fixes.
4. **The UI renders** an interactive report with expandable cards, OWASP bar chart, and best practices.

```
User Code
    │
    ▼
Anthropic API (claude-sonnet-4-20250514)
    │
    ▼
Structured JSON Report
    │
    ▼
Interactive UI (Findings + OWASP + Best Practices)
```

---

## 📋 Sample Report Output (JSON)

```json
{
  "language": "Python",
  "score": 18,
  "summary": "This Flask application contains multiple critical vulnerabilities...",
  "findings": [
    {
      "id": "VULN-001",
      "title": "SQL Injection via String Concatenation",
      "severity": "critical",
      "category": "Injection",
      "cwe": "CWE-89",
      "line": "12",
      "description": "User input is directly interpolated into a SQL query...",
      "snippet": "query = \"SELECT * FROM users WHERE username = '\" + username + \"'\"",
      "fix": "cursor.execute('SELECT * FROM users WHERE username = ?', (username,))",
      "references": ["OWASP A03:2021", "CWE-89"]
    }
  ],
  "bestPractices": [...],
  "owaspMapping": { "A03:2021": 3, "A02:2021": 2 }
}
```

---

## 🛡️ OWASP Top 10 Coverage

| ID | Category | Detected |
|---|---|---|
| A01:2021 | Broken Access Control | ✅ |
| A02:2021 | Cryptographic Failures | ✅ |
| A03:2021 | Injection | ✅ |
| A05:2021 | Security Misconfiguration | ✅ |
| A06:2021 | Vulnerable & Outdated Components | ✅ |
| A08:2021 | Software and Data Integrity Failures | ✅ |
| A09:2021 | Security Logging and Monitoring Failures | ✅ |

---

## ⚙️ Configuration

| Variable | Description | Required |
|---|---|---|
| `VITE_ANTHROPIC_API_KEY` | Your Anthropic API key | ✅ Yes |

> ⚠️ **Never commit your API key.** The `.env` file is in `.gitignore` by default.

---

## 🤝 Contributing

Contributions are welcome!

```bash
# Fork the repo, then:
git checkout -b feature/add-ruby-support
git commit -m "feat: add Ruby vulnerability patterns"
git push origin feature/add-ruby-support
# Open a Pull Request
```

**Ideas for contributions:**
- Add more languages (Ruby, C/C++, Rust, TypeScript)
- Improve detection prompts for specific vulnerability classes
- Add export to PDF / Markdown report
- Add GitHub Actions integration for CI/CD scanning
- Add diff view showing original vs. fixed code side-by-side

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

---

## 🙏 Acknowledgements

- [Anthropic Claude](https://anthropic.com) — AI backbone for vulnerability analysis
- [OWASP Top 10](https://owasp.org/www-project-top-ten/) — Security standard reference
- [CWE / MITRE](https://cwe.mitre.org/) — Common Weakness Enumeration database
- [React](https://react.dev) — UI framework

---

## ⚠️ Disclaimer

SecureAudit is a **learning and awareness tool**. It is not a replacement for professional penetration testing, a certified security audit, or tools like Semgrep, Snyk, or SonarQube in a production pipeline. Always validate findings manually and consult a security professional for critical systems.

---

<p align="center">Built with ❤️ for secure software development</p>
