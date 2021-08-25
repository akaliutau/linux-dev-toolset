## Step 1: Check What Graphics Card

```
lspci -k | grep -A 2 -i "VGA"
```

## Step 2: Check What Graphics Card the Laptop is Using

go to system settings > details

## Step 3: drivers installation

enter the following command to see which binary driver is recommended for your specific card.

```
sudo ubuntu-drivers devices
```

if, for example, nvidia-352 is recommended for my Nvidia card, then enter the following command to install it.

```
sudo apt-get install nvidia-352
```

## Step 4: switch drivers if needed

```
sudo prime-select intel
```