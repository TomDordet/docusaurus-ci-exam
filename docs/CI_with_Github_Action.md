Configuration de l'intégration continue (CI) avec GitHub Actions.

```yaml
name: CI    # Nom du workflow.

on:   # Ce workflow s'exécutera à chaque push sur la branch main
  push:  
    branches:
      - main

jobs:   # job de construction
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Set up Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '16'

    - name: Install dependencies
      run: npm install

    - name: Build website
      run: npm run build

    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./build

```

