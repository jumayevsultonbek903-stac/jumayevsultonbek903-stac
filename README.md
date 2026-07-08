name: Generate Snake

on:
  # Har 12 soatda avtomatik yangilanadi
  schedule:
    - cron: "0 */12 * * *"
  
  # Istalgan vaqtda qo'lda ishga tushirish imkoniyati
  workflow_dispatch:
  
  # Main branchga o'zgarish bo'lganda ishlaydi
  push:
    branches:
    - main

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
  
    steps:
      # Generates a snake game from a github user contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg    # Oddiy rejim
            dist/github
