# Linux suckless settings, mostly for Ubuntu

## Remove Snap on Ubuntu[^1]:

- Check pre-installed snaps:
  ```sh
  snap list
  ```
- Remove snaps by order:
  ```sh
  snap remove firefox
  snap remove gtk-common-themes
  snap remove ...
  snap remove snpad-desktop-integration
  snap remove snap-store
  snap remove core20
  snap remove bare
  snap remove snapd
  ```
- Remove `snapd` daemon:
  ```sh
  sudo systemctl stop snapd
  sudo systemctl disable snpad
  sudo systemctl mask snapd
  sudo apt purge snapd -y
  sudo apt-mark hold snpad
  ```
- Preventing Snap installatin through `apt` command:
  ```sh
  sudo cat <<EOF | sudo tee /etc/apt/preferences.d/nosnap.pref
  Package: snapd
  Pin: release a=*
  Pin-Priority: -10
  EOF
  ```
- Remove leftover Snap directories:
  ```sh
  rm -rf ~/snap
  sudo rm -rf /snap
  sudo rm -rf /var/snap
  sudo rm -rf /var/lib/snpad
  ```

## Disable ubuntu ESM messages in MOTD[^2]

- Create an empty file as following:
  ```sh
  sudo touch /var/lib/update-notifier/hide-esm-in-motd
  ```
- Enforce MOTD settings update:
  ```sh
  sudo /usr/lib/update-notifier/update-motd-updates-available --force
  ```

## Disable ubuntu waiting for network to be configured while boot[^3][^4]

- Commands to list network interfaces:
  ```sh
  sudo lshw -class network -short # only hardware interfaces
  ip link show
  ls /sys/class/net/
  nmcli device status
  netstat -i
  ifconfig -s -a
  sudo hwinfo --short --network
  iwconfig
  ```
- Add `optional: true` at all interfaces in `/etc/netplan/XXX.yaml`:
  - For example, my `XXX.yaml` is `01-network-manager-all.yaml` or `00-installer-config.yaml` on different machine.
  - Add `optional: true` to each interface, e.g.
    ```yml
    # This is the network config written by 'subiquity'
    network:
      ethernets:
        enp113s0:
          dhcp4: true
          optional: true
        enp114s0:
          dhcp4: true
          optional: true
        enx00e04c551144:
          dhcp4: true
          optional: true
      version: 2
    ```
- Apply new netplan:
  ```sh
  sudo netplan generate && sudo netplan apply
  ```

## Hardening ssh on server:

- Steps in [here](./server/ssh.md).

[^1]: https://www.baeldung.com/linux/snap-remove-disable

[^2]: https://canonical-ubuntu-pro-client.readthedocs-hosted.com/en/latest/explanations/motd_messages/

[^3]: https://askubuntu.com/questions/972215/a-start-job-is-running-for-wait-for-network-to-be-configured-ubuntu-server-17-1

[^4]: https://ubuntu.com/server/docs/configuring-networks
