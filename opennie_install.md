# Tutorial Basico Instalação Openni
![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

## Instalação dos pacotes dependentes:
```
$ sudo apt-get install libopenni0 libopenni-dev
```

## Instalação dos pacotes no Workspace :
```
$ cd ~/catkin_ws/src
$ git clone https://github.com/ros-drivers/openni_launch
$ git clone https://github.com/ros-drivers/openni_camera
$ git clone https://github.com/ros-drivers/rgbd_launch.git
```

Checar as dependências com rosdep:
```
$ rosdep update
$ rosdep check --from-paths . --ignore-src --rosdistro noetic
$ rosdep install --from-paths . --ignore-src --rosdistro noetic -y
```

Compilando a workspace:
```
$ cd ~/catkin_ws/
$ catkin_make
```

Source:
```
$ source devel/setup.bash
```

Testando o launch:

```
$ roslaunch openni_launch openni.launch

```

## Configuração do openin_tracker

Instalação dos pacotes no Workspace :

```
$ cd ~/catkin_ws/src
$ git clone https://github.com/ros-drivers/openni_tracker
```
Para funcionar corretamente no Ubuntu 20.04, subsitutua os arquivos do pacote openni_tracker por esses disponibilizados no repositorio (Cmakelists.txt, openni_tracker.xml, package.xml).

Foi feita uma mudança no CmakeLists.txt :

![image](https://user-images.githubusercontent.com/112727443/236873056-6443eda0-5308-4b9f-b099-8351e74ab8f1.png)

Checar as dependências com rosdep:
```
$ rosdep update
$ rosdep check --from-paths . --ignore-src --rosdistro noetic
$ rosdep install --from-paths . --ignore-src --rosdistro noetic -y
```

Compilando a workspace:
```
$ cd ~/catkin_ws/
$ catkin_make
```

Source:
```
$ source devel/setup.bash
```

Instalamos o NITE-Bin-Dev-Linux-v1.5.2.23 na workspace:

```
$ cd catkin_ws
$ git clone https://github.com/arnaud-ramey/NITE-Bin-Dev-Linux-v1.5.2.23.git
```

Instalamos através de:

```
$ cd ~/catkin_ws/src/NITE-Bin-Dev-Linux-v1.5.2.23
$ cd x86/x64 (dependendo da arquitetura)
$ sudo bash install.sh
```
## Testando openni_tracker

Iniciamos abrindo o launch do openni:

```
$ roslaunch openni_launch openni.launch
```

Em outro terminal, utilizamos a seguinte linha de código para que as seja ossível ver os dados do pointcloud e as transformações tf no rviz ao mesmo tempo:

```
$ rosparam set /openni_tracker/camera_frame_id camera_link
$ rosrun openni_tracker openni_tracker
```

Abrimos o rviz em outro terminal:

```
$ rviz
```
Primeiro devemos setar o rziv:
1. Nas 'Global Options' setamos o 'Fixed Frame' para 'camera_link'

![image](https://user-images.githubusercontent.com/112727443/236491093-f5f4da5f-d709-4a50-85c0-f56d959fb1d2.png)

2. Adicionamos o TF:

![image](https://user-images.githubusercontent.com/112727443/236877310-e0837b4e-560e-48a6-8e99-0c72ac0111aa.png)

Fazendo o T pose em frente do kinect conseguimos fazer o rastreamento:

![](https://github.com/HerickDallAgnol/Openni-e-Freenect-/blob/main/tf.gif)



