name: Build mod

on:
  push:
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Extrair o projeto
        run: unzip -q "$(ls *.zip | head -n 1)"

      - uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: 17

      - uses: gradle/actions/setup-gradle@v4
        with:
          gradle-version: 8.1.1

      - name: Compilar o mod
        working-directory: legendaryblades
        run: gradle build --no-daemon

      - name: Guardar o jar pronto
        uses: actions/upload-artifact@v4
        with:
          name: legendaryblades-jar
          path: legendaryblades/build/libs/*.jar
