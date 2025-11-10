# Michał Muzyka 2.3 – Sprawozdanie Lab 5

### Tworzę namespace dla środowiska deweloperskiego i namespace dla środowiska produkcyjnego. Weryfikuję, czy zostały utworzone.

![Krok 1](images/screen_1.png)



### Tworzę plik YAML ograniczenia zasobów ResourceQuota w przestrzeni nazw ns-prod.

![Krok 2](images/screen_2.png)




### Aplikuję plik YAML i sprawdzam poprawność konfiguracji.

![Krok 3](images/screen_3.png)




### Tworzę plik YAML ograniczenia zasobów ResourceQuota w przestrzeni nazw ns-dev (dostepne zasoby CPU i RAM dwa razy większe w ns-prod niż w ns-dev + ograniczenie do 10 podów w ns-dev). 

![Krok 4](images/screen_4.png)





### Aplikuję plik YAML i sprawdzam poprawność konfiguracji.

![Krok 5](images/screen_5.png)




### W środowisku ns-dev aplikacje mogą być uruchamiane bez zdefiniowanych żądań i limitów, a także nie mogą zużywać więcej niż 0.2 rdzenia procesora i 256 Mi pamięci  Dlatego też tworzę LimitRange dla tego namespace w pliku YAML, a w nim zapisuję domyślne żądanie zasobów i wspomniane zasoby maksymalne. Wartość maksymalna stanie się jednocześnie wartością domyślną limitu zasobów.

![Krok 6](images/screen_6.png)




### Aplikuję manifest dla przestrzeni nazw ns-dev i weryfikuje poprawność.

![Krok 7](images/screen_7.png)




### Tworzę plik YAML obiektu Deployment o nazwie no-test na bazie obrazu nginx w przestrzeni ns-dev. Dodaję żądanie zasobów na cpu=300m, co przekracza wymagania co do wykorzystania zasobów.

![Krok 8](images/screen_8.png)




### Uruchamiam obiekt Deployment. Weryfikuję, że tworzenie poda nie powiodło się z powodu przekroczenia limitu CPU.

![Krok 9](images/screen_9.png)
![Krok 10](images/screen_10.png)




### Tworzę plik YAML obiektu Deployment o nazwie yes-test na bazie obrazu nginx w przestrzeni ns-dev. Dodaję żądanie zasobów na cpu=150m i memory=200Mi, co spełnia wymagania co do zasobów.

![Krok 11](images/screen_11.png)




### Uruchamiam obiekt Deployment. Weryfikuję, że tworzenie poda powiodło się. Pod pomyślnie uruchomił się.

![Krok 12](images/screen_12.png)




### Tworzę plik YAML obiektu Deployment o nazwie zero-test na bazie obrazu nginx w przestrzeni ns-dev bez definiowania zasobów.

![Krok 13](images/screen_13.png)




### Uruchamiam obiekt Deployment. Weryfikuję, że tworzenie poda powiodło się. Pod pomyślnie uruchomił się. Weryfikuję poprawność przypisania domyślnych zasobów. Zasoby requests i limits zostały przypisane takie, jak określono w LimitRange.

![Krok 14](images/screen_14.png)
