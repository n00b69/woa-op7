<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Запуск Windows на OnePlus 7 Pro / 7T Pro

## Получение root-прав

### Что нужно
- [`Magisk`](https://github.com/topjohnwu/Magisk/releases/latest)

- [`Android platform tools`](https://developer.android.com/studio/releases/platform-tools)

### Копирование загрузочного образа на Android
- Подключите телефон к компьютеру (с включенной отладкой по USB).
- Нажмите на уведомление на телефоне, чтобы разрешить компьютеру доступ к данным. Если уведомление не появится, перейдите на панель уведомлений и нажмите на уведомление USB, а затем измените тип подключения на **передачу файлов** .
- Скопируйте файл**boot.img** из папки **platform-tools** во внутреннюю память.

#### Патч загрузочного образа
- Загрузите и установите **Magisk**, а затем откройте его.
- Нажмите **Установить** > **Пропатчить boot.img** и выберите **boot.img** который вы только что скопировали.
- После завершиния операции найдите **файл magisk_patched-29000_XXXX.img** в папке **Загрузки** и скопируйте его в папку **platform-tools** на вашем компьютере.

### Перезагрузитесь в fastboot
```cmd
adb reboot bootloader
```

#### Перепрошивка пропатченного загрузочного образа
> Замените `путь\к\magisk_patched.img` на файтический путь к образу
```cmd
fastboot flash boot_a путь\к\magisk_patched.img
```

### Перезагрузитесь в Android
```cmd
fastboot reboot
```

#### Завершение настройки
- Снова откройте приложение **Magisk**.
- Следуйте инструкциям на экране, и ваше устройство должно перезагрузиться через несколько секунд.

### Копирование рутированного загрузочного образа
> После того, как ваше устройство снова загрузится в Android
```cmd
adb shell "su -c cp /dev/block/by-name/boot$(getprop ro.boot.slot_suffix) /sdcard/rooted_boot.img" & adb pull /sdcard/rooted_boot.img
```
- На экране вашего телефона может появиться запрос на доступ к Shell. Если это так, предоставьте ему доступ..
- Если команда не выполняется, откройте **Magisk**, щёлкните по вкладке `Superuser`, найдите **Shell**, и предоставьте ему доступ.

## [Следующий шаг: установка Windows](3-install-ru.md)












































