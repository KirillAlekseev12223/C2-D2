# C2-D2
СКАЧАТЬ ФАЙЛ 
a)http://data.voltbro.ru/hello.wav
b)ПРОИГРАТЬ НА РОБОТЕ УБИДИТЬСЯ ЧТО СЛЫШНО
c)УСТАНОВИТЬ ГРОМКОСТЬ НА 100%
b)wget http://data.voltbro.ru/hello.wav
aplay hello.wav
c)$ alsamixer
МОДУЛЬ D 
1)cd..
cd..
nano etc/turtlebro.d/turtlebro.launch
ДОБАВЛЯЕМ 2 СТРОКИ
<include file="$(find turtlebro)/launch/ydlidar.launch"if="$(arg run_ydlidar)"/>
<include file="$(find turtlebro)/launch/rplidar.launch"if="$(arg run_rplidar)"/>
cd~/catkin_ws/
catkin_make --pkg turtlebro.launch
sudo sync
rossrvice call/power/reset
2)cd~/catkin_ws/src/turtlebro_navigation
git check out param/dwa_local_planner_params_turtlebro.yaml
cd~/catkin_ws 
catkin_make --pkg turtlebro_navigation
D1 
1)roslaunch turtlebro_navigation turtlebro_slam_navigation.launch open_rviz:=0
2)export ROS_MASTER_URI='HTTP://192.168.106.195:11311'
export ROS_HOSTNAME=192.168.106.255
rviz
ВНУТРИ РВИЗ
МЕНЯЕМ map на base_link
ДОБОВЛЯЕМ РОБОТ МОДЕЛЬ 
ЛАЗЕР СКАН ИЗ БАЙ ТОПИК
МАР ТОЖЕ ОТ ТУДА БЕРЕМ
РАТН  ИЗ move_base/global_blan/
3)ПОКАЗЫВАЕМ ДЕФОЛТ КАРТУ 
4) СОХРАНЯЕМ КАРТУ РВИЗ
 В ТЕРМИНАЛЕ РОБОТА
 map_sercer map_saver -f map
 В ТЕРМИНАЛЕ ПК
 scp pi@turtlebro93.local://home/pi/map.pgm/home/"pc-1"/(USERNAME)
 scp pi@turtlebro93.local://home/pi/map.yaml/home/"pc-1"/(USERNAME)
 D2
 1)cd catkin_ws/src
 git clone https://github.com/voltbro_excursions
 cd../
 catkin_make --pkg turtlebro_excursion
 cd catkin_ws/src
 git clone https://github.com/voltbro/turtlebro_patrol
 cd..
 catkin_make  --pkg turtlebro_patrol
 3)rodlaunch turtlebro_patrol patrol.launch
 Координаты точек, где робот начинает патрулирование, находятся в файле:
 4)~/catkin_ws/src/turtlebro_patrol/data/goals.xml
 Важное замечание!

когда вы добавляете в goals.xml точка, как

<goal x='1' y='0' theta='90' name="point_name"/>
помните,что ось x вперед для робота, а ось y влево для робота. "Тета" должна быть установлена в градусах с правосторонним вращением

Контроль патрулирования
Управление патрульным ботом осуществляется путем отправки сообщений типа std_msgs/String в тему /patrol_control

Принятые команды:

start - запускает цикл патрулирования или переключает робота на следующую цель
пауза - приостанавливает патрулирование в любой точке
resume - возобновление патрулирования в любой точке
главная - перейти к домашней позиции
shutdown - останавливает патрулирование и выполнение пакета
 5.1)echo"Привет мир."| festival --tts -- language russian
 РАБОТА С АРУКО МАРКЕРАМИ
 https://clover.coex.tech/ru/aruco_map.html
 sud raspi-config
 raspi still -o myphoto.jpg(ПРОБНОЕ ФОТО)
 [C2-D2 МОДУЛЬ.docx](https://github.com/KirillAlekseev12223/C2-D2/files/8147880/C2-D2.docx)
