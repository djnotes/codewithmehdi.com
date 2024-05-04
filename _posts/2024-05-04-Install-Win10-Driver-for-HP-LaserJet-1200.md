# Install Windows 10 driver for HP LaserJet 1200 printer

Today I had to install driver for HP LaserJet 1200 on a client's computer and I had a hard time making the printer work. The reason: The latest Universal PCL 6 printer driver offered on the HP site turned out not to be compatible with Windows 10, through there nothing written about it on the downloads page. I kept seeing an error message on the printed test pages. 

## The Errors
Error was something like: Pcl XL error Unsupported Protocol 

## Solution
It struck my mind that the printer, being an old machine, might need an older printer driver like PCL 5, and a search on Google showed that PCL 6 (a.k.a PCL XL) is very different from PCL 5. So, I looked for LaserJet 1200 printer PCL 5. There are not many options on the Internet. Finally, I found the driver's files in a zip on Driver Pack's website. You don't need the Driver Pack app to install the driver.

## How to Install 
I assume you downloaded and unzipped the driver for HP LaserJet 1200 PCL 5 on your system. To install the printer correctly, go to printers and hit Add Printer. Then select the model from the list and then find the button Have Disk instead of selecting Windows drivers. Then, give it the path where you unzipped the driver. It will install the driver and might even launch an installer mid-way. Nevertheless, you should have no problem after the driver gets installed. Hit Print Test Page on the final page and get your first (hopefully) successful printout.

## How to Print Multiple Copies using HP Printer
In case your printer does not print multiple copies of a page despite being told so in the print page, do the following:

- Right click printer and select Printer Properties
- Select Device Properties
- Scroll down to Mopier setting and disable it. Now, the driver should send multiple copies to the printer when you set print count to more then 1
