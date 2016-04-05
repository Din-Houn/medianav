# Requirements #
Assuming an Ubuntu 9.10 desktop installation as the starting point, you'll need to add the following packages:
  * mplayer-nogui
  * lirc
  * python-pygame
  * python-pylirc

# Setting up the client #
  1. Rename the medianav.cfg.linux to medianav.cfg and modify it
  1. Copy lircrc.example to $HOME/.lircrc, the provided example works fine with Windows MCE remotes, if yours is a different make, you may need to modify the controls
  1. 


# EXPERIMENTAL: Lean and mean dedicated medianav frontend #

These are the steps I'm taking to get a lean and mean medianav frontend machine. Documenting them here just in case it happens to work out well :)

  1. Install a base Ubuntu system, using the "Command-line only" option from the Alternate installer CD (I used 9.10 32-bit)
  1. Install a few packages:
    * build-essential (required for installing NVidia drivers, possibly others too)
    * nfs-common (assuming your media are stored on an NFS share)
    * portmap (needed for NFS mounting)
    * pulseaudio
    * 