################################################################################
# Add-on: HAOS Kiosk Display (haoskiosk)
# File: Dockerfile
# Version: 0.9.8.2
# Copyright Jeff Kosowsky
# Date: June 2025
################################################################################

ARG BUILD_FROM
FROM $BUILD_FROM

# Install Luakit and necessary dependencies
RUN apk update && apk add --no-cache \
    luakit \
    xorg-server \
    xf86-video-fbdev \
    xf86-input-evdev \
    openbox \
    ttf-dejavu \
    util-linux \
    xset \
    xdotool \
    bash \
    && rm -rf /var/cache/apk/*

# Set the display variable
ENV DISPLAY=:0

# Copy over 'xorg.conf' and lua 'userconf.lua' file
COPY xorg.conf /etc/X11/xorg.conf
COPY userconf.lua /root/.config/luakit/userconf.lua
COPY translations/*.yaml /translations/

COPY run.sh /
RUN chmod a+x /run.sh

CMD ["/run.sh"]
