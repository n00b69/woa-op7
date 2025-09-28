<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Запуск Windows на OnePlus 7 Pro / 7T Pro

## Установка Windows

### Что нужно
- [Модифицированный TWRP](https://github.com/n00b69/woa-op7/releases/download/Files/moddedtwrp.img)

- [Образ Windows ARM](https://arkt-7.github.io/woawin/)
  
- [Драйвера](https://github.com/n00b69/woa-op7/releases/tag/Drivers)

- [Modemprov.zip](https://github.com/n00b69/woa-op7/releases/download/Files/modemprov.zip)

- [Образ UEFI](https://github.com/n00b69/woa-op7/releases/tag/UEFI)

### Загрузитесь в модифицированый TWRP recovery
> Замените `путь\к\moddedtwrp.img` на фактический путь к образу
```cmd
fastboot boot путь\к\moddedtwrp.img
```

### Вход в режим Mass Storage Mode
- В TWRP нажмите **Advanced** > **Enable Mass Storage Mode**

### Diskpart
> [⚠️Внимание]
> НЕ СТИРАЙТЕ, НЕ СОЗДАВАЙТЕ И НЕ ИЗМЕНЯЙТЕ КАКИМ-ЛИБО ОБРАЗОМ РАЗДЕЛЫ В DISKPART!!!! ЭТО МОЖЕТ ПРИВЕСТИ К УДАЛЕНИЮ ВСЕЙ ВАШЕЙ UFS ИЛИ ПОМЕШАТЬ ВАМ ЗАГРУЗИТЬСЯ В РЕЖИМЕ FASTBOOT!!!! ЭТО ОЗНАЧАЕТ, ЧТО ВАШЕ УСТРОЙСТВО БУДЕТ НАВСЕГДА ОКИРПИЧЕНО БЕЗ РЕШЕНИЯ! (кроме перепрошивки с помощью [EDL](edl.md)
```cmd
diskpart
```

#### Выберите том Windows на телефоне
> Используйте `list volume` чтобы найти его, замените `$` на фактический номер **WINONEPLUS**
>
> Если вы не видите **WINONEPLUS**, воспользуйтесь [этим руководством](troubleshooting.md#mass-storage-mode-does-not-work) для альтернативного метода входа в режим mass storage 
```diskpart
select volume $
``` 

#### Назначить букву X
```diskpart
assign letter x
``` 

#### Выберите ESP том телефона
> Используйте `list volume` чтобы найти его, замените `$` на фактический номер **ESPONEPLUS**
```diskpart
select volume $
``` 

#### Назначьте букву Y
```diskpart
assign letter y
```

#### Выйдите из diskpart
```cmd
exit
```

### Установка Windows
> [⚠️Важно]
> Из соображений производительности рекомендуется использовать Windows 11 24H2 (сборки, начинающиеся с 261XX, например 26100.2454)

> Замените `путь\к\install.esd` на фактический путь к install.esd (он также может называться install.wim или 22631.2861.XXXXXXX.esd)

```cmd
dism /apply-image /ImageFile:путь\к\install.esd /index:6 /ApplyDir:X:\
```

> Если вы получили `Error 87`, проверьте индекс вашего образа `dism /get-imageinfo /ImageFile:путь\к\install.esd`, затем замените его `index:6` на фактический номер индекса **Windows 11 Pro** в вашем образе

### Копирование вашего boot.img в Windows
- Перетащите **rooted_boot.img** из папки **platform-tools** на диск **WINONEPLUS** в проводнике Windows, затем переименуйте его в **boot.img**.

### Установка драйверов
- Скачайте и распакуйте архив с драйвером для вашего устройства, затем откройте `OfflineUpdater.cmd` файл (если возникнет ошибка, запустите `OfflineUpdaterFix.cmd` )

> Если вас попросят ввести букву, введите букву диска **WINONEPLUS** (которая должна быть X ), затем нажмите Enter.
  
#### Создать файлы загрузчика Windows
> Если возникнет какая-либо ошибка, например «Сбой при попытке копирования загрузочных файлов», откройте `diskpart` и снова назначьте **ESPONEPLUS**, любую новую букву, а затем замените букву `Y` в следующей команде на букву, которую вы только что добавили 
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Удалить букву диска для ESP
> Если это не сработает, проигнорируйте её и перейдите к следующей команде. Этот фантомный диск исчезнет при следующей перезагрузке компьютера.
```cmd
mountvol y: /d
```

### Прошивка modemprov.zip
> Иначе LTE не будет работать
- В TWRP, выберите `Install` и найдите **modemprov.zip**.
- Вам может понадобиться использовать другой образ восстановления с поддержкой дешифрования, или вы можете загрузить его с помощью `ADB Sideload`

### Перезагрузитесь в fastboot
```cmd
adb reboot bootloader
```

#### Загрузитесь в  UEFI
> Скачайте образ UEFI для вашего устройства, а затем замените `путь\к\devicename-uefi.img` на фактический путь к образу UEFI
```cmd
fastboot boot path\to\devicename-uefi.img
```

### Перезагрузитесь в Android
Ваше устройство должно перезагрузиться автоматически примерно через 10 минут ожидания, после чего вы будете загружены в Android для последнего шага.

## [Последний шаг: настройка двойной загрузки](/dualboot-selection.md)

















