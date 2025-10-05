<img align="right" src="https://github.com/n00b69/woa-op7/blob/main/op7.png" width="350" alt="Windows 11 running on hotdog/guacamole">

# Запуск Windows на OnePlus 7 Pro / 7T Pro

## Дополнительные материалы
> Ниже вы найдете список настроек и материалов для Windows на вашем устройстве ARM.


### Список поддерживаемых приложений/игр
> Это далеко не все списки, однако в них перечислены приложения/игры, протестированные сообществом.
- [Список протестированных приложений/игр](https://docs.google.com/spreadsheets/d/1XYuoySgYQE0HL573sA-0RGMX7I4lt5rWJuQ8Z8yRJNY/edit?usp=drivesdk)

- [ARM Repo (нативное ПО ARM)](https://armrepo.ver.lt/)

- [Новости & поддерживаемые приложения](https://windowsonarm.org/)

#### Готово!


### Переключение режима USB-хоста
> [!Warning]
> Отключите режим USB-хоста, если вы используете USB-концентратор с питанием, так как это может привести к необратимому повреждению вашего устройства. Если вы не используете USB-концентратор с питанием, включите режим USB-хоста, иначе вы не сможете использовать USB-устройства.

- Запустите [USB Host Mode Control](https://github.com/Misha803/My-Scripts/releases/tag/USB-Host-Mode-Control) чтобы включить/отключить режим USB-хоста, затем подтвердите, что вы хотите отключить/включить режим USB-хоста.
- Если в данный момент включен режим USB-хоста и USB не работает, выключите его, а затем снова включите.

#### Готово!


### Настройте автоматическую прошивку Android boot.img
> [!NOTE]
> Настройте автоматическую прошивку Android boot.img при загрузке Windows или при низком заряде батареи (<15%), чтобы предотвратить разрядку батареи при прошивке UEFI.
>
> Если вы используете Dualboot Kernel Patcher, не используйте это.

- Загрузите **boot.img auto-flasher** [здесь](https://github.com/Misha803/My-Scripts/releases/tag/boot.img-Auto-Flasher).
- Запустите его, нажмите кнопку **УСТАНОВИТЬ** , выберите, когда следует автоматически прошивать Android boot.img (при загрузке Windows/низком заряде батареи) и дождитесь завершения установки.
- Чтобы удалить программу автоматической прошивки, снова откройте **boot.img auto-flasher** и нажмите кнопку **УДАЛИТЬ** 

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



















