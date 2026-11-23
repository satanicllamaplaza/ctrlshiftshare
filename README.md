# PROTOCOLS


## Make a wiping station
Use the mac tower with a bootable usb of nwipe.
Use insignia dual drive booth to wipe multiple drives at once.

## Drive Wipes
* For HDDs Use nwipe 1-pass zero wipe (sudo nwipe --method=prng --verify=last /location/
* For SSDs Use hdparm Secure Erase OR Parted Magic (sudo nwipe --method=dodshort --verify=last /location/)
* For drives donated with "disposal policies" adhere to the policies specified

### Log All Wiped Drives

This will be the full standard for documentation maintinance and organization.

quick pass fail helth check to save time on bad drives
```bash
sudo smartctl -H /drive/location/
```

Check drives health before spending time wiping it.
```bash
sudo smartctl -a /drive/location/
```

If the drive passes do a full wipe with log info for data keeping.
```bash
DEV=/drive/location/
SERIAL=$(lsblk -dno SERIAL $DEV)
sudo mkdir -p ~/wipe-logs
sudo nwipe --method=prng --verify=last \
  -l ~/wipe-logs/${SERIAL:-unknown}-$(date +%Y%m%d-%H%M).log \
  $DEV
```


# Collaborations
* Commerce Bucks Collab
* [non-profit wrench](https://www.nonprofitwrench.org/)
* [mower resource guide](https://www.uwmower.org/resource-guide.html)
# CTRL SHIFT SHARE
