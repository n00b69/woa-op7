<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Запуск Windows на OnePlus 7 Pro / 7T Pro

## Гайд двойной загрузки (DualbootKernelPatcher)
> Ниже описаны 2 метода, первый требует root-доступ , второй не требует root-доступ. Используйте метод который вам больше подходит, т.к. оба они делают одно и то же.

> [!Important]
> Если вы используете OOS12 или прошивку на её основе, вам нужно будет выполнить несколько дополнительных и альтернативных шагов которые вы можете найти [тут](troubleshooting-ru.md#Я-хочу-использовать-Windows-используя-OOS12)

### Prerequisites (method 1: root required)
- [`Приложение WOA Helper`](https://github.com/n00b69/woa-helper/releases/tag/APK)

### Настройка - Android
- Скачайте и установите приложение **WOA Helper**, затем откройте его и предоставьте ему root-доступ.
- Откройте **WOA Toolbox**, затем нажмите кнопку **DUALBOOT KERNEL PATCHER**.
- Подождите пока процесс завершится и перезагрузите ваш телефон.

#### Загрузка в Windows
- Переместите **alert slider** в верхнюю позицию и перезагрузите (или включите) ваш телефон.

#### Загрузка в Android
- Переместите **alert slider** в среднюю или нижнюю позицию и перезагрузите (или включите) ваш телефон.

## Готово!


### Что нужно? (метод 2: root не нужен)
- [`Модифицированный TWRP`](https://github.com/n00b69/woa-op7/releases/tag/Recovery)

- [`Magiskboot`](https://github.com/n00b69/woa-op7/releases/download/DBKP/magiskboot.exe)

- [`DualBoot Kernel Patcher`](https://github.com/n00b69/woa-op7/releases/download/DBKP/DualBootKernelPatcher.zip)

- [`.fd файл`](https://github.com/n00b69/woa-op7/releases/DBKP) (скачайте именно для вашего устройства, например для `guacamole` или `hotdog`)

### Открытие CMD от имени администратора 
> Откройте CMD от имени **администратора** , затем выполните указанную ниже команду, заменив `путь\к\platform-tools` фактическим путем к папке platform-tools, например **C:\platform-tools**.
>
> Не закрывайте это окно. Оно понадобится вам на протяжении всего руководства.
```cmd
cd путь\к\platform-tools
```

### Загрузитесь в модифицированный TWRP recovery
> Замените `путь\к\moddedtwrp.img` на фактический путь к образу
```cmd
fastboot boot путь\к\moddedtwrp.img
```

#### Создайте резервную копию вашего загрузочного образа
> Это создаст резервную копию вашего загрузочного образа в текущем каталоге (например `C:\platform-tools`).
```cmd
adb pull /dev/block/by-name/boot_a boot.img
```

#### Настройка необходимых файлов
- Загрузите **magiskboot.exe** и переместите его в папку `platform-tools`.
- Загрузите **DualBootKernelPatcher.zip** и извлеките папку **DualBootKernelPatcher** в папку `platform-tools`.
- Загрузите **DEVICENAME.fd** для вашего устройства и переместите его в `platform-tools` folder.

### Распаковка вашего загрузочного образа
> Убедитесь что **boot.img** находится в папке `platform-tools` 
```cmd
magiskboot unpack boot.img
```

### Обновление загрузочного образа
> Замените `DEVICENAME.fd` в приведенной ниже команде фактическое имя вашего устройства (`guacamole.fd` или `hotdog.fd`)
```cmd
DualBootKernelPatcher\bin\Windows\DualBootKernelPatcher-x86_64.exe kernel DEVICENAME.fd output DualBootKernelPatcher\Config\DualBoot.Sm8150.cfg DualBootKernelPatcher\ShellCode\ShellCode.Hotdog.bin
```

### Переименование файла ядра
- Удалите или переименуйте файл **kernel** в `platform-tools`, tзатем переименуйте **output** файл в `kernel`

### Переупаковка вашего загрузочного образа
> Это переупакует ваш пропатченный загрузочный образ в новый файл с именем **new_boot.img**
```cmd
magiskboot repack boot.img
```

### Перезагрузитесь в fastboot
```cmd
adb reboot bootloader
```

### Перепрошивка пропатченного загрузочного образа
> Замените `путь\к\new_boot.img` на фактический путь в образу
```cmd
fastboot flash boot_a путь\к\new_boot.img
```
```cmd
fastboot flash boot_b путь\к\new_boot.img
```

#### Перезагрузите устройство.
```cmd
fastboot reboot
```

#### Загрузка Windows
- Переместите **ползунок оповещения** в верхнее положение и перезагрузите (или включите) ваше устройство.

#### Загрузка Android
- Переместите **ползунок оповещения** в среднее или нижнее положение и перезагрузите (или включите) ваше устройство

## Готово!

















