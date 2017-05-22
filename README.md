## Laboratory work V

Данная лабораторная работа посвещена изучению систем непрерывной интеграции на примере сервиса **Travis CI**

```bash
$ open https://travis-ci.org
```

## Tasks

- [ ] 1. Авторизоваться на сервисе **Travis CI** с использованием **GitHub** аккаунта
- [ ] 2. Создать публичный репозиторий с названием **lab05** на сервисе **GitHub**
- [ ] 3. Ознакомиться со ссылками учебного материала
- [ ] 4. Включить интеграцию сервиса **Travis CI** с созданным репозиторием
- [ ] 5. Получить токен для **Travis CLI** с правами **repo** и **user**
- [ ] 6. Получить фрагмент вставки значка сервиса **Travis CI** в формате **Markdown**
- [ ] 7. Выполнить инструкцию учебного материала
- [ ] 8. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```bash
$ export GITHUB_USERNAME=<имя_пользователя>
$ export GITHUB_TOKEN=<полученный_токен>
```

```bash
$ git clone https://github.com/${GITHUB_USERNAME}/lab04 lab05
$ cd lab05
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab05
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
$ cat >> .travis.yml <<EOF

addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
EOF
```

```bash
$ travis login --github-token ${GITHUB_TOKEN}
```

```bash
$ travis lint
```

```bash
$ ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md
```

```bash
$ git add .travis.yml
$ git add README.md
$ git commit -m"added CI"
$ git push origin master
```

```bash
$ travis lint
$ travis accounts
$ travis sync
$ travis repos
$ travis enable
$ travis whatsup
$ travis branches
$ travis history
$ travis show
```

## Report

```bash
$ cd ~/workspace/labs/
$ export LAB_NUMBER=05
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m"lab${LAB_NUMBER}"
```

## Links

- [Travis Client](https://github.com/travis-ci/travis.rb)
- [AppVeyour](https://www.appveyor.com/)
- [GitLab CI](https://about.gitlab.com/gitlab-ci/)

```
Copyright (c) 2017 Братья Вершинины
```
