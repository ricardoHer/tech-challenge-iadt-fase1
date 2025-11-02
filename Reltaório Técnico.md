## 📘 Relatório Técnico – Fase 1

**Objetivo:** Desenvolver um sistema de suporte ao diagnóstico de câncer de mama com foco em recall da classe maligna.

**Dataset:** Breast Cancer Wisconsin (569 amostras, 30 features).  
**Modelos testados:** Logistic Regression, Decision Tree, Random Forest, XGBoost.

| Modelo | Recall | AUC | Observações |
|:--------|:-------|:----|:------------|
| Logistic Regression | 0.96 | 0.98 | Baseline simples |
| Random Forest | 0.97 | 0.99 | Mais robusto, interpretável |
| XGBoost | **0.99** | **1.00** | Melhor equilíbrio entre recall e precisão |

**Principais insights:**
- Dataset limpo e balanceado (~37% maligno).  
- Variáveis relacionadas à concavidade e forma das células são as mais relevantes.  
- O modelo XGBoost atingiu o melhor recall e foi explicado via SHAP, garantindo transparência.  

**Conclusão:**  
O sistema alcançou desempenho elevado e interpretabilidade clínica satisfatória, podendo ser expandido para uma API de diagnóstico assistido na Fase 2.
