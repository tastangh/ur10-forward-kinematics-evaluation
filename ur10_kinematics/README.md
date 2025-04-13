# UR10 Forward Kinematics - HW2 Soru 1

## Proje Açıklaması

Bu ROS paketi, UR10 robot kolunun ileri kinematik hesabını gerçekleştirmek ve simülasyon ortamındaki sonuçlarla karşılaştırmak amacıyla geliştirilmiştir. Açı bilgisi simülasyona gönderilir, simülasyondan alınan uç efektör konumu teorik hesapla karşılaştırılır.

---

## Kurulum

### 1. Gazebo Simülasyon Ortamını Klonlayın

```bash
cd ~/robotlar_ws/src
git clone https://gitlab.com/blm6191_2425b_tai/blm6191/gazebo_plugins_rtg.git
```

### 2. Bağımlılıkları Kurun ve Ortamı Derleyin

```bash
cd ~/robotlar_ws
rosdep install -a
catkin_make
source ~/.bashrc
cp -r src/gazebo_plugins_rtg/models/ur10 ~/.gazebo/models
```

---

## Simülasyonu Başlatma

```bash
roslaunch gazebo_plugins_rtg ur10.launch
```

---

## Teorik Kinematik Hesabı

```bash
rosrun ur10_kinematics forward_kinematics
```

Bu komut, tanımlı açı setine göre uç efektörün teorik konumunu (`x, y, z`) hesaplar ve terminale yazdırır.

---

---

## Simülasyon Hızını Artırma (Opsiyonel)

```bash
gz physics -u 10000
```

---

## Kamera Ayarı

Gazebo'da daha net gözlem yapmak için kamerayı robot koluna göre döndürerek pozisyon ayarlayın.

---

## Simülasyonu Durdurma

```bash
rosnode kill -a
pkill -9 gzserver
pkill -9 gzclient
pkill -9 roscore
```

---

## Görseller

*Simülasyon ortamından üstten, önden, yandan ve genel görünüş alınmış ekran görüntüleri bu bölüme eklenecektir.*

---

## Hazırlayan

Mehmet Taştan  
Yıldız Teknik Üniversitesi – BLM6191 Robotlar Dersi
```
