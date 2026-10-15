# Praca nad szablonami

Proces jest opisany w AGENTS.md i w [CONTRIBUTING CLI](https://github.com/GCICHON-DEV/platformctl/blob/main/CONTRIBUTING.md). Proces CLI i rejestru jest dostarczany w dwóch powiązanych PR zadania PLAT-1.

Każdy PR wskazuje Jira, CLI SHA i pin szablonu. Sprawdź walidację manifestu, renderowanie plików, wersje zależności i testy adekwatne do zmiany. Dla lifecycle wymagany izolowany apply/readiness/destroy. Nie uznawaj testu echo za test platformy.

Niezależne review dotyczy pełnego HEAD SHA. Każdy nowy commit wymaga nowego review i CI. Finalną synchronizację obu repozytoriów i wydanie serializuj; zachowaj zgodność starego CLI i nowych manifestów albo udokumentuj migrację.

CI wymaga process-policy i template-contract. Pierwsza kontrola sprawdza metadane PR/commity i testy procesu. Druga używa przypiętego CLI SHA do walidacji i renderowania manifestów; nie instaluje narzędzi i nie wykonuje workflow. Prawdziwe Kind/AWS E2E i pełna macierz wersji pozostają w backlogu. Ochrona main wymaga aktualnej bazy i sukcesu kontroli również dla administratora.

Merge: python3 scripts/merge_pr.py --repo GCICHON-DEV/platformctl-templates --pr NUMER --approved-head PELNY_SHA --merge. Przedtem właściciel publikuje komentarz platformctl-review:v1 z rzeczywistego niezależnego review dokładnego SHA według formatu CONTRIBUTING CLI. Jest to atestacja właściciela, a nie formalna tożsamość agenta w GitHub. Nie obchodź skryptu.

Potwierdzone statusy PLAT: Do zrobienia, W toku, Weryfikacja, Gotowe. Blokadę oznacz etykietą blocked i komentarzem z warunkiem odblokowania. Start, blokady i końcowy wynik zapisuj w Jira i czacie. Raport: zmiana, testy/ograniczenia, PR/review/SHA, para CLI–template, wydanie, readiness, dane, rollback i sprzątanie. Gotowe wymaga wszystkich kryteriów akceptacji.

Wycofanie pinu nie odwraca zasobów cloud. Chroń state, kubeconfig i sekrety. Cloud apply/destroy/restore wymaga jawnego zakresu. Sprzątaj tylko własne odtwarzalne pliki; archiwizuj worktree po potwierdzonej weryfikacji.
