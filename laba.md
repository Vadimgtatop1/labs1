
**

## LABS1


### **1. Скачивание Boost**
wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz


![enter image description here](https://i.yapx.ru/YgOgr.png)



### **2 Разархивирование**
tar -xvzf boost_1_69_0.tar.gz -C ~/
(разархивируем)

### **3. Подсчитывем количество файлов (без вложенных директорий)**

> Команда :  find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l

    ❯ find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l
    
    16




### **4. Подсчитываем количество файлов (включая вложенные директории)**
команда

    find ~/boost_1_69_0 -type f | wc -l
 Результат 

     ❯ find ~/boost_1_69_0 -type f | wc -l
    
    61198
### **5. Подсчитываем заголовочные файлы, .cpp и остальные**
#
Команды:

    find ~/boost_1_69_0 -type f -name "*.hpp" | wc -l
    find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l
    find ~/boost_1_69_0 -type f ! -name "*.hpp" ! -name "*.cpp" | wc -l

#
Результат:
#

    ❯ find ~/boost_1_69_0 -type f -name "*.hpp" | wc -l && find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l && find ~/boost_1_69_0 -type f ! -name "*.hpp" ! -name "*.cpp" | wc -l
    
    14912
    13774
    32512

#
 
### **6. Ищем путь до файла `any.hpp`**
#
Команды:

    find ~/boost_1_69_0 -type f -name "any.hpp"


#
Результат:
#

   

    ❯ find ~/boost_1_69_0 -type f -name "any.hpp"
    
    /home/osb/boost_1_69_0/boost/type_erasure/any.hpp
    /home/osb/boost_1_69_0/boost/proto/detail/any.hpp
    /home/osb/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
    /home/osb/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
    /home/osb/boost_1_69_0/boost/any.hpp
    /home/osb/boost_1_69_0/boost/hana/fwd/any.hpp
    /home/osb/boost_1_69_0/boost/hana/any.hpp
    /home/osb/boost_1_69_0/boost/fusion/include/any.hpp
    /home/osb/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
    /home/osb/boost_1_69_0/boost/fusion/algorithm/query/any.hpp



#


### **7. Ищем файлы с `boost::asio`**


#
Команды: 

    grep -rl "boost::asio" ~/boost_1_69_0


#
Результат:
#
 
   -[Результат](https://raw.githubusercontent.com/Vadimgtatop1/labs1/refs/heads/main/log.txt)
#

### **8. Компируем Boost**

# команда:

    cd ~/boost_1_69_0  && ./bootstrap.sh && ./b2

# Результат:
Мы успешно установили Boost
## 9. Перемещение статических библиотек

# Команда:

    mkdir -p ~/boost-libs && find ~/boost_1_69_0/stage/lib -type f -name "*.a" -exec mv {} ~/boost-libs/ \;

# Результат: 

Перемещенные статические библиотеки 

## 10. Подсчитываем занимаемое пространство каждым файлом

# Команда:

    du -sh ~/boost-libs/*

# Результат:

    ❯ du -sh ~/boost-libs/*
    
    4,0K	/home/osb/boost-libs/libboost_atomic.a
    152K	/home/osb/boost-libs/libboost_container.a
    24K	/home/osb/boost-libs/libboost_context.a
    328K	/home/osb/boost-libs/libboost_contract.a
    152K	/home/osb/boost-libs/libboost_date_time.a
    236K	/home/osb/boost-libs/libboost_fiber.a
    416K	/home/osb/boost-libs/libboost_filesystem.a
    836K	/home/osb/boost-libs/libboost_graph.a
    472K	/home/osb/boost-libs/libboost_iostreams.a
    212K	/home/osb/boost-libs/libboost_prg_exec_monitor.a
    1,6M	/home/osb/boost-libs/libboost_program_options.a
    80K	/home/osb/boost-libs/libboost_random.a
    3,2M	/home/osb/boost-libs/libboost_regex.a
    1,2M	/home/osb/boost-libs/libboost_serialization.a
    40K	/home/osb/boost-libs/libboost_stacktrace_addr2line.a
    16K	/home/osb/boost-libs/libboost_stacktrace_basic.a
    4,0K	/home/osb/boost-libs/libboost_stacktrace_noop.a
    2,3M	/home/osb/boost-libs/libboost_unit_test_framework.a
    4,5M	/home/osb/boost-libs/libboost_wave.a
    788K	/home/osb/boost-libs/libboost_wserialization.a


## 11. Топ-10 самых тяжёлых файлов

# Команда: 

    du -sh ~/boost-libs/* | sort -hr | head 
    -10

# Результат:

    ❯ du -sh ~/boost-libs/* | sort -hr | head -10
    
    4,5M	/home/osb/boost-libs/libboost_wave.a
    3,2M	/home/osb/boost-libs/libboost_regex.a
    2,3M	/home/osb/boost-libs/libboost_unit_test_framework.a
    1,6M	/home/osb/boost-libs/libboost_program_options.a
    1,2M	/home/osb/boost-libs/libboost_serialization.a
    836K	/home/osb/boost-libs/libboost_graph.a
    788K	/home/osb/boost-libs/libboost_wserialization.a
    472K	/home/osb/boost-libs/libboost_iostreams.a
    416K	/home/osb/boost-libs/libboost_filesystem.a
    328K	/home/osb/boost-libs/libboost_contract.a




