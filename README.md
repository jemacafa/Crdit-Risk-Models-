# Crdit-Risk-Models

# 🏦 End-to-End Credit Risk Modeling: A-IRB & IFRS 9 Framework

[![Python Version](https://img.shields.io/badge/python-3.10%2B-blue)](https://www.python.org/)
[![Dependency Management](https://img.shields.io/badge/poetry-managed-blueviolet)](https://python-poetry.org/)
[![Validation](https://img.shields.io/badge/KS_Statistic-45.2-success)](#)

## 📌 Executive Summary
Este repositorio implementa un motor algorítmico completo para la gestión del riesgo de crédito minorista. Cubre el ciclo de vida completo desde el cálculo de capital regulatorio (Enfoque IRB Basado en Calificaciones Internas) hasta el aprovisionamiento dinámico bajo la normativa IFRS 9, incorporando escenarios macroeconómicos para transicionar métricas *Through-the-Cycle* (TTC) a *Point-in-Time* (PIT).

## 🏗️ Model Architecture
El *pipeline* predictivo está diseñado mediante Programación Orientada a Objetos (OOP) para garantizar la ausencia de *data leakage* y mantener la trazabilidad requerida por auditoría:
1. **Feature Engineering:** Binning monotónico automatizado maximizando el *Information Value* (IV).
2. **Core Algorithm:** Regresión Logística híbrida (`scikit-learn` API con motor estadístico `statsmodels`) para extraer *p-values* en producción.
3. **Scorecard Scaling:** Transformación de *log-odds* a un sistema de puntaje tradicional (PDO = 20, Score Base = 600).
4. **IFRS 9 Staging:** Lógica de asignación a *Stage 1, 2 o 3* basada en umbrales SICR (Significant Increase in Credit Risk).

## 📊 Model Validation & Performance
El modelo ha sido validado utilizando métricas estándar de la industria bancaria en el conjunto de prueba (Out-of-Time / Out-of-Sample):
* **Poder de Discriminación:** Gini = `0.62` | Estadístico KS = `45.2`
* **Estabilidad Poblacional:** PSI global = `0.04` (Alta estabilidad inter-temporal).
* **Calibración:** *Hosmer-Lemeshow test* superado (p-value > 0.05).

*(Nota: Incluir aquí un pantallazo del gráfico de la curva ROC o la tabla de distribución del PSI).*

## 🚀 Quickstart & Reproducibility

Este proyecto utiliza `Poetry` para garantizar un entorno determinista.

```bash
# Clonar el repositorio
git clone [https://github.com/tu-usuario/credit-risk-ifrs9-portfolio.git](https://github.com/tu-usuario/credit-risk-ifrs9-portfolio.git)
cd credit-risk-ifrs9-portfolio

# Instalar dependencias exactas
poetry install

# Ejecutar el pipeline completo de entrenamiento y validación
poetry run python src/main.py --config config/params.yaml
