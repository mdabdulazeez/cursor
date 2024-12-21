# Cursor Installation Guide for Linux

## Installation Methods

### Method 1: Download from Website
1. Visit [Cursor's official website](https://www.cursor.so/)
2. Click "Download for Linux"
3. Rename the downloaded file:
```bash
mv cursor-0.44.5-build-241220s3ux0e1tv-x86_64.AppImage cursor.AppImage
```

### Method 2: Using curl
```bash
curl -L https://cursor-app-release.s3.amazonaws.com/Cursor-latest.AppImage -o cursor.AppImage
```

## Installation Steps

1. Make the AppImage executable:
```bash
chmod +x cursor.AppImage
```

2. Install FUSE dependency:
```bash
sudo add-apt-repository universe
sudo apt install libfuse2
```

3. Create directory and move file:
```bash
sudo mkdir -p /opt/cursor
sudo mv cursor.AppImage /opt/cursor/cursor.appimage
```

4. Create desktop entry:
```bash
sudo nano /usr/share/applications/cursor.desktop
```

5. Add the following content to the desktop entry:
```
[Desktop Entry]
Version=1.0
Name=Cursor
Comment=Open Cursor Application
Exec=/opt/cursor/cursor.appimage
Icon=/opt/cursor/cursor.png
Terminal=false
Type=Application
Categories=Utility;
```

6. Download the icon:
```bash
sudo curl -L https://cursor.sh/apple-touch-icon.png -o /opt/cursor/cursor.png
```

7. Make the desktop entry executable:
```bash
sudo chmod +x /usr/share/applications/cursor.desktop
```

## Running Cursor

You can launch Cursor in two ways:

1. From the applications menu (search for "Cursor")
2. From the terminal:
```bash
/opt/cursor/cursor.appimage
```

## Troubleshooting

If you encounter the error "dlopen(): error loading libfuse.so.2", make sure you have installed the FUSE dependency as mentioned in step 2.

## Uninstallation

To uninstall Cursor, run these commands:
```bash
sudo rm /opt/cursor/cursor.appimage
sudo rm /opt/cursor/cursor.png
sudo rm /usr/share/applications/cursor.desktop
sudo rmdir /opt/cursor
```

## Support

For additional support or to report issues, visit:
- [Cursor's official website](https://www.cursor.so/)
- [Cursor's GitHub repository](https://github.com/getcursor/cursor)
