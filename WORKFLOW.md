# GitHub Actions Workflow

## Cel

Workflow automatyzuje proces CI/CD aplikacji.

Obsługuje:

- build aplikacji,
- testy,
- wdrożenie produkcyjne,
- generowanie artefaktów,
- raportowanie statusu.

## Triggery

Workflow uruchamia się dla:

- push do `main`
- push do `develop`
- pull request do `main`
- pull request do `develop`

## Build

Job `Build`:

1. Pobiera repozytorium.
2. Instaluje Python.
3. Instaluje zależności.
4. Buduje aplikację.
5. Dla push do main zapisuje wynik jako artifact.

## Test

Job `Test` uruchamia się po poprawnym zakończeniu Build.

Instaluje zależności i uruchamia testy przez pytest.

## Deploy

Job `Deploy to prod` uruchamia się tylko, gdy:

- zdarzeniem jest `push`,
- gałęzią jest `main`.

Pull request nie powoduje wdrożenia produkcyjnego.

## Workflow Status

Job status uruchamia się zawsze dzięki:

```yaml
if: always()Test PR
