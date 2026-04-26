# HID Linux VM Initial Setup Automation

Projekt przedstawia kontrolowany payload HID służący do automatyzacji początkowej konfiguracji maszyny Linux uruchomionej w VMware Workstation. Rozwiązanie zostało przygotowane jako element homelabu SOC i służy do demonstracji automatyzacji konfiguracji systemu oraz zrozumienia ryzyk związanych z urządzeniami klasy HID.

Payload uruchamia terminal w systemie Ubuntu Desktop, tworzy lokalny skrypt Bash, a następnie wykonuje podstawowy setup systemu, instalację narzędzi administracyjnych oraz wybrane elementy hardeningu.

> Projekt został przygotowany wyłącznie do użycia w kontrolowanym środowisku laboratoryjnym i na własnych maszynach wirtualnych.

---

## Cel projektu

Celem projektu jest automatyzacja powtarzalnych czynności wykonywanych po instalacji systemu Linux w środowisku VMware Workstation.

Projekt pokazuje praktyczne podejście do:

- automatyzacji konfiguracji systemu Linux,
- podstawowego hardeningu Ubuntu,
- przygotowania hosta do pracy w homelabie SOC,
- wykorzystania urządzeń HID w kontrolowanym scenariuszu administracyjnym,
- dokumentowania i standaryzacji procesu wdrożenia VM.

---

## Środowisko testowe

Payload był projektowany z myślą o następującym środowisku:

| Komponent | Wartość |
|---|---|
| Hypervisor | VMware Workstation |
| System gościa | Ubuntu Desktop 22.04 / 24.04 |
| Typ automatyzacji | HID Payload |
| Shell | Bash |
| Uprawnienia | Użytkownik z dostępem do `sudo` |
| Układ klawiatury | US |
| Zastosowanie | Homelab / SOC Lab |

---

## Zakres automatyzacji

Payload wykonuje następujące działania:

- aktualizuje system,
- instaluje VMware Tools,
- instaluje podstawowe narzędzia administracyjne,
- instaluje narzędzia sieciowe,
- włącza usługę SSH,
- konfiguruje zaporę UFW,
- instaluje i uruchamia `fail2ban`,
- instaluje i konfiguruje `auditd`,
- dodaje podstawowe reguły audytu,
- wykonuje podstawowy hardening SSH,
- uruchamia szybki audyt systemu za pomocą Lynis,
- wyświetla podstawowe informacje o systemie, adresach IP i otwartych portach.

---

## Instalowane pakiety

W ramach procesu instalowane są między innymi:

```bash
open-vm-tools
open-vm-tools-desktop
curl
wget
git
vim
nano
htop
net-tools
dnsutils
iputils-ping
traceroute
nmap
tcpdump
openssh-server
ufw
fail2ban
auditd
rsyslog
lynis
chkrootkit
rkhunter
python3
python3-pip
python3-venv
