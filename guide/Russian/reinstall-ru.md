<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Запуск Windows на OnePlus 7 Pro / 7T Pro

## Переустановка Windows

### Что нужно
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Модифицированный TWRP](https://github.com/n00b69/woa-op7/releases/download/Files/moddedtwrp.img)

### Открытие CMD от имени администратора
> Загрузите **platform-tools**  и извлеките папку куда-нибудь, затем откройте CMD от имени **администратора**.
>
> Рекомендуется держать это окно открытым и использовать его на протяжении всего руководства.
> 
> Замените `путь\к\platform-tools` на фактический путь к папке platform-tools, например  **C:\platform-tools**.
```cmd
cd путь\к\platform-tools
```

### Загрузитесь в модифицированный recovery TWRP
> Замените `путь\к\moddedtwrp.img` на фактический путь к образу
```cmd
fastboot boot путь\к\moddedtwrp.img
```

### Форматирование разделов Windows и ESP
```cmd
adb shell format
```

## [Следующий шаг: установка Windows](3-install-ru.md)

















