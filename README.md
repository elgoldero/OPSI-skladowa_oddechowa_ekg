# wyznaczanie składowej oddechowej z sygnału EKG

Sygnał oddechowy można wyznaczyć z zapisu EKG dzięki modulacjom powodowanym przez proces oddychania. Poniżej przedstawiono kluczowe metody i wnioski z badań:

### **Główne metody ekstrakcji sygnału oddechowego**

1. **Analiza amplitudy załamków QRS**
    - **R-S i R-Q**: Różnica amplitud między załamkiem R a S (lub Q) wykazuje korelację z cyklem oddechowym. Metoda jest prosta, ale wrażliwa na zakłócenia[^1][^4].
    - **Pole pod załamkiem R**: Mierzone w oknie 100 ms po początku QRS, jednak mniej skuteczne przy niskiej amplitudzie sygnału[^1][^7].
2. **Zmiany osi elektrycznej serca**
Oblicza się kąt osi elektrycznej (x) z dwóch ortogonalnych odprowadzeń kończynowych (np. I i aVF) za pomocą wzoru:
\$ x = \arctg(y) \$ [rad][^1].
Zmiany tego kąta odzwierciedlają ruch serca podczas oddychania.
3. **Transformata Falkowa**
Sygnał EKG jest dekomponowany na poziomy, a rekonstrukcja z wybranych składowych (np. 0.2–0.4 Hz) izoluje składową oddechową. Liczba poziomów zależy od częstotliwości próbkowania[^1].
4. **Analiza PCA (Principal Component Analysis)**
Łączy zmienność wielu cech EKG (amplitudy P, QRS, T, odstępy RR). Skuteczniejsza niż metody oparte na pojedynczych parametrach, zwłaszcza przy analizie całego kompleksu QRS[^3][^5][^7].
5. **Filtracja homomorficzna**
Stosuje transformatę Fouriera lub kosinusową (DFT/DCT) na cepstrum sygnału EKG, aby wyodrębnić składową oddechową. Metoda z DFT osiąga lepszą spójność z referencyjnym sygnałem oddechowym[^2].
6. **Respiratory Sinus Arrhythmia (RSA)**
Wykorzystuje zmienność odstępów RR, związanych z wpływem autonomicznego układu nerwowego. Mniej skuteczna przy arytmiach[^6][^8].

### **Porównanie skuteczności metod**

| Metoda | Zalety | Ograniczenia |
| :-- | :-- | :-- |
| Amplituda R-S/R-Q | Prosta implementacja | Wrażliwa na zakłócenia[^4] |
| Oś elektryczna | Bezpośredni związek z anatomią | Wymaga ortogonalnych odprowadzeń[^1] |
| PCA | Wysoka spójność z referencją | Złożoność obliczeniowa[^3][^5] |
| Filtracja homomorficzna | Dobra wydajność w zakresie 0.2–0.4 Hz | Zależność od transformacji[^2] |
| RSA | Niskie wymagania sprzętowe | Niewiarygodna przy arytmiach[^8] |

### **Wnioski praktyczne**

- **Dla sygnałów z arytmią** (np. migotanie przedsionków): Najbardziej odporne są metody **R-S amplituda**, **R-Q amplituda** i **centralny moment segmentu RS**[^4].
- **W warunkach szpitalnych**: Zaleca się metody oparte na PCA lub analizie osi elektrycznej ze względu na precyzję[^1][^5].
- **Monitorowanie holterowskie**: Filtracja Savitzky’ego-Golaya (S-G) pozwala uzyskać ciągły sygnał oddechowy, mniej podatny na artefakty[^6][^8].


### **Wyzwania**

- **Zakłócenia**: Ruch elektrod, artefakty mięśniowe[^1].
- **Częstotliwość próbkowania**: Kluczowa dla metod opartych na dekompozycji (np. transformata Falkowa)[^1].
- **Czas trwania sygnału**: Krótkie zapisy (np. 10 s) ograniczają skuteczność algorytmów[^1].

<div>⁂</div>

[^1]: http://www.edi.agh.edu.pl/start/przyklady_rozw/osie/QRS_AX_2010a.pdf

[^2]: https://pubmed.ncbi.nlm.nih.gov/25698628/

[^3]: https://pubmed.ncbi.nlm.nih.gov/29260405/

[^4]: https://lup.lub.lu.se/student-papers/record/9169676/file/9169678.pdf

[^5]: https://pubmed.ncbi.nlm.nih.gov/19362906/

[^6]: https://yadda.icm.edu.pl/baztech/element/bwmeta1.element.baztech-83e1f795-3af1-4a19-9fa2-3b07c2284bfd/c/Szmajda_Three_MMS_4_2023.pdf

[^7]: https://www.cinc.org/archives/2016/pdf/296-336.pdf

[^8]: https://yadda.icm.edu.pl/baztech/element/bwmeta1.element.baztech-1e6b3a10-4a6f-47d9-b775-c5eccfb57644/c/Szmajda_Three_MMS_1_2024.pdf

[^9]: https://www.izbapiel.katowice.pl/attachments/article/5739/EKG.pdf

[^10]: https://www.mp.pl/pacjent/badania_zabiegi/152094,elektrokardiografia-ekg

[^11]: https://journals.viamedica.pl/kardiologia_inwazyjna/article/view/50793/44339

[^12]: https://www.nature.com/articles/s41598-020-62624-5

[^13]: https://yadda.icm.edu.pl/baztech/element/bwmeta1.element.baztech-d1f17197-f039-4b45-8c2b-6f648e092c99/c/Wilk_wirtualny_PAK_9bis_2007.pdf

[^14]: https://www.nature.com/articles/s41598-023-50470-0

[^15]: https://ejtcm.gumed.edu.pl/articles/51

[^16]: https://www.mchtr.pw.edu.pl/content/download/1019/7593/file/dr_asobotnicki_rozprawa.pdf

[^17]: http://pe.org.pl/articles/2019/12/13.pdf

[^18]: https://yadda.icm.edu.pl/baztech/element/bwmeta1.element.baztech-article-BSW4-0032-0015/c/Wilk.pdf

[^19]: https://bip.wat.edu.pl/bip/dokumenty/postepowania-awansowe/ksieczkowski/rozprawa_doktorska_-_k._sieczkowski.pdf

