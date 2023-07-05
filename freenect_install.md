# Tutorial Basico Freenect
![Badge em Desenvolvimento](http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge)

## Instalação dos pacotes dependentes:
```
$ sudo apt-get install git-core cmake freeglut3-dev pkg-config build-essential libxmu-dev libxi-dev libusb-1.0-0-dev
```

## Instalação do repositorio:
```
$ git clone git://github.com/OpenKinect/libfreenect.git

```

Compilando:

```
$ cd libfreenect
$ mkdir build
$ cd build
$ cmake -L ..
$ make
$ sudo make install
$ sudo ldconfig /usr/local/lib64/
```

## Instalação dos pacotes no Workspace :
```
$ cd ~/catkin_ws/src
$ git clone https://github.com/ros-drivers/freenect_stack.git
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

Podemos como exemplo rodar um launch para obter a nuvem de pontos:

```
$ roslaunch freenect_launch freenect.launch depth_registration:=true

```

Para a visualização dos topicos do Kinect usamos o rviz, em outro terminal:

```
$ source devel/setup.bash
$ rviz
```

## Configuração Rviz

Primeiro devemos setar o rziv:
1. Nas 'Global Options' setamos o 'Fixed Frame' para 'camera_link'

![image](https://user-images.githubusercontent.com/112727443/236491093-f5f4da5f-d709-4a50-85c0-f56d959fb1d2.png)

2. Adicionamos 'pointcloud2' e setemos o topico para '/camera/depth_registered/points'

![image](https://user-images.githubusercontent.com/112727443/236491568-bb6ed89f-4ca2-48c2-acef-66cbf4496b42.png) 


![image](https://user-images.githubusercontent.com/112727443/236491772-02c92416-1c0c-4944-aae1-91e29ebd2553.png)

Agora temos os pontos no display:

![](https://github.com/HerickDallAgnol/Openni-e-Freenect-/blob/main/rviz.gif)

Também podemos visualizar outros topicos como a camera rgb:

1. Adicionamos 'Image' e setemos o topico para '/camera/rgb/image_color'

![](https://github.com/HerickDallAgnol/Openni-e-Freenect-/blob/main/imagecolor.gif)





