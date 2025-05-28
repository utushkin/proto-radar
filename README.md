# Создание gRPC и Protobuf

## Подготовка

- Зайти на сайт `https://github.com/protocolbuffers/protobuf/releases?ysclid=m9hd0dry7f812282739`
- Скачать версию программы protoc для своей ОС - например `protoc-30.2-win64.zip`
- Для windows распаковать скаченный архив в папку `C:\protoc`
- в системных переменных добавить путь к папке `C:\protoc\bin`
- отдельно может понадобится установить системную переменную для vscode и других терминалов кроме cmd
- установить `go install google.golang.org/protobuf/cmd/protoc-gen-go@latest`
- установить `go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest`

## Создание proto файла

- создайте директорию нового проекта - например manager-radar
- добавьте в нее новый файл с окончанием .proto (manager-radar.proto)

## Сборка

- `cd manager-radar/`
- `protoc --go_out=. --go_opt=paths=source_relative --go-grpc_out=. --go-grpc_opt=paths=source_relative --experimental_allow_proto3_optional manager-radar.proto`
- `git tag` - проверить последний tag + переключаемся на последний тег
- `git checkout -b fix-for-v0.1.0 v0.1.0` - текущий последний тег
- `git add .`
- `git commit -m ""`
- `git tag v0.1.11` - добавить следующий по счету tag
- `git push origin v0.1.11`

## Разворачивание сервисов gRPC

- на серверной части используем команду `go get github.com/utushkin/proto-radar` для обновления до последнего тега (адрес используем тот который указали в поле option в файле .proto)
<!-- - на серверной части используем команду `go get gl.npo-its.ru/radar/proto-radar` для обновления до последнего тега (адрес используем тот который указали в поле option в файле .proto) -->

## Удаление тегов

- `git push --delete origin v0.1.12` - удаленный репозиторий
- `git tag --delete v0.1.12` - локально

git tag v0.1.1
git push origin v0.1.1

git tag -l -n
git checkout <имя_тега>

Если нужно внести изменения (создать ветку)
Если вы хотите изменить код, находясь на теге, лучше создать новую ветку:

git checkout -b <новая*ветка> <имя*тега>

Например: git checkout -b fix-for-v0.1.0 v0.1.0

Получить все теги с удалённого сервера

git fetch --tags
