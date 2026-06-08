# Surplus: Reverse Engineering, Deobfuscation & Incident Report

## 📌 Executive Summary & The Theft
**Surplus** is a third-party JavaScript client modification for **survev.io**, which is functionally a direct, uncredited fork of my original open-source project, [**KrityHack**](https://github.com/Drino955/survev-krityhack). 

The operators behind Surplus ("noam" and "mahdi") appropriated the KrityHack source code, implemented a rudimentary UI, added a basic injection system via prototype hooking, and heavily obfuscated the payload to conceal the plagiarism. When confronted with the deobfuscated evidence, the operators denied the theft. This repository serves as both a technical breakdown of their obfuscation methods and a public warning regarding the operators' background.

## 🛠️ Technical Analysis: Defeating js-confuser

### The Obfuscation Layer
To hide the stolen logic, the operators applied **js-confuser** at its peak obfuscation level (version 1.2). This caused severe performance degradation and latency for end-users. 

### Deobfuscation & LLM Integration
The reverse engineering process required bypassing standard minification and complex control-flow flattening:
1. **AST Analysis**: Manual Abstract Syntax Tree analysis was required to strip dummy nodes. 
2. **Context-Window Challenges**: The obfuscated payload was extremely dense (68KB of string literals). Standard LLMs (GPT-4, Claude) failed during the reconstruction process due to context-window limitations.
3. **Reconstruction**: The final logic was successfully parsed and reconstructed by leveraging large-context models (**Google Gemini** and **Grok**). 

The deobfuscated core proved to be a 1:1 match with KrityHack's functionality.

## ⚠️ Threat Actor Profiles & Malicious Activity
As a security researcher, it is my obligation to warn the community about the operators distributing this code. Both individuals have a documented history of scams and toxic behavior. **Do not trust their software, as it poses a significant risk to users.**

## 🤝 Acknowledgments & Contact
Massive respect to **askile** for executing the AST analysis and breaking the `js-confuser` protection.

**Victim Contact:** If you have been scammed by Mahdi or Noam, or have further information regarding their fraudulent activities, please reach out:
- 📲 Telegram: [t.me/drino955](https://t.me/drino955)
- 🎮 Discord: **drino955**
