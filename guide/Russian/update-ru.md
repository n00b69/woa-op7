<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Запуск Windows на OnePlus 7 Pro / 7T Pro

## Обновление драйверов

### Что нужно
- [`Android platform tools`](https://developer.android.com/studio/releases/platform-tools)

- [`Модифицированный TWRP`](https://github.com/n00b69/woa-op7/releases/tag/Recovery)

- [`Драйвера`](https://github.com/n00b69/woa-op7/releases/tag/Drivers)

- [`Образ UEFI`](https://github.com/n00b69/woa-op7/releases/tag/UEFI)

### Загрузитесь в модифицированный recovery TWRP
> Замените `путь\к\moddedtwrp.img` на фактический путь к образу
```cmd
fastboot boot путь\к\moddedtwrp.img
```

### Вход в режим mass storage
- В TWRP нажмите **Advanced** > **Enable Mass Storage Mode**

### Назначьте букву диска WINONEPLUS с помощью Diskpart
> [!NOTE]
> Вы можете пропустить этот шаг если WINONEPLUS уже присвоена буква диска 


### Запустите Diskpart
```cmd
diskpart
```

#### Выберите том Windows
> Используйте `list volume` чтобы найти его, замените `$` на фактический номер **WINONEPLUS**
```cmd
select volume $
```

#### Назначьте букву X
```cmd
assign letter x
```

#### Выйдите из diskpart
```cmd
exit
```

### Установка драйверов
> [!Note]
> Этот процесс займёт около 20 минут. Не волнуйтесь, это нормально.

- Распакуйте архив с драйверами, затем откройте файл `OfflineUpdater.cmd` (если возникнет ошибка, запустите `OfflineUpdaterFix.cmd`)

> Если вас попросят ввести букву, введите букву диска **WINONEPLUS** (которая должна быть **X** ), затем нажмите Enter.

#### Перезагрузите устройство.
> [!NOTE]
> Обязательно замените образ UEFI в Android, иначе при последующей загрузке в Windows вы можете столкнуться с «синим экраном смерти» (BSoD).
```cmd
adb reboot
```

## Готово!











