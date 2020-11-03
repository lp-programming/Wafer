# Wafer
Wayland Based Thin Client

Started for the Level1Techs Devember2020 event ( https://forum.level1techs.com/t/wayland-thin-client/163291 ).
The goal of this project is to create a Thin client for use with a Linux server and Linux clients using the Wayland protocol over a high speed LAN.
Applications running on the server should have full 3d acceleration, same as for a local user.  
CPU consumption on the clients should be minimal, suitable for a raspberry pi or similar.

As there are multiple servers and clients involved, including software components which simultaneously act as both a client and server, the following terminology is used throughought the project to avoid ambiguity.


1. **Wafer**
  Working name for the project, and for the client and server halves considered together.  
1. **Mainframe**
    A powerful multi-core machine with a GPU supporting the GBM protocol, and gigabit or better ethernet.
  For testing, will be my ryzen 3800x machine.
1. **Thin Client**
  A low powered linux machine with USB input and 1 display output, also with gigabit ethernet.
  For testing, will be one or more Raspberry Pis.
1. **Wayland Client Compositor**
  A wayland compositor (kde/gnome/weston) running on the *Mainframe* and outputting to the *Thin Wayland Compositor*.
1.  **Thin Wayland Compositor**
     The server half of the *Wayland ThinClient*.  Runs on the *Mainframe*, exposes the Wayland Server protocol via a unix socket on *Mainframe*.  
  Expects a single *Wayland Client Compositor*
1.  **Thin Wayland Client**
  The client half of the *Wayland ThinClient*, runs on the *Thin Client* and outputs to either a kernel frame buffer, or to another Wayland Compositor.
1.  **Client Application**
  An actual application a user wants to run (firefox, libreoffice, et cetera).  
