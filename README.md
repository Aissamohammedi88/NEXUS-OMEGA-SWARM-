# NEXUS-OMEGA-SWARM-
Sovereign autonomous multi-agent system. 4 agents (Planner, Coder, Executor, Reflector) orchestrated via LangGraph and Ollama. Self-correction, sandboxed execution, and persistent memory via ChromaDB. 100% local, 0 hallucination. Architected by Aissa Mohammedi.
markdown

<!-- ═══════════════════════════════════════════════════════════════════════════
     NEXUS OMEGA SWARM - README
     L'Architecture Multi-Agents Souveraine
════════════════════════════════════════════════════════════════════════════ -->

<div align="center">

<!-- 🎬 BANNIÈRE ANIMÉE SVG -->
<svg width="850" height="200" viewBox="0 0 850 200" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="bg" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="#050810"/>
      <stop offset="100%" stop-color="#1a0b2e"/>
    </linearGradient>
    <linearGradient id="neon" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#00d4ff">
        <animate attributeName="stop-color" values="#00d4ff;#a855f7;#00d4ff" dur="4s" repeatCount="indefinite"/>
      </stop>
      <stop offset="100%" stop-color="#a855f7">
        <animate attributeName="stop-color" values="#a855f7;#00d4ff;#a855f7" dur="4s" repeatCount="indefinite"/>
      </stop>
    </linearGradient>
    <filter id="glow">
      <feGaussianBlur stdDeviation="4" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <rect width="850" height="200" fill="url(#bg)" rx="12"/>
  <rect x="2" y="2" width="846" height="196" fill="none" stroke="url(#neon)" stroke-width="2" rx="10" opacity="0.6"/>

  <text x="425" y="90" text-anchor="middle" font-family="ui-monospace, monospace" font-size="42" font-weight="900" fill="url(#neon)" filter="url(#glow)">
    NEXUS OMEGA SWARM
    <animate attributeName="opacity" values="1;0.8;1" dur="2s" repeatCount="indefinite"/>
  </text>
  
  <text x="425" y="130" text-anchor="middle" font-family="ui-monospace, monospace" font-size="16" fill="#e0f7fa" letter-spacing="4">
    AUTONOMOUS MULTI-AGENT SYSTEM
  </text>
  <text x="425" y="165" text-anchor="middle" font-family="ui-monospace, monospace" font-size="12" fill="#a855f7" letter-spacing="2">
    AISSA MOHAMMEDI (DGK) // NAIM MOHAMMEDI
  </text>
</svg>

<br/>

[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python)](#)
[![LangGraph](https://img.shields.io/badge/LangGraph-Supervisor-a855f7?style=for-the-badge)](#)
[![Ollama](https://img.shields.io/badge/Ollama-Local_LLM-00d4ff?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/License-MIT-ffb800?style=for-the-badge)](#)

<br/>

**Un système d'agents qui planifie, code, exécute et s'auto-corrige.**
**Zéro cloud. Zéro hallucination. 100% Souverain.**

</div>

---

## 🧬 L'Architecture du Swarm

Le système repose sur le **Supervisor Pattern** : un agent central (le Planner) orchestre une équipe d'agents spécialisés.

```mermaid
graph TD
    U[👑 Héritier / User] -->|Requête| P(Planner Agent)
    
    P -->|Décomposition| C{Coder Agent}
    C -->|Génération de Code| E(Executor Agent)
    E -->|Sandbox isolé| R{Reflector Agent}
    
    R -->|✅ Succès| M[(ChromaDB Memory)]
    R -->|❌ Échec| C
    
    M -.->|Contexte| P
    
    style U fill:#050810,stroke:#00d4ff,color:#fff
    style P fill:#1a0b2e,stroke:#a855f7,color:#fff
    style C fill:#1a0b2e,stroke:#a855f7,color:#fff
    style E fill:#1a0b2e,stroke:#00d4ff,color:#fff
    style R fill:#1a0b2e,stroke:#ffb800,color:#fff
    style M fill:#050810,stroke:#00d4ff,color:#fff

Les 4 Agents

    🧠 Planner : Décompose la requête complexe en tâches atomiques.

    💻 Coder : Génère le code Python en utilisant le contexte de la mémoire.

    ⚙️ Executor : Exécute le code dans un sandbox isolé (sécurité maximale).

    🪞 Reflector : Analyse les erreurs et demande une correction au Coder (jusqu'à 3 retries).

