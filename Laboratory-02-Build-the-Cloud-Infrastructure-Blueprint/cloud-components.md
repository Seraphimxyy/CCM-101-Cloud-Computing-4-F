# Compute Resources
- Purpose: The compute resource in this environment is the CPU, which is responsible for processing commands and running the calculations that make the machine actually work.
- Why it matters in cloud computing: Compute matters in cloud computing because you need processing power to run anything, and instead of buying your own computer or server, you're basically renting that processing power from the cloud provider.
- Relation to the KillerCoda environment: In this KillerCoda server, the compute resource I identified was an Intel Xeon E312xx (Sandy Bridge) with 1 core, which seems pretty small compared to a real computer, but that's likely normal for a free lab environment since it's meant for practicing commands, not running anything heavy.
# Storage Resources
- Purpose: Storage refers to where files and data are saved and kept on a computer or server.
- Why it matters in cloud computing: This is important in cloud computing because data needs to be saved somewhere reliable and accessible, and with cloud storage you don't have to worry about running out of space on your own device.
- Relation to the KillerCoda environment: My server has a 19G disk (/dev/vda1) mounted at /, which I'm assuming works as the storage space for this whole server, similar to how my laptop has a hard drive with a set amount of GB.
# Networking Resources
- Purpose: Networking allows computers and servers to connect and send information to each other instead of working in isolation.
- Why it matters in cloud computing: In cloud computing, networking is essential because servers and services are spread across different locations, so they need a way to communicate for anything to work properly.
- Relation to the KillerCoda environment: My server's IP address is 172.30.1.2 on interface enp1s0, which means it has its own address inside this KillerCoda setup so it can send and receive data, even though I don't fully understand yet how all of that works behind the scenes.
# Operating System
- Purpose: The OS manages the hardware (like the CPU and storage) and lets me actually use the computer through commands instead of interacting with the hardware directly.
- Why it matters in cloud computing: In the cloud, the OS is important because it's the actual software environment you're working in, and it determines what tools and commands are even available.
- Relation to the KillerCoda environment: My environment runs Ubuntu 24.04.4 LTS (kernel 6.8.0-136-generic), which is the specific OS I've been using this whole time, and knowing the version and kernel helps show exactly what setup I was working with.
