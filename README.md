# nfqws-keenetic

[![GitHub Release](https://img.shields.io/github/release/Anonym-tsk/nfqws-keenetic?style=flat&color=green)](https://github.com/Anonym-tsk/nfqws-keenetic/releases)
[![GitHub Stars](https://img.shields.io/github/stars/Anonym-tsk/nfqws-keenetic?style=flat)](https://github.com/Anonym-tsk/nfqws-keenetic/stargazers)
[![License](https://img.shields.io/github/license/Anonym-tsk/nfqws-keenetic.svg?style=flat&color=orange)](LICENSE)
[![CloudTips](https://img.shields.io/badge/donate-CloudTips-598bd7.svg?style=flat)](https://pay.cloudtips.ru/p/054d0666)
[![YooMoney](https://img.shields.io/badge/donate-YooMoney-8037fd.svg?style=flat)](https://yoomoney.ru/to/410019180291197)
[![Join Telegram group](https://img.shields.io/badge/Telegram_group-Join-blue.svg?style=social&logo=telegram)](https://t.me/nfqws)
[![Ask DeepWiki](https://deepwiki.com/badge.svg)](https://deepwiki.com/Anonym-tsk/nfqws-keenetic)

Packages for installing `nfqws` on routers.

> [!IMPORTANT]
> This material was prepared for scientific and technical purposes.
> Use of the materials provided for purposes other than information may be a violation of applicable law.
> The author is not responsible for the unlawful use of this material.

> [!WARNING]
> **You use these instructions at your own peril and risk!**
> 
> The author is not responsible for damage to equipment and software, problems with access and potency.
> It assumes that you understand what you are doing.

Originally written for Keenetic/Netcraze routers with entware installed.
However, performance was also tested on Padavan and OpenWRT firmware (read below).

Списки проверенного оборудования собираем в [отдельной теме](https://github.com/Anonym-tsk/nfqws-keenetic/discussions/1).
<details>
  <summary>Собранный список моделей из темы</summary>
 
  - Beeline Smart Box GIGA
  - Beeline Smart Box Turbo
  - ASUS ROG Rapture GT-AX6000
  - ASUS RT-AC51U
  - ASUS RT-AC68U
  - ASUS RT-AC86U
  - ASUS RT-AX58U
  - ASUS RT-AX86U
  - ASUS RT-AX88U
  - ASUS RT-N16
  - ASUS RT-N56U
  - Cudy TR1200
  - Cudy TR3000
  - D-Link DIR-620/D/F1A
  - GL.iNet Flint 2 (GL-MT6000)
  - Zyxel Keenetic II
  - Zyxel Keenetic III
  - Zyxel Keenetic Giga II
  - Zyxel Keenetic Giga III
  - Zyxel Keenetic Extra
  - Zyxel Keenetic Extra II
  - Zyxel Keenetic Ultra
  - Zyxel Keenetic Ultra II
  - Keenetic Giga (KN-1010)
  - Keenetic Giga (KN-1011)
  - Keenetic Giga (KN-1012)
  - Keenetic 4G (KN-1212)
  - Keenetic Omni (KN-1410)
  - Keenetic Extra (KN-1710)
  - Keenetic Extra (KN-1711)
  - Keenetic Extra (KN-1713)
  - Keenetic Ultra (KN-1810)
  - Keenetic Ultra (KN-1811)
  - Keenetic Viva (KN-1910)
  - Keenetic Viva (KN-1912)
  - Keenetic Viva (KN-1913)
  - Keenetic DSL (KN-2010)
  - Keenetic Launcher DSL (KN-2012)
  - Keenetic Duo (KN-2110)
  - Keenetic Skipper DSL (KN-2112)
  - Keenetic Runner 4G (KN-2211)
  - Keenetic Hero 4G+ (KN-2311)
  - Keenetic Giga SE (KN-2410)
  - Keenetic Giant (KN-2610)
  - Keenetic Peak (KN-2710)
  - Keenetic Hopper DSL (KN-3610)
  - Keenetic Hopper (KN-3810)
  - Keenetic Hopper (KN-3811)
  - Keenetic Hopper SE (KN-3812)
  - MikroTik hEX S (RB760iGS)
  - MikroTik RB951G-2HnD
  - Mikrotik hAP ac lite (RB952Ui-5ac2nD)
  - TP-Link Archer C20
  - TP-Link Archer C6U
  - TP-Link WDR3500
  - Xiaomi Mi Router 3G
  - Xiaomi Mi Router 4
  - Xiaomi Mi Router 4A
  - Xiaomi Mi Router 4C
  - Xiaomi Mi Router Mini
  - Xiaomi Mi Router Pro
  - Xiaomi Mi Wi-Fi mini
  - Xiaomi Router AX3000T
  - Xiaomi Router Redmi AC2100

</details>

Поделиться опытом можно в разделе [Discussions](https://github.com/Anonym-tsk/nfqws-keenetic/discussions) или в [чате](https://t.me/nfqws).

### What is this?

`nfqws` - ​​a utility for modifying a TCP connection at the packet level, works through the NFQUEUE queue handler and raw sockets.

Почитать подробнее можно на [странице авторов](https://github.com/bol-van/zapret) (ищите по ключевому слову `nfqws`).

### Preparing Keenetic/Netcraze

- Read the instructions completely before you start doing anything!

- Рекомендуется игнорировать предложенные провайдером адреса DNS-серверов. Для этого в интерфейсе роутера отметьте пункты ["игнорировать DNS от провайдера"](https://help.keenetic.com/hc/ru/articles/360008609399) в настройках IPv4 и IPv6.
 
- Вместе с этим рекомендуется [настроить использование DoT/DoH](https://help.keenetic.com/hc/ru/articles/360007687159).

- Установить entware на маршрутизатор по инструкции [на встроенную память роутера](https://help.keenetic.com/hc/ru/articles/360021888880) или [на USB-накопитель](https://help.keenetic.com/hc/ru/articles/360021214160).

- Using the Keenetic/Netcraze web interface, install the packages **IPv6 Protocol** (**Network functions > IPv6**) and **Netfilter subsystem kernel modules** (**OPKG > Kernel modules for Netfilter** - not to be confused with "Netflow"). Please note that the second component will appear in the list of packages only after you select the first one for installation.

- In the "Internet filters" section, disable all third-party filters (NextDNS, SkyDNS, Yandex DNS and others).

- All further commands are executed not in the router’s cli, but **in the entware environment**. You can connect to it in several ways:
  - Via telnet: in the terminal, run `telnet 192.168.1.1`, and then `exec sh`.
  - Or connect directly via SSH (login - `root`, default password - `keenetic`, port - 222 or 22). To do this, write `ssh 192.168.1.1 -l root -p 222` in the terminal.

---

### Installation on Keenetic/Netcraze and other systems with Entware

1. Install required dependencies
   ```bash
   opkg update
   opkg install ca-certificates wget-ssl
   opkg remove wget-nossl
   ```

2. Install the opkg repository on the system
   ```bash
   mkdir -p /opt/etc/opkg
   echo "src/gz nfqws-keenetic https://anonym-tsk.github.io/nfqws-keenetic/all" > /opt/etc/opkg/nfqws-keenetic.conf
   ```
The repository is universal, supported architectures: `mipsel`, `mips`, `mips64`, `aarch64`, `armv7`, `x86`, `x86_64`, `lexra`.

   <details>
     <summary>Или можете выбрать репозиторий под конкретную архитектуру</summary>

     - `mips-3.4` <sub><sup>Keenetic Giga SE (KN-2410), Ultra SE (KN-2510), DSL (KN-2010), Launcher DSL (KN-2012), Duo (KN-2110), Skipper DSL (KN-2112), Hopper DSL (KN-3610); Zyxel Keenetic DSL, LTE, VOX</sup></sub>
       ```bash
       mkdir -p /opt/etc/opkg
       echo "src/gz nfqws-keenetic https://anonym-tsk.github.io/nfqws-keenetic/mips" > /opt/etc/opkg/nfqws-keenetic.conf
       ```

     - `mipsel-3.4` <sub><sup>Keenetic 4G (KN-1212), Omni (KN-1410), Extra (KN-1710/1711/1713), Giga (KN-1010/1011), Ultra (KN-1810), Viva (KN-1910/1912/1913), Hero 4G (KN-2310/2311), Giant (KN-2610), Skipper 4G (KN-2910), Hopper (KN-3810); Zyxel Keenetic II / III, Extra, Extra II, Giga II / III, Omni, Omni II, Viva, Ultra, Ultra II</sup></sub>
       ```bash
       mkdir -p /opt/etc/opkg
       echo "src/gz nfqws-keenetic https://anonym-tsk.github.io/nfqws-keenetic/mipsel" > /opt/etc/opkg/nfqws-keenetic.conf
       ```

     - `aarch64-3.10` <sub><sup>Keenetic Peak (KN-2710), Ultra (KN-1811), Hopper (KN-3811), Hopper SE (KN-3812), Giga (KN-1012)</sup></sub>
       ```bash
       mkdir -p /opt/etc/opkg
       echo "src/gz nfqws-keenetic https://anonym-tsk.github.io/nfqws-keenetic/aarch64" > /opt/etc/opkg/nfqws-keenetic.conf
       ```
   </details>

3. Install the package
   ```bash
   opkg update
   opkg install nfqws-keenetic
   ```

4. Install the web interface (optional)
   ```bash
   opkg install nfqws-keenetic-web
   ```
> [!NOTE]
> Адрес веб-интерфейса `http://<router_ip>:90` (например http://192.168.1.1:90)<br/>
> To authorize, enter the username and password of the entware user (by default root and keenetic if not changed during installation)

> [!TIP]
> By default, php uses only 8MB of memory. Due to this limitation, large lists of files may not be downloaded.
> You can change the php configuration yourself:<br/>
> Откройте файл `/opt/etc/php.ini` и измените следующие значения
> ```ini
> memory_limit = 32M
> post_max_size = 32M
> upload_max_filesize = 16M
> ```

##### Update

```bash
opkg update
opkg upgrade nfqws-keenetic
opkg upgrade nfqws-keenetic-web
```

##### Removal

```bash
opkg remove --autoremove nfqws-keenetic-web nfqws-keenetic
```

##### Information about the installed version

```bash
opkg info nfqws-keenetic
opkg info nfqws-keenetic-web
```

### Access policies on Keenetic/Netcraze

On Keenetic/Netcraze you can create an access policy **NFQWS** (Connection priorities - Internet access policies)
and after restarting nfqws-keenetic will only work for devices from this policy.<br/>
_Don't forget to check the box on the provider interface in the created policy._

You can make an exclusion policy by adding `POLICY_EXCLUDE=1` to the config. Then traffic will be processed for all devices except those added to the `NFQWS` policy.<br/>
The policy name can be changed in the config, parameter `POLICY_NAME`.

If a policy with the same name is not found, all traffic will be processed.

---

### Installing OpenWRT

#### Up to version 24.10 inclusive, package manager `opkg`

1. Install required dependencies
   ```bash
   opkg update
   opkg install ca-certificates wget-ssl
   opkg remove wget-nossl
   ```

2. Set the repository public key
   ```bash
   wget -O "/tmp/nfqws-keenetic.pub" "https://anonym-tsk.github.io/nfqws-keenetic/openwrt/nfqws-keenetic.pub"
   opkg-key add /tmp/nfqws-keenetic.pub
   ```

3. Install the repository on the system
   ```bash
   echo "src/gz nfqws-keenetic https://anonym-tsk.github.io/nfqws-keenetic/openwrt" > /etc/opkg/nfqws-keenetic.conf
   ```
The repository is universal, supported architectures: `mipsel`, `mips`, `mips64`, `aarch64`, `armv7`, `x86`, `x86_64`, `lexra`.
   Для добавления поддержки новых устройств, [создайте Feature Request](https://github.com/Anonym-tsk/nfqws-keenetic/issues/new?template=feature_request.md&title=%5BFeature+request%5D+)

4. Install the package
   ```bash
   opkg update
   opkg install nfqws-keenetic
   ```

5. Install the web interface (optional)
   ```bash
   opkg install nfqws-keenetic-web
   ```

#### Versions 25.xx and Snapshot, package manager `apk`

1. Install required dependencies
   ```bash
   apk --update-cache add ca-certificates wget-ssl
   apk del wget-nossl
   ```

2. Set the repository public key
   ```bash
   wget -O "/etc/apk/keys/nfqws-keenetic.pem" "https://anonym-tsk.github.io/nfqws-keenetic/openwrt/nfqws-keenetic.pem"
   ```

3. Install the repository on the system
   ```bash
   echo "https://anonym-tsk.github.io/nfqws-keenetic/openwrt/packages.adb" > /etc/apk/repositories.d/nfqws-keenetic.list
   ```
The repository is universal, supported architectures: `mipsel`, `mips`, `mips64`, `aarch64`, `armv7`, `x86`, `x86_64`, `lexra`.
   Для добавления поддержки новых устройств, [создайте Feature Request](https://github.com/Anonym-tsk/nfqws-keenetic/issues/new?template=feature_request.md&title=%5BFeature+request%5D+)

4. Install the package
   ```bash
   apk --update-cache add nfqws-keenetic
   ```

5. Install the web interface (optional)
   ```bash
   apk add nfqws-keenetic-web
   ```

> [!NOTE]
> NB: All file paths described in this manual starting with `/opt` will start with the root `/` on OpenWRT.
> For example, the config is located in `/etc/nfqws/nfqws.conf`
> 
> To start/stop use the command `service nfqws-keenetic {start|stop|restart|reload|status}`

---

### Settings

Файл настроек расположен по пути `/opt/etc/nfqws/nfqws.conf`. Для редактирования можно воспользоваться встроенным редактором `vi` или установить `nano`.

```bash
# Интерфейс провайдера. Обычно `eth3` или `eth2.2` для проводного соединения, и `ppp0` для PPPoE
# Заполняется автоматически при установке
# Можно ввести несколько интерфейсов, например ISP_INTERFACE="eth3 nwg1"
# Для поиска интерфейса можно воспользоваться командами `route` или `ifconfig`
ISP_INTERFACE="..."

# Стратегии обработки HTTPS и QUIC трафика
NFQWS_ARGS="..."
NFQWS_ARGS_QUIC="..."

# Стратегия обработки UDP трафика (не использует параметры из NFQWS_EXTRA_ARGS)
NFQWS_ARGS_UDP="..."

# Режим работы (auto, list, all)
NFQWS_EXTRA_ARGS="..."

# IP-списки
NFQWS_ARGS_IPSET="..."

# Дополнительные стратегии
NFQWS_ARGS_CUSTOM=""

# Обрабатывать ли IPv6 соединения
IPV6_ENABLED=0|1

# TCP порты для iptables
# Оставьте пустым, если нужно отключить обработку TCP
# Добавьте порт 80 для обработки HTTP (TCP_PORTS=443,80)
TCP_PORTS=443(,80)

# UDP порты для iptables
# Оставьте пустым, если нужно отключить обработку UDP
# Удалите порт 443, если не нужно обрабатывать QUIC
UDP_PORTS=443(,50000:50099)

# Политика доступа (только для Keenetic/Netcraze)
POLICY_NAME="nfqws"

# Режим работы политики доступа
# 0 - обрабатывается трафик только для устройств в политике
# 1 - обрабатывается трафик для всех устройств, кроме добавленных в политику
POLICY_EXCLUDE=0|1

# Логирование в Syslog
LOG_LEVEL=0|1
```

The strategies apply to all domains from `user.list` and `auto.list`, with the exception of domains from `exclude.list`.<br/>
In the config there are 3 options for the `NFQWS_EXTRA_ARGS` parameter - this is the nfqws operating mode:
- In `$MODE_LIST` mode only domains from the `user.list` file will be processed
- In the `$MODE_AUTO` mode, in addition, unavailable domains will be automatically detected and added to the list by which `nfqws` processes traffic. The domain will be added if within 60 seconds it is determined 3 times that the resource is unavailable
- In `$MODE_ALL` mode all traffic will be processed except domains from the `exclude.list` list

Also, there are two IP lists: `ipset.list` and `ipset_exclude.list`.
Addresses from the lists are used in any operating mode.

---

### Useful

1. Конфиг-файл `/opt/etc/nfqws/nfqws.conf`
2. Скрипт запуска/остановки `/opt/etc/init.d/S51nfqws {start|stop|restart|reload|status}`
3. Вручную добавить домены в список можно в файле `/opt/etc/nfqws/user.list` (один домен на строке, поддомены учитываются автоматически)
4. Автоматически добавленные домены `/opt/etc/nfqws/auto.list`
5. Лог автоматически добавленных доменов `/opt/var/log/nfqws.log`
6. Домены-исключения `/opt/etc/nfqws/exclude.list` (один домен на строке, поддомены учитываются автоматически)
7. IP list for processing `ipset.list` (on each line ip or cidr ipv4, or ipv6)
8. IP list to exclude `ipset_exclude.list`
9. Check that the necessary rules have been added to the routing table `iptables-save | grep "queue-num 200"`
   > You should see similar lines
   > ```
   > -A POSTROUTING -o eth3 -p tcp -m tcp --dport 443 -m connbytes --connbytes 1:6 --connbytes-mode packets --connbytes-dir original -m mark ! --mark 0x40000000/0x40000000 -j NFQUEUE --queue-num 200 --queue-bypass
   > ```

### If nothing works...

1. If your device supports hardware acceleration (flow offloading, hardware nat, hardware acceleration), then iptables may not work.
When offloading is enabled, the packet does not go through the normal netfilter path.
It is necessary to either disable it or selectively manage it.
2. На Keenetic/Netcraze можно попробовать выключить или наоборот включить [сетевой ускоритель](https://help.keenetic.com/hc/ru/articles/214470905)
3. It may be worth turning off the IntelliQOS traffic classification service.
4. You can try disabling IPv6 on the ISP's network interface through the router's web interface.
5. You can try to block all UDP traffic on port 443 to disable QUIC:
   > Firewall → Home Network → Add Rule<br/>
   > Enable rule: Enabled<br/>
   > Description: Block QUIC<br/>
   > Action: Deny<br/>
   > Protocol: UDP<br/>
   > Destination port number: Equal to 443<br/>
   > We leave the remaining parameters unchanged

### Common problems
1. `iptables: No chain/target/match by that name`<br/>
The "Netfilter subsystem kernel modules" package is not installed. On Keenetic/Netcraze it appears in the list of packages only after installing "IPv6 Protocol"
2. `can't initialize ip6tables table` и/или `Perhaps ip6tables or your kernel needs to be upgraded`<br/>
The IPv6 protocol package is not installed. Also, the problem may appear on older firmware 2.xx, disable IPv6 support in the NFQWS config
3. Sight errors `readlink: not found`, `dirname: not found`<br/>
Usually do not occur on kinetics. The solution is to install busybox: `opkg install busybox` or separate packages `opkg install coreutils-readlink coreutils-dirname`
4. `Failed to download the package list from https://anonym-tsk.github.io/nfqws-keenetic/all/Packages.gz`<br/>
Most likely the `wget-ssl` package is not installed. If you are sure that it is installed, reinstall it: `opkg install --force-reinstall wget-ssl`

### How to use multiple strategies

You can add additional strategies to the `NFQWS_ARGS_CUSTOM` options in the config and separate them with the `--new` parameter.
For example, the strategy below will use the `--dpi-desync=fake,split2` option for HTTPS requests to domains from `custom.list`,
and for HTTP requests it will use `--dpi-desync=disorder2 --dpi-desync-fooling=md5sig,badseq`:
```bash
NFQWS_ARGS_CUSTOM="--filter-tcp=443 --dpi-desync=fake,split2 --hostlist=custom.list --new --filter-tcp=80 --dpi-desync=disorder2 --dpi-desync-fooling=md5sig,badseq"
```

### How to choose a working NFQWS strategy

1. Run the script and follow its instructions
   ```bash
   opkg install curl
   /bin/sh -c "$(curl -fsSL https://github.com/Anonym-tsk/nfqws-keenetic/raw/master/common/strategy.sh)"
   ```
   Подробнее можно почитать на [исходной странице](https://github.com/bol-van/zapret?tab=readme-ov-file#%D0%BF%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0-%D0%BF%D1%80%D0%BE%D0%B2%D0%B0%D0%B9%D0%B4%D0%B5%D1%80%D0%B0)

2. Найденную стратегию вписать в конфиге `/opt/etc/nfqws/nfqws.conf` в параметр `NFQWS_ARGS`

---

Нравится проект? Поддержи автора [здесь](https://yoomoney.ru/to/410019180291197) или [тут](https://pay.cloudtips.ru/p/054d0666). Купи ему немного :beers: или :coffee:!
