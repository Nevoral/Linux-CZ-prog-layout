# Adding a Customized Czech Keyboard Layout to Ubuntu

This guide will help you add a new keyboard layout to your Ubuntu system. The new layout is a full-size keyboard where the first layer is the Czech layout, and the second layer is the English layout with some changes and compromises.

## Step 1: Update `evdev.lst`

1. Open a terminal.
2. Edit the `evdev.lst` file located in `/usr/share/X11/xkb/rules/` directory with your preferred text editor (you may need root privileges to edit this file). For example, you can use `nano`:

   ```bash
   sudo nano /usr/share/X11/xkb/rules/evdev.lst
   ```

3. Scroll to the section where keyboard layouts are listed and add the following line:

   ```plaintext
   cz-prog         cz: Czech (prog)
   ```

4. Save and close the file.

## Step 2: Update `evdev.xml`

1. In the same `/usr/share/X11/xkb/rules/` directory, edit the `evdev.xml` file:

   ```bash
   sudo nano /usr/share/X11/xkb/rules/evdev.xml
   ```

2. Find the `cz` layout section and add the following code snippet under it:

   ```xml
   <variant>
      <configItem>
         <name>cz-prog</name>
         <description>Czech (prog)</description>
      </configItem>
   </variant>
   ```

3. Save and close the file.

## Step 3: Reboot Your System

For the changes to take effect, you need to restart your computer. You can do this from the terminal by typing:

```bash
sudo reboot
```

After the system reboots, the new keyboard layout should be available in your keyboard settings.
