
### introduce
Build Enviroment is making for Virtualbox

### ubuntu install steps
```
1. ubuntu-16.04.2-desktop-amd64.iso download.
2. ubuntu-16.04.2 was install to Virtualbox.
3. memory size 8192MB
4. disk size 90GB
```

### Ubuntu16.04.2 latest update steps
```
$ sudo apt-get -y update
$ sudo apt-get -y upgrade
$ sudo apt-get -y autoremove
$ sudo apt-get -y autoclean
```

### Build Enviroment install steps
[B2G OS �r���h�̕K�v����](https://developer.mozilla.org/ja/docs/Archive/B2G_OS/B2G_build_prerequisites)
```
$ sudo apt-get install make=3.81-8.2ubuntu3
$ sudo apt-mark hold make 
```

��L�菇�ŁA�u3.81-8.2ubuntu3�v������܂���ƁA�\������܂�����Ƃ��p�����܂��B

```
$ sudo dpkg --add-architecture i386
$ sudo dpkg --add-architecture amd64
```

```
$ sudo apt-get install --no-install-recommends autoconf2.13 bison bzip2 ccache curl flex gawk gcc g++ g++-multilib git lib32ncurses5-dev lib32z1-dev libgconf2-dev zlib1g:amd64 zlib1g-dev:amd64 zlib1g:i386 zlib1g-dev:i386 libgl1-mesa-dev libx11-dev make zip lzop libxml2-utils openjdk-8-jdk nodejs unzip python
```

��L�菇�ŁA�u�V�X�e���ɃG���[���������܂����B�v�ƁA�o�O���|�[�g���M�̗L����
�\������܂����A�������č�Ƃ��p�����܂��B
�������̏ꍇ�́A���|�[�g���M�����Ă���i�߂܂����B

### Ubuntu16.10 set up steps
#### Ubuntu16.10�̍�Ƃł����AUbuntu14.04.2�ɂ��K�p���܂����E

##### ����� make �̃o�[�W������ 4.1 �ł���Aandroid �̃r���h���ł��܂���B���̖����������ɂ́A�R���\�[���Ŏ��̃R�}���h�����s���܂�:
```
$ wget http://ftp.us.debian.org/debian/pool/main/m/make-dfsg/make_3.81-8.2_amd64.deb
$ sudo dpkg -i make_3.81-8.2_amd64.deb
$ sudo apt-mark hold make
```

##### �K�{�̃A�[�L�e�N�`����ǉ�
```
$ sudo dpkg --add-architecture i386
$ sudo dpkg --add-architecture amd64
```

#####  �ēx�r���h���C���X�g�[��
```
$ sudo apt-get install --no-install-recommends autoconf2.13 bison bzip2 ccache curl flex gawk gcc g++ g++-multilib git lib32ncurses5-dev lib32z1-dev libgconf2-dev zlib1g:amd64 zlib1g-dev:amd64 zlib1g:i386 zlib1g-dev:i386 libgl1-mesa-dev libx11-dev make zip lzop libxml2-utils openjdk-8-jdk nodejs unzip python -y
```

#####  ccache �̐ݒ�
```
ccache -M 50G
```

#####  adb �C���X�g�[���֘A�C���X�g�[��
[ ubuntu_setup_dev/setup-adb.md](https://github.com/gurezo/ubuntu_setup_dev/blob/master/setup-adb.md) ���

#####  adb setup
 ```
$ sudo apt-get install -y android-tools-adb
```

#####  adb_usb.ini �ҏW����
```
$ mkdir ~/.android
$ vi ~/.android/adb_usb.ini
```
#####  ���L�̓��e��ǋL����  
~~~~
# ��FFx0, Open Web Board  
# ���̃f�o�C�X�����l�ɋL�q���鎖
# 1 USB VENDOR ID PER LINE.
0x2207
# 2 USB VENDOR ID PER LINE.
0x1004
~~~~

#####  ���[����ݒ肷��
```
$ sudo vi /etc/udev/rules.d/51-android.rules
```

#####   ���L�̓��e��ǋL����
~~~~
# ��FFx0, Open Web Board  
# ���̃f�o�C�X�����l�ɋL�q���鎖
SUBSYSTEM=="usb", ATTR{idVendor}=="2207", MODE="0666", GROUP="plugdev"
SUBSYSTEM=="usb", ATTR{idVendor}=="1004", MODE="0666", GROUP="plugdev"
~~~~

#####  �ݒ�𔽉f������B
```
$ sudo udevadm control --reload
```

### git �֘A�̎菇
1. configuration e-mail / git �̃��[���̐ݒ�
2. configuration username / git �̃��[�U�[���̐ݒ�
3. configuration http.postBuffer / git �� http.postBuffer �̐ݒ�

```
$ git config --global user.email "you@example.com"
$ git config --global user.name "Your Name"
$ git config --global http.postBuffer 524288000
```

### B2G �r���h���
- git clone
```
$ git clone https://github.com/chirimen-oh/B2G.git
```
- �r���h�R���t�B�O���s
```
$ ./config.sh chirimen
```
- teimeconst.pl�t�@�C��372�s�� �̏C��
```
if (!defined(@val)) {
    @val = compute_values($hz);
}
=>
if (!@val){
    @val = compute_values($hz);
}
```
