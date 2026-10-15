# platformctl-templates — zasady pracy

Przeczytaj CONTRIBUTING.md. Rozmowa, Jira i PR domyślnie po polsku.
Jedno zadanie → jeden chat → gałąź c/<klucz>-opis → jeden PR w tym repozytorium.
Sprawdź git status i aktualny main; nie nadpisuj cudzej pracy. Do równoległej pracy użyj izolowanego worktree.

- Zmiany manifestu wymagają testów walidacji i renderowania przez platformctl z konkretnego SHA oraz testów scenariusza. Zmiany lifecycle wymagają izolowanego E2E apply/readiness/destroy i ochrony zasobów innych zadań.
- Nie uruchamiaj cloud apply ani destroy istniejących zasobów bez jawnego zakresu konta/regionu/zasobów/budżetu. Nie zapisuj sekretów w YAML, generated ani raportach.
- Wersjonuj parę CLI–template. PR zmieniający kontrakt musi wskazać powiązany PR CLI i kolejność wydania. Finalną synchronizację, review, CI, merge i release serializuj.
- Dla implementacji zleć niezależne review osobnemu agentowi przez narzędzia współpracy; jest to jawne upoważnienie do delegowania review. Reviewer otrzymuje zadanie, bazę, HEAD SHA i wyniki testów. Nowy commit unieważnia review i CI.
- Merge wymaga aktualnego main, niezależnego APPROVED oraz sukcesu wymaganych testów. Wymagane kontrole CI: process-policy i template-contract. Merge przez python3 scripts/merge_pr.py --repo GCICHON-DEV/platformctl-templates --pr NUMER --approved-head SHA --merge. Nie obchodź ochrony gałęzi.
- Zlecenie implementacji obejmuje normalne dostarczenie w istniejącym środowisku testowym; ograniczenia użytkownika do audytu/PR mają pierwszeństwo. Samo planowanie backlogu nie upoważnia do implementacji wszystkich zadań.
- Gotowe dopiero po kryteriach zadania, CI wynikowego SHA jeśli dostępne, opublikowanym lub zainstalowanym artefakcie tam, gdzie wymagany, i weryfikacji scenariusza. Dokumentacja nie wymaga cloud deploy.
- Raportuj start, istotny postęp, blokady i wynik końcowy w chat/Jira; uwzględnij testy, PR/reviewer/SHA, wersję CLI i szablonu, readiness, dane, rollback, cleanup i następny krok. Bez wiadomości do innych osób; queued nie jest wynikiem.
- Zachowaj Terraform state, kubeconfig, dane i cudze pliki. Rollback szablonu nie cofa automatycznie infrastruktury. Sprzątaj tylko własne odtwarzalne artefakty; bez globalnego prune/git clean -fdx. Archiwizuj worktree po potwierdzonym dostarczeniu.
- Context7: resolve-library-id → query-docs dla składni/config/API i migracji narzędzi oraz cloud; zwykłe review nie wymaga docs.
- Conventional Commits: type(templates): konkretny efekt, ewentualnie ci/docs. Opis PR: Zadanie, Zmiana, Weryfikacja, Ryzyko i rollback.
