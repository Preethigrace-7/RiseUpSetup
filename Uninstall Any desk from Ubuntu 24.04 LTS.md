
# Uninstall AnyDesk from Ubuntu

This guide provides step-by-step instructions to uninstall AnyDesk from an Ubuntu system completely.

---

## Step 1: Remove the AnyDesk Package

Use the following command to remove AnyDesk and its configuration files:

```bash
sudo apt remove --purge anydesk -y
```

---

## Step 2: Remove the AnyDesk APT Repository and GPG Key

Delete the AnyDesk repository entry:

```bash
sudo rm -f /etc/apt/sources.list.d/anydesk-stable.list
```

Delete the GPG key used for verifying AnyDesk packages:

```bash
sudo rm -f /etc/apt/keyrings/keys.anydesk.com.asc
```

---

## Step 3: Remove AnyDesk Configuration and Cache Files

Remove any local user and system configuration files:

```bash
rm -rf ~/.anydesk
sudo rm -rf /var/lib/anydesk
```

---

## Step 4: Clean Up Unused Dependencies

Clean up any remaining unused dependencies:

```bash
sudo apt autoremove -y
sudo apt clean
```

---

## Step 5: Verify Uninstallation

Check if AnyDesk is still installed:

```bash
anydesk --version
```

If the output is `command not found`, AnyDesk has been successfully uninstalled.

---
```
✅ You're done! AnyDesk has been fully removed from your system.
```

Resources:
[Youtube video link]()
