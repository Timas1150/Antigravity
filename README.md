# Projeto Aula Antigravity 🚀

Projeto prático desenvolvido durante as atividades com agentes inteligentes e skills no ambiente Antigravity.

---

## 📁 Estrutura do Repositório

```text
aula-antigravity/
├── .agents/skills/              # Skills locais configuradas no projeto
│   ├── chart-image/             # Skill para geração de gráficos com qualidade de publicação
│   ├── conferir-csv/            # Skill de auditoria e qualidade de dados CSV
│   └── decision-matrix/         # Skill para análise multicritério e tomada de decisão
├── dados/                       # Dados originais de entrada
│   └── fornecedores.csv         # Tabela de métricas dos 4 fornecedores
├── resultados/                  # Arquivos gerados pelas análises
│   ├── fornecedores_corrigido.csv         # Base tratada e validada
│   ├── grafico_fornecedores.png           # Comparativo geral e por critério (150 DPI)
│   ├── grafico_radar_fornecedores.png     # Perfil multicritério em radar
│   ├── grafico_termometro.png             # Calibração e zonas do termômetro
│   ├── grafico_tradeoff_custo_qualidade.png # Dispersão Custo x Defeitos
│   ├── melhor_fornecedor.txt              # Ficha consolidada do vencedor
│   ├── qualidade.md                       # Relatório de auditoria de dados
│   └── relatorio_fornecedores.md          # Relatório da matriz de decisão
├── analise_qualidade.py         # Script de auditoria de dados (conferir-csv)
├── fornecedores.py              # Script da matriz de decisão e gráficos
├── forncedores.py               # Script de compatibilidade
├── termometro.py                # Calibração linear de transmissor 4-20 mA
├── AGENTS.md                    # Combinados e regras da aula
├── .gitignore                   # Arquivos ignorados pelo Git (.venv, caches)
└── README.md                    # Documentação do projeto
```

---

## 🛠️ Scripts e Funcionalidades

### 1. `termometro.py` (Calibração 4-20 mA)
- Calcula os coeficientes $A$ e $B$ da reta ($y = ax + b$) a partir dos pontos $(0 \text{ ºC}, 4 \text{ mA})$ e $(100 \text{ ºC}, 20 \text{ mA})$.
- Determina a corrente elétrica para $50 \text{ ºC}$ ($12.0 \text{ mA}$).
- Classifica faixas de temperatura: Baixa ($\le 30 \text{ ºC}$), Média ($31 \text{ a } 60 \text{ ºC}$) e Alta ($> 60 \text{ ºC}$).
- Gera o gráfico com zonas visuais coloridas em `resultados/grafico_termometro.png`.

### 2. `fornecedores.py` (Decision Matrix & Chart-Image)
- Analisa os 4 fornecedores (`Alfa`, `Beta`, `Gama` e `Delta`).
- Pondera os critérios: Preço Unitário (30%), Prazo (20%), Defeitos (30%) e Suporte (20%).
- Normaliza os dados na escala de 1 a 10 e elege o fornecedor **Beta** como o vencedor recomendado (nota final: 7.51).
- Gera 3 gráficos de padrão editorial e o relatório completo em Markdown.

### 3. `analise_qualidade.py` (Auditoria de Dados)
- Executa auditoria na base de dados original conforme a skill `conferir-csv`.
- Verifica integridade, linhas duplicadas e valores ausentes.
- Gera o relatório em `resultados/qualidade.md` e a base validada em `resultados/fornecedores_corrigido.csv`.

---

## ⚙️ Como Executar

Execute os scripts utilizando o interpretador do ambiente virtual:

```bash
# Executar a calibração do termômetro
.\.venv\Scripts\python.exe termometro.py

# Executar a matriz de decisão dos fornecedores
.\.venv\Scripts\python.exe fornecedores.py

# Executar a auditoria de qualidade
.\.venv\Scripts\python.exe analise_qualidade.py
```

