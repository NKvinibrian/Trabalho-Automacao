# Trabalho de Automação — LaTeX

Este repositório contém um projeto LaTeX simples com `main.tex` e saída em `build/`.
Abaixo estão as instruções para instalar, configurar e compilar em macOS, Windows e Linux, bem como usar o VS Code.

## Estrutura
- `main.tex`: arquivo principal do documento
- `build/`: pasta de saída (PDF e arquivos auxiliares)

## IDE recomendada
- VS Code + extensão "LaTeX Workshop" (James Yu)
  - Abra a paleta: View → Extensions e instale "LaTeX Workshop"

## macOS
- Instale o MacTeX (inclui `pdflatex` e `latexmk`).
- Verifique o executável:
  ```zsh
  which latexmk
  latexmk --version
  ```
- Compilar pelo terminal (na raiz do projeto):
  ```zsh
  latexmk -pdf -synctex=1 -interaction=nonstopmode -file-line-error -outdir=build main.tex
  ```
- Limpar artefatos:
  ```zsh
  latexmk -C -outdir=build
  ```
- Observação: este projeto já traz `.vscode/settings.json` configurado para usar `/Library/TeX/texbin/latexmk` no macOS.

## Windows
- Instale o MiKTeX (ou TeX Live) e o `latexmk`.
  - Se necessário, instale o Perl (ex.: Strawberry Perl) para o `latexmk`.
- Compilar pelo terminal (PowerShell ou CMD) na pasta do projeto:
  ```powershell
  latexmk -pdf -synctex=1 -interaction=nonstopmode -file-line-error -outdir=build main.tex
  ```
- Limpar artefatos:
  ```powershell
  latexmk -C -outdir=build
  ```
- Se não tiver `latexmk`, use o `pdflatex` (rodar 2x normalmente é suficiente para documentos sem bibliografia):
  ```powershell
  pdflatex -interaction=nonstopmode -file-line-error -output-directory=build main.tex
  pdflatex -interaction=nonstopmode -file-line-error -output-directory=build main.tex
  ```

## Linux (Debian/Ubuntu)
- Instale TeX Live e `latexmk`:
  ```bash
  sudo apt-get update
  sudo apt-get install -y texlive-latex-extra latexmk
  ```
- Compilar:
  ```bash
  latexmk -pdf -synctex=1 -interaction=nonstopmode -file-line-error -outdir=build main.tex
  ```
- Limpar:
  ```bash
  latexmk -C -outdir=build
  ```

## Compilar no VS Code (LaTeX Workshop)
- Abra o projeto no VS Code e o arquivo `main.tex`.
- Use o comando "LaTeX Workshop: Build with recipe" e escolha "latexmk (TeX Live)".
- O PDF será gerado em `build/main.pdf` e pode ser visualizado na aba do VS Code.

## Dicas e solução de problemas
- PATH no macOS: garanta que `/Library/TeX/texbin` está no PATH. Este projeto já injeta esse caminho para o VS Code.
- Se o build não iniciar no VS Code, tente compilar uma vez pelo terminal para validar a instalação do LaTeX/latexmk.
- Logs: cheque `build/main.log` para mensagens detalhadas de erro.
