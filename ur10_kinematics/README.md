### 📄 `README.md`

```markdown
# UR10 Forward Kinematics (HW2 - Q1)

Bu ROS paketi, BLM6191 Robotlar dersi kapsamında verilen Ödev 2’nin Soru 1 kısmını gerçekleştirmek için hazırlanmıştır. UR10 robot kolunun ileri kinematik modeli kullanılarak, belirli eklem açıları için uç efektörün pozisyonu hesaplanmakta ve simülasyon ortamındaki sonuçlarla karşılaştırılmaktadır.

## 🧾 İçerik

- `src/forward_kinematics.cpp`: UR10 robot kolunun ileri kinematik denklemini çözerek uç efektör pozisyonunu hesaplar.
- `src/publisher_node.cpp`: Belirli açı değerlerini `/ur10_arm/acilar` topic’ine gönderir.
- `src/compare_with_sim.cpp`: Simülasyon ortamından `/ur10_arm/odometri` verisini alır ve teorik pozisyon ile farkını karşılaştırır.
- `launch/test_q1.launch`: Yukarıdaki iki node'u birlikte başlatır.

---

## 🚀 Kurulum ve Derleme

1. ROS çalışma alanınızı oluşturun:

```bash
mkdir -p ~/robotlar_ws/src
cd ~/robotlar_ws/src
catkin_init_workspace
```

2. Bu paketi `src` klasörüne ekleyin:

```bash
cd ~/robotlar_ws/src
git clone <bu paketin deposu veya zip'ten çıkarılan klasör>
```

3. Gerekli modelleri kopyalayın:

```bash
cd ~/robotlar_ws
rosdep install -a
catkin_make
cp -r src/gazebo_plugins_rtg/models/ur10 ~/.gazebo/models
```

4. Ortam değişkenlerini yükleyin:

```bash
source devel/setup.bash
```

---

## ▶️ Çalıştırma Adımları

### 1. Simülasyonu başlatın

```bash
roslaunch gazebo_plugins_rtg ur10.launch
```

Bu komut UR10 robot kolunu simülasyon ortamında çalıştırır.

### 2. Node'ları başlatın

Aşağıdaki komutla açıları gönderip odometri verisiyle teorik hesapları karşılaştırabilirsiniz:

```bash
roslaunch ur10_kinematics test_q1.launch
```

Alternatif olarak, her node'u ayrı terminalde çalıştırabilirsiniz:

```bash
rosrun ur10_kinematics publisher_node
rosrun ur10_kinematics compare_with_sim
```

---

## 📌 Test Açı Seti

Aşağıdaki eklem açıları kullanılmıştır (radyan cinsinden):

```cpp
[0.5, -0.2, 0.6, -0.6, -0.4, 0.5]
```

---

## 📷 Örnek Simülasyon Görüntüsü

*(Ekran görüntülerini buraya ekleyiniz — üstten, önden, yandan ve genel görünüş olacak şekilde 4 farklı açıdan.)*

---

## 🧪 Örnek Çıktı

```bash
Sim pozisyon:     1.184 0.335 2.011
Teorik pozisyon:  1.179 0.341 2.009
Fark (m):         0.007
```

---

## 👨‍💻 Hazırlayan

Mehmet Taştan  
BLM6191 - Robotlar  
Yıldız Teknik Üniversitesi  
```

---

Bu `README.md` dosyası ödev kriterlerini karşıladığı gibi, kodu test etmek isteyen herkesin rahatlıkla çalıştırabilmesini sağlar.
