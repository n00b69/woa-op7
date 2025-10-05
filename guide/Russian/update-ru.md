<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Запуск Windows на OnePlus 7 Pro / 7T Pro

## Обновление драйверов

### Что нужно
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Модифицированный TWRP](https://github.com/n00b69/woa-op7/releases/download/Files/moddedtwrp.img)

- [Драйвера](https://github.com/n00b69/woa-op7/releases/tag/Drivers)

- [Образ UEFI](https://github.com/n00b69/woa-op7/releases/tag/UEFI)

### Загрузитесь в модифицированный recovery TWRP
> Замените `путь\к\moddedtwrp.img` на фактический путь к образу
```cmd
fastboot boot путь\к\moddedtwrp.img
```

### Вход в режим mass storage
- В TWRP нажмите **Advanced** > **Enable Mass Storage Mode**

### Diskpart
```cmd
diskpart
```

#### Выберите том Windows
> Используйте `list volume` чтобы найти его, замените `$` на фактический номер **WINONEPLUS**
```cmd
select volume $
```

#### Назначить букву X
```cmd
assign letter x
```

#### Выйти из diskpart
```cmd
exit
```

### Установка драйверов
> [!Note]
> Этот процесс займёт около 20 минут. Не волнуйтесь, это нормально.

- Распакуйте архив с драйверами, затем откройте файл `OfflineUpdater.cmd` (если возникнет ошибка, запустите `OfflineUpdaterFix.cmd`)

> Если вас попросят ввести букву, введите букву диска **WINONEPLUS** (которая должна быть **X** ), затем нажмите Enter.

#### Перезагрузите устройство.
> Обязательно измените образ UEFI в Android, иначе при последующей загрузке Windows вы можете столкнуться с «синим экраном смерти» (BSoD).

## Готово!











