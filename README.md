# Nav2 Demo TurtleBot3

![Resim Açıklaması](https://github.com/gulslamoglu/gulslamoglu--Nav2-Project---build-a-Patrolling-Robot/blob/master/Screenshot%20from%202024-03-09%2019-14-16.png)


Bu depo, ROS 2'de Navigation 2 çerçevesinin kullanımını TurtleBot3 Gazebo simülasyonu ile göstermektedir. Bu proje, robotun belirli bir alanı (basitleştirme amacıyla haritada 4 konum belirlenmiştir) devriye gezmek üzere programlanmasını içerir.

Bu çalışma, Hummingbird Robotics demosundan esinlenilmiştir. Umuyoruz ki bu, ROS 2'de Navigation 2 ile çalışmaya başlamak için harika bir temel oluşturur.

Bu depo, Navigation 2 öğrenme deneyimi hizmetindedir ve aşağıdakilerin gösterimini gerçekleştirir:

- Navigation 2 çerçevesi
- Davranış Ağaçları (C++)

Ayrıca, ilk kez ROS 2 geliştiricileri için bu depo ayrıca aşağıdakileri de gösterir:

- ROS 2 python paketi kullanımı
- ROS 2 C++ paketi kullanımı
- ROS 2 başlatma altyapısı

## Gereksinimler

Bu projeyi çoğaltmak için, aşağıdaki gereksinimleri karşılamanız gerekmektedir:

- ROS 2 (mevcut ana dal kullan besleme, galaktik ise başka bir dalda)
- Gazebo'da çalışan TurtleBot3 simülasyonu. Eğer bu gereksinimleri sağlayabiliyorsanız, aşağıdaki adımları takip ederek sonuçları yeniden oluşturabilirsiniz.

## Adımlar

1. Yeni bir ROS 2 çalışma alanında bu depoyu src dizinine klonlayın (örneğin, turtlebot3_ws/src):

    ```
    git clone git@github.com:gulislamoglu/gulslamoglu--Nav2-Project---build-a-Patrolling-Robot.git

/ .
    ```

2. TurtleBot3 paketlerini vcs ile içeri aktarın:

    ```
    vcs import . < turtlebot3.repos
    ```

3. Çalışma alanı dizininden (turtlebot3_ws) tüm paketleri derleyin:

    ```
    colcon build --symlink-install
    ```

4. Çalışma alanını kaynak dosyalarıyla güncelleyin:

    ```
    source ./install/setup.bash
    ```

5. TurtleBot3 modelini ortama tanıtın:

    ```
    export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:~/turtlebot3_ws/src/turtlebot3/turtlebot3_simulations/turtlebot3_gazebo/models
    export TURTLEBOT3_MODEL=waffle_pi
    ```

6. TurtleBot3 simülasyon altyapısını başlatın:

    ```
    ros2 launch tb3_sim turtlebot3_world.launch.py
    ```

7. Navigation 2 altyapısını (nav2 + amcl başlangıç konumu) başlatın:

    ```
    source ./install/setup.bash
    ros2 launch tb3_sim nav2.launch.py
    ```

8. Demo için otonomi davranışını başlatın:

    ```
    source ./install/setup.bash
    ros2 launch tb3_autonomy autonomy.launch.py
    ```

Bu adımlar TurtleBot'un simülasyon ortamında belirlenen 4 farklı konum arasında hareket etmesini sağlayacak olan demonstrasyonu başlatacaktır (tb3_sim/config/sim_house_locations.yaml'da belirlenen konumlar). Bu konumlar, TurtleBot'un devriye gezmesi için belirlenmiştir.
