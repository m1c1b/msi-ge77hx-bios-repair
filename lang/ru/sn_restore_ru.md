# 🔧 Восстановление серийных номеров

Симптомы пустых серийных номеров выглядят следующим образом:

- MSI Center либо вылетает, либо всем своим видом показывает, что не понимает, какое у вас устройство

## 🛠️ DMI EDIT

Прежде всего необходимо убедиться, что серийные номера действительно отсутствуют. Для этого открываем утилиту DMI EDIT из архива и проверяем содержимое следующих полей:

- Base Board/Module Information ⇒ Serial Number
- System Information ⇒ UUID
- System Information ⇒ Product Name
- System Information ⇒ Serial Number

Если эти поля пусты (что будет так, если вы зашивали стоковый образ с сайта), следует выполнить следующие действия:

- Форматировать флешку в FAT32
- Закинуть на неё содержимое каталога _SN-writer-m1ujt72usa_ (сама утилита взята с сайта ASUS)
- Открыть файл efi/boot/startup.nsh
- Вписать в него свои значения. Соответствие команд и полей из DMI EDIT:

  - BS — Base Board/Module Information ⇒ Serial Number
  - SU — System Information ⇒ UUID
  - SP — System Information ⇒ Product Name (у моего ноутбука это "Raider GE77 HX", очень важно не ошибиться)
  - SS — System Information ⇒ Serial Number

- Вставить флешку в ноутбук
- В BIOS поставить загрузку с флешки **раньше**, чем загрузка OS
- При запуске нажать Enter

## 💾 Сохранение значений

Данная утилита только подменяет значения, теперь их необходимо записать. Как оказалось, MSI Center умеет это делать:

- После запуска ноутбука заходим в DMI EDIT и проверяем, появились ли номера
- Если новые значения появились, можно смело запускать MSI Center — на этот раз он успешно распознаёт устройство
- Извлекаем флешку и перезагружаемся, чтобы убедиться, что все серийные номера действительно сохранились
