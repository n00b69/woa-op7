<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Запуск Windows на OnePlus 7 Pro / 7T Pro

## Дополнительные материалы
> Ниже вы найдете список настроек и материалов для Windows на вашем ARM устройстве.


### Список поддерживаемых приложений/игр
> Это далеко не все списки, однако в них перечислены приложения/игры, протестированные сообществом.
- [Список протестированных приложений/игр](https://docs.google.com/spreadsheets/d/1XYuoySgYQE0HL573sA-0RGMX7I4lt5rWJuQ8Z8yRJNY/edit?usp=drivesdk)

- [ARM Repo (нативное ПО ARM)](https://armrepo.ver.lt/)

- [Новости & поддерживаемые приложения](https://windowsonarm.org/)

#### Готово!


### Переключение режима USB
> [!Warning]
> Переключите USB в режим `DEVICE`, если вы используете USB-hub с питанием, так как это может привести к необратимому повреждению вашего устройства. Если вы не используете USB-hub с питанием, переключите USB в режим `HOST`, иначе вы не сможете использовать USB-устройства.

- Запустите [USB Mode Control](https://github.com/Misha803/My-Scripts/releases/tag/USB-Host-Mode-Control) чтобы переклчить режим USB, затем подтвердите, что вы хотите переключить режим USB (включить/выключить режим USB-хоста).
- Если в данный момент USB в режиме `HOST` и подключённые USB устройства не работают, переключите его в режим `DEVICE`, а затем снова в `HOST`.

#### Готово!


### Настройте автоматическую прошивку Android boot.img
> [!NOTE]
> Настройте автоматическую прошивку boot.img Android при загрузке Windows или при низком заряде батареи (<15%/20%), чтобы предотвратить разрядку батареи с прошитым UEFI.
>
> Если вы используете Dualboot Kernel Patcher, не используйте это.

- Скачайте **boot.img auto-flasher** [здесь](https://github.com/Misha803/My-Scripts/releases/tag/boot.img-Auto-Flasher).
- Запустите его, нажмите кнопку **INSTALL** , выберите, когда следует автоматически прошивать Android boot.img (при загрузке Windows/низком заряде батареи) и дождитесь завершения установки.
- Чтобы удалить сервис автоматической прошивки, снова запустите **boot.img auto-flasher** и нажмите кнопку **UNINSTALL** 

#### Готово! 


### Установка Microsoft Office
- Перейдите на [страницу установщика Gravesoft's Office](https://gravesoft.dev/office_c2r_links).
- Загрузите подходящий вам установщик. Убедитесь, что вы выбрали `Online x64`.
- Откройте `setup.exe` и следуйте всем содержащимся в нем инструкциям.

#### Готово!


### Активация Windows / Office
- Следуйте инструкциям Massgravel [здесь](https://github.com/massgravel/Microsoft-Activation-Scripts)

#### Готово!


### Заставляем клавиатуру парить
> [!WARNING]  
> Убедитесь, что эти шаги выполняются на устройстве под управлением Windows, а не на компьютере!

- Откройте CMD от имени администратора и запустите ```reg delete HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Scaling /v MonitorSize```
- Нажмите `y` а затем enter.
- Перезагрузите устройство.

##### Готово!



















