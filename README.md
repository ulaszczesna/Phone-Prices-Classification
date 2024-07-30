# Prognozowanie cen telefonów na podstawie ich parametrów technicznych

## Opis Projektu
Celem projektu było stworzenie modelu uczenia maszynowego, który na podstawie parametrów technicznych telefonów klasyfikowałby je do odpowiednich przedziałów cenowych. Wykorzystano do tego dane z platformy Kaggle, zawierające informacje na temat różnych cech telefonów oraz ich kategorii cenowych.

## Dane
- **Źródło**: Dane pochodzą z publicznego zbioru danych na platformie Kaggle, dostępnego [tutaj](https://www.kaggle.com/datasets/ahmedghonem01/phones-price-classification).
- **Zawartość**: Zbiór danych składał się z 21 kolumn o wartościach liczbowych, bez brakujących danych. Kolumna `price_range` była zmienną celu z wartościami od 0 do 3.

## Przygotowanie Danych
1. **Przegląd danych**: Sprawdzenie kolumn i typów danych oraz braków danych.
2. **Skalowanie**: Ze względu na duże różnice w zakresach wartości, dane zostały przeskalowane za pomocą MinMaxScalera.
3. **Analiza korelacji**: Sprawdzenie zależności pomiędzy parametrami technicznymi a ceną telefonów przy użyciu macierzy korelacji.

## Inżynieria Cech i Wstępne Modelowanie
Przeprowadzono testy na kilku prostych modelach klasyfikacyjnych:
- Drzewo decyzyjne
- K-Nearest Neighbors
- Regresja logistyczna
- Support Vector Machine
- Gaussian Naive Bayes

Model regresji logistycznej osiągnął najlepsze wyniki, z dokładnością na poziomie 98%.

## Pierwszy Model: Regresja Logistyczna
Dla finalnego modelu regresji logistycznej, przeprowadzono dostrajanie hiperparametrów za pomocą Grid Search:
- **max_iter**: 6000
- **solver**: 'saga'
- **penalty**: 'none'
- **C**: 0.001
- **l1_ratio**: 0.1

### Wyniki Modelu:
- **Precyzja**: 1.00 dla klasy 0.
- **Czułość (Recall)**: Powyżej 0.97 dla wszystkich klas.
- **Dokładność (Accuracy)**: 0.98.

## Drugi Model: Stacked Classifier
Dla porównania, zbudowano model Stacked Classifier, który osiągnął średnią dokładność 93.85% w krzyżowej walidacji.

## Porównanie Modeli
Logistic Regression osiągnął lepsze wyniki w porównaniu do Stacked Classifier, jednak oba modele wykazały dobrą wydajność.

## Ewaluacja Modelu z Wykorzystaniem Technik Wyjaśnialnej Sztucznej Inteligencji
Przeprowadzono analizę wpływu poszczególnych zmiennych na wyniki modelu za pomocą metod `model_parts` oraz `permutation_importance`:
- **RAM**: Najważniejsza zmienna, odpowiadająca za około 70% dokładności modelu.
- **Battery power**: Istotna zmienna, ale z mniejszym wpływem (25% dokładności).
- Inne zmienne miały minimalny wpływ na predykcje modelu.


## Autorzy
- [Urszula Szczęsna](https://github.com/ulaszczesna)
- [Martyna Leśniak](https://github.com/martynalesniak)
## Wnioski
W ramach projektu udało się zbudować skuteczny model klasyfikacji cen telefonów na podstawie ich parametrów technicznych. Wyniki sugerują, że możliwe jest precyzyjne przewidywanie cen telefonów na podstawie danych dostępnych w zbiorze.
