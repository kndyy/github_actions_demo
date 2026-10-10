![CI](https://github.com/kndyy/github_actions_demo/actions/workflows/devops.yml/badge.svg)
![Release](https://img.shields.io/github/v/release/kndyy/github_actions_demo)

# github_actions_demo

Demo de CI/CD con GitHub Actions y Python.

## Estructura

- `hello.py`: aplicacion Python simple
- `tests/test_hello.py`: tests unitarios con pytest
- `.github/workflows/devops.yml`: CI con test, package, docs y deploy a Pages
- `.github/workflows/release.yml`: releases versionados con SemVer
- `site/index.html`: plantilla de la pagina publicada

## Uso local

```bash
pip install -r requirements.txt
PYTHONPATH=$(pwd) pytest -q --cov --cov-report=term-missing --cov-fail-under=80
python hello.py
```

## Pipeline

1. `test`: instala, corre pytest con gate de cobertura 80%, sube `test-report` y publica Job Summary.
2. `package`: arma `app-<build_tag>.zip` con el tag del job test.
3. `docs`: muestra info del repo y runner.
4. `deploy`: solo en `push` a `main`, renderiza `site/` a `public/` y publica en GitHub Pages con aprobacion manual.

Pagina: https://kndyy.github.io/github_actions_demo/
