# Guide-to-Fixing-Ubuntu-22.04-After-You-ve-Nuked-Python-3.10


If you've accidentally wrecked your Python installation on a Debian-based system like Ubuntu, you're in for a wild ride. Though the fix might seem trivial, messing up Python can tie your system into knots in ways you wouldn't believe. So, for those unlucky enough to have blundered like I have, here’s how to claw your way back:


## Step 1: Don’t Panic and Don't Reboot

If you corrupt your Python, things might seem fine—at first. But the moment you try to open bash or zsh, you'll know something’s up. If you realize your mistake, do not reboot your machine. Cause you midght still be able to use your browser which makes the whole process less of a hussle and you can jump to Step 4. If your system is fresh with little to no important data, it might be easier to just wipe it and reinstall Ubuntu. Trust me, it could save you days of headache.


 ## Step 2: If You've Rebooted and It's All Gone Pear-Shaped

Maybe you rebooted, and now your graphics are gone. First things first, you’ll need to boot into a root shell. This part is crucial and thankfully, doesn't rely on Python. Here’s a lifeline: [How do I boot into a root shell?](https://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell).


### Step 3: Forget `apt`, It’s Not Your Friend Here
You might think, "Ah, I’ll just use apt to fix my Python." Nope. Apt depends on Python, and you just torpedoed Python. All those Stack Overflow posts and guides telling you to use apt? Ignore them. They’re dead ends here.

### Step 4: Time to Go Old School with `curl` or `wget`
Next up, you need to manually fetch the damaged or missing Python *.deb files. You’ll find your salvation summarised beautifully in this response: [Ubuntu 16.04 completely broken Python3, dpkg, apt-get](https://askubuntu.com/questions/1092919/ubuntu-16-04-completely-broken-python3-dpkg-apt-get). But for your Ubuntu 22.04 system, check out the mirrors for the Python dependencies you need on your smartphone or another device.

### Step 5: Download and Deploy with `dpkg`
Head over to [packages.ubuntu.com](https://packages.ubuntu.com), search for the Python3 package, and grab these guys:
- `python3`
- `python3-minimal`
- `libpython3-stdlib`
- `python 3.10`

It is import to note again, you midght need more installations, but you will realize, as apt keeps breaking if you are not done.

Make sure they match your Ubuntu release to avoid further chaos. Once downloaded, install them in the correct order as you can observe this  [link](https://packages.ubuntu.com/jammy/python/python3) here is an example from this answer [answer](https://askubuntu.com/questions/1487336/how-to-fix-the-error-of-complete-removing-python-from-ubuntu-20-04)
```bash
cd ~/Downloads
sudo dpkg -i python3-minimal_3.10.6-1~22.04_amd64.deb
sudo dpkg -i libpython3-stdlib_3.10.6-1~22.04_amd64.deb
sudo dpkg -i python3.10_3.10.12-1~22.04.2_amd64.deb
sudo dpkg -i python3_3.10.6-1~22.04_amd64.deb

```

### Step 6: Fix the Mess with `apt-get install -f`
After running those dpkg commands, you might still have dependencies crying for attention. Fire up `sudo apt-get install -f` to automatically pick up the pieces. This should finally stitch your system back together.

### Step 7: Reboot and Cross Your Fingers
Once you’ve battled through the steps above, reboot your machine. With a bit of luck and a lot of crossed fingers, your graphical interface and everything else should spring back to life.

### Conclusion
Moral of the story? Messing with your Python installation on Ubuntu can unleash all sorts of chaos. For those looking to experiment with different Python versions, consider safer alternatives like VMs, containers, or virtual environments to keep your main system stable and functioning.
Thansk to the people that actually gave answer that where based on knowledge and not copy pasting crap others where mindlessly commenting.
### References
- [Ask Ubuntu - Boot into a Root Shell](https://askubuntu.com/questions/92556/how-do-i-boot-into-a-root-shell)
- [Ask Ubuntu - Broken Python3, Dpkg, Apt-get](https://askubuntu.com/questions/1092919/ubuntu-16-04-completely-broken-python3-dpkg-apt-get)
- [Packages Ubuntu - Python Dependencies](https://packages.ubuntu.com/jammy/python/python3)
- [Unix & Linux Stack Exchange - Install Package with Dependencies Using Dpkg](https://unix.stackexchange.com/questions/366488/how-to-use-dpkg-i-to-install-package-and-dependencies-where-dependencies-are-al)

So, here you go. Follow these steps, and hopefully, you'll get your system back on track without too much despair. Good luck!
