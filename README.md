## Laboratory work V

Данная лабораторная работа посвещена изучению систем непрерывной интеграции на примере сервиса **Travis CI**

```bash
$ open https://travis-ci.org
```

## Tasks

- [ ] 1. Авторизоваться на сервисе **Travis CI** с использованием **GitHub** аккаунта
- [ ] 2. Создать публичный репозиторий с названием **lab5** на сервисе **GitHub**
- [ ] 3. Включить интеграцию сервиса **Travis CI** с созданным репозиторием
- [ ] 4. Получить фрагмент вставки значка сервиса **Travis CI** в формате **Markdown**
- [ ] 5. Выполнить инструкцию учебного материала
- [ ] 6. Ознакомиться со ссылками учебного материала

## Tutorial

```bash
$ export GITHUB_USERNAME=<имя_пользователя>
```

```bash
$ git clone https://github.com/${GITHUB_USERNAME}/lab4 lab5
$ cd lab5
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab5
```

```bash
$ cat > .travis.yml <<EOF
language: cpp
EOF
```

```bash
$ cat >> .travis.yml <<EOF

script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
EOF
```

```bash
$ ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md
```

```bash
$ mkdir artifacts && cd artifacts
$ screencapture -T 10 screenshot.jpg
<Command>-T
$ open https://github.com/${GITHUB_USERNAME}/lab5
```

```bash
$ git add .
$ git commit -m"added CI"
$ git push origin master
```

## Links

- [AppVeyour](https://www.appveyor.com/)
- [GitLab CI](https://about.gitlab.com/gitlab-ci/)
