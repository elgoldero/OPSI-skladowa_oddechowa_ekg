# Metody Odszumiania Sygnału EKG

Elektrokardiogram (EKG) stanowi kluczowe narzędzie diagnostyczne w kardiologii, umożliwiające ocenę elektrycznej aktywności serca. Jednak na jakość rejestrowanego sygnału wpływają różnorodne zakłócenia, które mogą zniekształcać istotne cechy diagnostyczne. Skuteczne odszumianie sygnału EKG jest niezbędnym etapem przetwarzania wstępnego, pozwalającym na tłumienie zakłóceń i uwydatnienie charakterystycznych elementów zapisu. Niniejszy raport przedstawia kompleksowy przegląd klasycznych i nowoczesnych metod odszumiania sygnału EKG, ich skuteczności oraz obszarów zastosowań.

## Charakterystyka zakłóceń w sygnale EKG

Sygnał EKG, będący nielinowym, niestacjonarnym, quasi-okresowym szeregiem czasowym, podlega różnorodnym zakłóceniom, które można sklasyfikować następująco:

### Typowe rodzaje zakłóceń

Zakłócenia występujące w sygnale EKG mają różnorodną naturę i charakterystykę częstotliwościową, co wymaga stosowania odmiennych metod ich eliminacji. Główne źródła zakłóceń obejmują:

- Dryft linii izoelektrycznej - związany z ruchami pacjenta, oddychaniem i zmianami impedancji elektrod, występujący w zakresie niskich częstotliwości (poniżej 0,5 Hz)[^2]
- Zakłócenia sieciowe - pochodzące z sieci elektroenergetycznej (50/60 Hz)[^2][^6]
- Zakłócenia mięśniowe (EMG) - wynikające z aktywności mięśni, szczególnie trudne do usunięcia ze względu na nakładanie się ich widma z użytecznym sygnałem EKG[^5][^12]
- Artefakty związane z ruchem elektrod - powodujące nagłe skoki i nieciągłości sygnału[^3]
- Zewnętrzne zakłócenia elektromagnetyczne - pochodzące z urządzeń elektrycznych w otoczeniu[^14]
- Szum gaussowski - występujący w elektronicznych układach pomiarowych[^3]

Obecność tych zakłóceń może prowadzić do nieprawidłowej diagnozy, dlatego opracowano szereg metod ich efektywnego usuwania, zachowując jednocześnie istotne cechy diagnostyczne sygnału EKG.

## Klasyczne metody filtracji sygnału EKG

Tradycyjne podejście do odszumiania sygnału EKG opiera się na filtracji w dziedzinie częstotliwości, wykorzystującej różnice w charakterystykach widmowych sygnału użytecznego i zakłóceń.

### Filtry analogowe i cyfrowe

Proces filtracji sygnału EKG typowo obejmuje trzy etapy:

1. Filtracja górnoprzepustowa (0,2-0,5 Hz) - usuwająca dryft linii izoelektrycznej[^2]
2. Filtracja pasmowozaporowa (50 Hz) - eliminująca zakłócenia sieci elektroenergetycznej[^2]
3. Filtracja dolnoprzepustowa (25-35 Hz) - redukująca zakłócenia wysokoczęstotliwościowe, w tym artefakty ruchowe i zakłócenia mięśniowe[^2]

Filtry cyfrowe typu FIR (o skończonej odpowiedzi impulsowej) charakteryzują się stabilnością i liniową charakterystyką fazową, co jest istotne dla zachowania morfologii sygnału EKG[^9]. Przykładowy proces filtracji obejmuje kolejne etapy eliminacji zakłóceń wysokoczęstotliwościowych, zakłóceń sieciowych i dryftu linii izoelektrycznej, co prowadzi do uzyskania oczyszczonego sygnału EKG zachowującego kluczowe cechy diagnostyczne[^2].

Warto zauważyć, że charakterystyka szumowa filtrów analogowych i cyfrowych różni się znacząco - dla częstotliwości odcięcia 10 Hz szumy filtra cyfrowego były większe o 34 dB niż dla jego analogowego odpowiednika, co należy uwzględnić przy projektowaniu systemów akwizycji sygnału EKG[^9].

### Filtracja adaptacyjna

Zmienność charakteru zakłóceń w sygnale EKG wymaga stosowania bardziej zaawansowanych rozwiązań. Filtry adaptacyjne dostosowują swoje parametry w czasie rzeczywistym do zmieniających się właściwości sygnału, co czyni je szczególnie przydatnymi w usuwaniu zakłóceń niestacjonarnych[^6].

Metody adaptacyjne są szczególnie skuteczne w redukcji zakłóceń mięśniowych, osiągając poprawę stosunku sygnału do szumu (SNR) o ponad 3 dB przy odpowiednich wartościach długości filtra i wielkości kroku[^12]. Dzięki niskiej złożoności obliczeniowej, filtry adaptacyjne są odpowiednie do zastosowań w przenośnych i wbudowanych systemach rejestracji EKG[^12].

## Metody oparte na transformacie falkowej

Transformata falkowa stanowi potężne narzędzie do analizy sygnałów niestacjonarnych, umożliwiając dekompozycję sygnału w dziedzinie czasu i częstotliwości, co jest szczególnie przydatne w przypadku sygnału EKG.

### Zasada działania i rodzaje progowania

Odszumianie z wykorzystaniem transformaty falkowej obejmuje następujące etapy:

1. Wczytanie sygnału EKG
2. Wielopoziomowa dekompozycja sygnału przy użyciu wybranej falki-matki
3. Odszumianie poprzez progowanie współczynników falkowych
4. Rekonstrukcja sygnału za pomocą odwrotnej transformaty falkowej[^1][^14]

W kontekście progowania współczynników falkowych stosuje się dwa główne podejścia:

- Progowanie twarde - całkowite zerowanie współczynników poniżej ustalonego progu
- Progowanie miękkie - zerowanie współczynników poniżej progu i redukcja wartości powyżej progu o wartość progu[^1][^5][^11]

Badania wykazały, że metoda ta jest szczególnie skuteczna w redukcji zakłóceń mięśniowych przy zachowaniu istotnych diagnostycznie składowych sygnału o małej amplitudzie[^5].

### Optymalizacja parametrów transformaty falkowej

Skuteczność odszumiania z wykorzystaniem transformaty falkowej zależy od kilku kluczowych parametrów:

- Wybór odpowiedniej falki-matki - badania wskazują, że najlepsze rezultaty uzyskuje się dla falek typu Symlets (sym10, sym11, sym13) oraz Daubechies (db13)[^14]
- Poziom dekompozycji - optymalną redukcję szumu uzyskuje się najczęściej dla trzeciego poziomu dekompozycji[^14]
- Metoda progowania - wybór między progowaniem miękkim i twardym zależy od charakterystyki zakłóceń i wymaganej jakości odszumionego sygnału[^1][^5]

Transformata falkowa skutecznie eliminuje szerokie spektrum zakłóceń, włączając szum gaussowski, dryft linii izoelektrycznej oraz zakłócenia mięśniowe, umożliwiając jednocześnie zachowanie istotnych cech morfologicznych sygnału EKG[^11].

## Nowoczesne metody oparte na uczeniu maszynowym

Rozwój uczenia maszynowego i sztucznych sieci neuronowych przyniósł nowe, obiecujące podejścia do problemu odszumiania sygnału EKG, oferujące wysoką skuteczność w przypadku złożonych zakłóceń.

### Sieci rekurencyjne i konwolucyjne

Rekurencyjne sieci neuronowe, w szczególności architektury wykorzystujące warstwy typu Long Short-Term Memory (LSTM), wykazują zdolność do uczenia się zależności czasowych w szeregach czasowych, takich jak sygnał EKG[^7]. Prostej sieci rekurencyjnej typu DRNN, składającej się z warstwy LSTM i następujących warstw gęsto połączonych, udaje się osiągnąć średni błąd RMSE na poziomie 3,047 i średnie MAD wynoszące 0,689[^14].

Sieć typu FCN-DAN (Fully Convolutional Denoising Autoencoder Network), oparta na architekturze autoenkodera, uczy się kodowania i dekodowania pożądanego sygnału, osiągając znacznie lepsze wyniki niż metody klasyczne - średni RMSE wynoszący 1,859 i średnie MAD na poziomie 0,429[^14].

### Metody generatywne i podejścia hybrydowe

Sieci generatywne typu GAN (Generative Adversarial Networks) zdobywają coraz większą popularność w dziedzinie odszumiania sygnału EKG. Badania wykazują, że:

- GAN1 jest najskuteczniejszym rozwiązaniem do usuwania dryftu linii izoelektrycznej i artefaktów związanych z ruchem elektrod[^3]
- GAN2, obok innych metod jak Wavelet-VBE, EMD-MAF, GSSSA, nowy MP-EKF, DLSR i AKF, dobrze radzi sobie z usuwaniem addytywnego białego szumu gaussowskiego[^3]

Warto podkreślić, że wybór odpowiedniej metody powinien uwzględniać rodzaj zakłóceń występujących w sygnale - nie istnieje jedno uniwersalne rozwiązanie dla wszystkich typów zakłóceń[^3][^10].

## Zaawansowane metody w domenie czasowo-częstotliwościowej

Najnowsze badania koncentrują się na wykorzystaniu zaawansowanych technik analizy czasowo-częstotliwościowej, oferujących jeszcze wyższą skuteczność odszumiania.

### Empiryczna transformata falkowa (EWT)

Empiryczna transformata falkowa (EWT) to współczesna metoda odszumiania, która rozkłada sygnał na komponenty częstotliwościowe, umożliwiając szczegółową analizę poprzez konstrukcję niestandardowej bazy falkowej[^4]. Badania porównawcze z użyciem baz danych MIT-BIH potwierdzają, że EWT skutecznie eliminuje różne rodzaje zakłóceń, w tym zakłócenia sieciowe, zachowując jednocześnie informacje zawarte w sygnale[^4].

EWT okazuje się obiecującą metodą odszumiania sygnałów EKG, ułatwiającą dokładną analizę w zastosowaniach klinicznych i badawczych, szczególnie w zestawieniu z mniej adaptacyjnymi metodami opartymi na klasycznej transformacie falkowej[^4].

### Wieloskalowa dekompozycja czasowo-częstotliwościowa

Nowoczesne podejście do odszumiania sygnału EKG oparte na wieloskalowej dekompozycji czasowo-częstotliwościowej łączy transformatę S (S-transform), dwuwymiarową empiryczną dekompozycję modalną (BEMD) i metody średnich nielokalnych (NLM)[^10].

Metoda ta pozwala na skuteczniejszą identyfikację charakterystyk sygnału EKG i zakłóceń w wieloskalowej dziedzinie czasowo-częstotliwościowej, osiągając wyższy SNR i SSIM oraz niższy RMSE i PRD dla wszystkich rodzajów zakłóceń przy różnych poziomach SNR wejściowego[^10]. Jest to szczególnie istotne dla systemów monitorowania serca opartych na technologii wearable, gdzie jakość sygnału jest często niska ze względu na warunki akwizycji[^10].

## Porównanie skuteczności metod odszumiania

Ocena skuteczności metod odszumiania sygnału EKG wymaga zastosowania obiektywnych miar jakości, pozwalających na ilościowe porównanie różnych technik.

### Miary oceny jakości odszumiania

Najczęściej stosowane miary do oceny skuteczności metod odszumiania obejmują:

- SNR (Signal-to-Noise Ratio) - stosunek mocy sygnału do mocy szumu
- RMSE (Root Mean Square Error) - pierwiastek błędu średniokwadratowego
- PRD (Percentage Root mean square Difference) - procentowa różnica pierwiastka średniokwadratowego
- SSIM (Structural Similarity Index) - indeks podobieństwa strukturalnego[^3][^4][^10]


### Skuteczność różnych metod dla specyficznych zakłóceń

Na podstawie analizy literatury można wskazać najbardziej skuteczne metody dla konkretnych typów zakłóceń:

- Dla addytywnego białego szumu gaussowskiego: Wavelet-VBE, EMD-MAF, GAN2, GSSSA, nowy MP-EKF, DLSR, AKF[^3]
- Dla artefaktów mięśniowych: GAN1, nowy MP-EKF, DLSR, AKF[^3][^5]
- Dla dryftu linii izoelektrycznej: GAN1, filtry górnoprzepustowe, EWT[^2][^3][^4]
- Dla zakłóceń sieciowych: DLSR, EWT, filtry pasmowozaporowe[^2][^3][^4]
- Dla złożonych zakłóceń: FCN-based DAE, DWT (Sym6) z miękkim progowaniem, MABWT (soft), CPSD sparsity, UWT[^3]

Warto podkreślić, że metody oparte na głębokim uczeniu (FCN-DAN, DRNN, GAN) często przewyższają metody klasyczne, jednak wymagają odpowiednich zbiorów danych treningowych i zasobów obliczeniowych[^14][^8].

## Wnioski i kierunki przyszłych badań

Na podstawie przeprowadzonej analizy można sformułować następujące wnioski dotyczące metod odszumiania sygnału EKG:

- Nie istnieje jedna uniwersalna metoda odszumiania odpowiednia dla wszystkich typów zakłóceń - wybór metody powinien uwzględniać rodzaj dominujących zakłóceń oraz dostępne zasoby obliczeniowe[^3][^10]
- Metody oparte na transformacie falkowej oferują dobry kompromis między skutecznością a złożonością obliczeniową, szczególnie w przypadku progowania miękkiego i odpowiednio dobranej falki-matki[^5][^11][^14]
- Techniki oparte na uczeniu maszynowym, zwłaszcza sieci głębokie, wykazują najwyższą skuteczność w usuwaniu złożonych zakłóceń, jednak wymagają dużych zbiorów danych treningowych[^7][^8][^14]
- Zaawansowane metody analizy czasowo-częstotliwościowej, takie jak empiryczna transformata falkowa i wieloskalowa dekompozycja, reprezentują obiecujący kierunek badań, oferując wysoką skuteczność dla różnych typów zakłóceń[^4][^10]

Przyszłe badania w dziedzinie odszumiania sygnału EKG powinny koncentrować się na:

- Opracowaniu metod hybrydowych, łączących zalety różnych podejść
- Doskonaleniu technik uczenia głębokiego specyficznych dla sygnału EKG
- Rozwoju metod adaptacyjnych, dostosowujących się do zmiennych warunków akwizycji sygnału
- Implementacji wydajnych algorytmów odszumiania w systemach monitorowania typu wearable[^10]

Skuteczne odszumianie sygnału EKG pozostaje kluczowym elementem w przetwarzaniu biomedycznych sygnałów diagnostycznych, wpływającym bezpośrednio na jakość diagnostyki kardiologicznej i efektywność systemów monitorowania pracy serca.

<div>⁂</div>

[^1]: https://repo.pw.edu.pl/info/bachelor/WUT668df7e16d3f4d85a6268be52e012eb8/

[^2]: https://lucc.pl/inf/informatyka_w_medycynie/wyklad/EKG.pdf

[^3]: https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/iet-spr.2020.0104

[^4]: https://onlinelibrary.wiley.com/doi/10.1155/2024/9050909

[^5]: https://yadda.icm.edu.pl/baztech/element/bwmeta1.element.baztech-article-LOD1-0018-0008?q=5afb9d35-cdfa-4e55-b345-4f6d58792a4d%2410\&qt=IN_PAGE

[^6]: http://yadda.icm.edu.pl/baztech/element/bwmeta1.element.baztech-f3ebf1cf-066d-4c75-8215-44017aafed2f

[^7]: https://studia.icm.edu.pl/odszumianie-sygnalu-ekg-przy-pomocy-rekurencyjnej-sieci-neuronowej/

[^8]: https://www.nature.com/articles/s41598-023-50334-7

[^9]: https://elektronikab2b.pl/technika/17135-analiza-szumow-w-filtrach-analogowych-i-cyfrowych

[^10]: https://www.frontiersin.org/journals/cardiovascular-medicine/articles/10.3389/fcvm.2024.1277123/full

[^11]: https://thescipub.com/pdf/ajassp.2008.276.281.pdf

[^12]: https://ev.fe.uni-lj.si/5-2024/AlSafi.pdf

[^13]: https://pl.linkedin.com/pulse/zastosowanie-ml-w-automatycznej-analizie-sygnałów-ekg-łukasz-malicki

[^14]: https://github.com/MichWozPol/ECG_denoising

[^15]: https://home.agh.edu.pl/~august/pub/pdf/p22.pdf

[^16]: https://www.ire.pw.edu.pl/~arturp/Dydaktyka/aus/aus.pdf

[^17]: http://www.ijeei.org/docs-8294823895029f51e5c2eb.pdf

[^18]: https://www.degruyter.com/document/doi/10.1515/cdbme-2019-0097/pdf

[^19]: https://esezam.okno.pw.edu.pl/mod/book/view.php?id=9\&chapterid=89

[^20]: https://www.ire.pw.edu.pl/~rois/dydaktyka/aus.pdf

[^21]: https://www.mdpi.com/2079-9292/12/7/1606

[^22]: https://www.spiedigitallibrary.org/conference-proceedings-of-spie/12615/126150G/ECG-signal-denoising-algorithm-based-on-wavelet-transform/10.1117/12.2673787.full

[^23]: https://home.agh.edu.pl/~august/pub/pdf/p23.pdf

[^24]: https://foton.if.uj.edu.pl/documents/12579485/c275e5bf-3b3d-436b-99e5-da32bcd57675

[^25]: https://pubmed.ncbi.nlm.nih.gov/34715686/

[^26]: https://www.mdpi.com/2079-9292/12/2/387

[^27]: https://home.agh.edu.pl/~august/stud/dypl/khpraca.pdf

[^28]: https://yadda.icm.edu.pl/baztech/element/bwmeta1.element.baztech-97e54569-0bc3-4f49-b95c-c1d5f1460431

[^29]: https://pulsmedycyny.pl/medycyna/diagnostyka/nowe-algorytmy-ai-do-diagnostyki-skuteczniejsze-od-technikow-ekg-badania/

[^30]: https://arxiv.org/pdf/1807.11551.pdf

[^31]: https://winntbg.bg.agh.edu.pl/skrypty2/0281/transformacjefalkowe.pdf

[^32]: http://www5.informatik.uni-erlangen.de/fileadmin/research/Konferenzen/Biomed07/sessions/Baraniak_070615.pdf

[^33]: https://sigma-not.pl/keyword-119359-1--convolutional-neural-networks.html

[^34]: https://dl.acm.org/doi/10.1145/3700706.3700722

[^35]: https://mostwiedzy.pl/pl/publication/download/1/wykorzystanie-analizy-falkowej-do-odszumiania-oraz-kompresji-sygnalow_65963.pdf

[^36]: https://www.mdpi.com/1424-8220/22/19/7638

[^37]: https://pages.mini.pw.edu.pl/~mandziukj/2018-10-24.pdf

