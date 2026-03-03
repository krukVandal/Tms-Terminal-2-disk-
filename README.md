# Терминал Задача № 2 ---- Роман Салий  
0. Создал два дополнительных диска в virtualbox по инструкции по 10G.    

1. Создал по два раздела на каждый диск с помощью команд:  
   - ('sudo fdisk /dev/sdb')
       
   - ('sudo fdisk /dev/sdc')  
<img width="1194" height="749" alt="image" src="https://github.com/user-attachments/assets/cc7a376d-be7a-4126-9b94-274fdbeea4ec" />

2. Собрал из sdb1 и sdc2 группу tms-vg и создал 2 логических тома(data, bkp),
 
   смонтировал их в ('/opt/data' - xfs и '/opt/backup' - ext4).

   Использовал команды:

   - ('sudo pvcreate') - создание физических томов.
  
   - ('sudo vgcreate tms-vg') - создание логической группы.
 
   - ('sudo lvcreate -L 2G -n "Имя тома" tms-vg') - создание логических томов в группе.
  
 <img width="978" height="623" alt="image" src="https://github.com/user-attachments/assets/e641e3a1-99c0-4ee5-a5e8-e11f61c07f58" />
 
   - ('sudo mkfs.xfs') - создание файловой системы для data. 
    
   - ('sudo mkfs.ext4') - создание файловой системы для backup.
    
 <img width="978" height="605" alt="image" src="https://github.com/user-attachments/assets/24d23165-38aa-42c0-a192-672fbfc7e7f5" />

   - ('sudo mount') - смонтировал.

 <img width="978" height="605" alt="image" src="https://github.com/user-attachments/assets/51df2277-86f7-4e1c-a28d-74002aca8f83" />

 3. Добавил в tms-vg sdb2 с помощью команды:

    - ('sudo vgextend') - добавил в группу.

 <img width="978" height="605" alt="image" src="https://github.com/user-attachments/assets/7c599fa6-06ec-456f-a3fa-b32f418c39dd" />

 4. Расширил data до максимального объема c помощью команд:

    - ('sudo lvextend -l +100%FREE') - выделяет всё пространство data
      
    - ('sudo xfs-growfs') - вроде бы делает тоже самое, но на всякий случай применил.

 <img width="1254" height="796" alt="image" src="https://github.com/user-attachments/assets/42fd6dd2-fc2d-476e-afbe-0b66b9b83a78" />

 5. Собрал группу reserved, создал физический затем логический том с имене test
    
    и смонтировал полученный образ в папку /opt/tests предварительно созданную.

 <img width="1146" height="785" alt="image" src="https://github.com/user-attachments/assets/ebd9a12f-a36f-4ad3-a7d7-fbee85c170db" />

 6. Отмонтировал тестовый том, файлы утратились и еще раз создал файлы file и file1 после монтирования они остались

    Использовал команду:

    - ('sudo umount') - Отмонтирование тома.

 <img width="1146" height="785" alt="image" src="https://github.com/user-attachments/assets/b9431cb0-aea8-4cc1-ac6c-419ba09afb3d" />



    


    
  

