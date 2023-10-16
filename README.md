
# TCP-UDP

Nama : Andrian Tambunan
NRP : 5025211018

## No.1
"What is the IP address and TCP port number used by the client computer (source) that is transferring the alice.txt file to gaia.cs.umass.edu? To answer this question, it’s probably easiest to select an HTTP message and explore the details of the TCP packet used to carry this HTTP message, using the “details of the selected packet header window” (refer to Figure 2 in the “Getting Started with Wireshark” Lab if you’re uncertain about the Wireshark windows)."

Masukkan Filter `http` dan Transmission Control Protocol akan muncul.
```
Ip Address : 192.168.0.24
Port       : 653400
```
![image](https://github.com/AndrianTambunan/TCP-UDP/assets/100081922/47b2b37b-53c5-4d4f-851a-92d188dd019c)

## No.2
"What is the IP address of gaia.cs.umass.edu? On what port number is it sending and receiving TCP segments for this connection?"

IP Address dari gaia.cs.umass.edu adalah sebagai berikut
```
IP Address : 128.119.245.12
Port       : 80
```
![image](https://github.com/AndrianTambunan/TCP-UDP/assets/100081922/8d0b9a98-e7b4-4f9d-b10d-fd4efad8027c)

## No.3
"What is the sequence number of the TCP SYN segment that is used to initiate the TCP connection between the client computer and gaia.cs.umass.edu? (Note: this is the “raw” sequence number carried in the TCP segment itself; it is NOT the packet # in the “No.” column in the Wireshark window. Remember there is no such thing as a “packet number” in TCP or UDP; as you know, there are sequence numbers in TCP and that’s what we’re after here. Also note that this is not the relative sequence number with respect to the starting sequence number of this TCP session.). What is it in this TCP segment that identifies the segment as a SYN segment? Will the TCP receiver in this session be able to use Selective Acknowledgments (allowing TCP to function a bit more like a “selective repeat” receiver, see section 3.4.5 in the text)?"

Masukkan Filter `tcp.flags.syn == 1 and ip.dst == 128.119.245.12`, dan Filter tersebut hanya akan menampilkan packet yang memiliki flag TCP SYN dengan tujuan ke gaia.cs.umass.edu.

```
TCP SYN sequence number (raw) : 590476643
```
![image](https://github.com/AndrianTambunan/TCP-UDP/assets/100081922/93cff38e-6215-430b-a2e9-9a2672400985)

## No.4
"What is the sequence number of the SYNACK segment sent by gaia.cs.umass.edu to the client computer in reply to the SYN? What is it in the segment that identifies the segment as a SYNACK segment? What is the value of the Acknowledgement field in the SYNACK segment? How did gaia.cs.umass.edu determine that value?"

Pilih `ACK` dan didapatkan sebagai berikut.

```
Sequence number : 1068969752
```
## No.5
"What is the sequence number of the TCP segment containing the header of the HTTP POST command? Note that in order to find the POST message header, you’ll need to dig into the packet content field at the bottom of the Wireshark window, looking for a segment with the ASCII text “POST” within its DATA field. How many bytes of data are contained in the payload (data) field of this TCP segment? Did all of the data in the transferred file alice.txt fit into this single segment?"

Pilih `SYN` lalu didapatkan hasil seperti berikut.

```
Sequence number : 
```
## No.6
"Consider the TCP segment containing the HTTP “POST” as the first segment in the data transfer part of the TCP connection."

Masukkan filter `http.request.method == "POST"`.
Didapatkan `Sequence Numbernya adalah 151595` dan `RAW Sequence Numbernya adalah 2479418499`
![image](https://github.com/AndrianTambunan/TCP-UDP/assets/100081922/6597a5e6-bd31-477e-bae2-93f0fba0a744)

### No. 6a
"At what time was the first segment (the one containing the HTTP POST) in the data-transfer part of the TCP connection sent?"

Dan Didapatkan data Arrival pada
```
Arrival Time: Oct 16, 2023 23:01:18.822429000 SE Asia Standard Time
```
![image](https://github.com/AndrianTambunan/TCP-UDP/assets/100081922/cb0e0377-8bfb-447f-8720-506ad9e0683a)

## No. 6b
"What is the EstimatedRTT value (see Section 3.5.3, in the text) after the ACK for the second data-carrying segment is received? Assume that in making this calculation after the received of the ACK for the second segment, that the initial value of EstimatedRTT is equal to the measured RTT for the first segment, and then is computed using the EstimatedRTT equation on page 242, and a value of alpha = 0.125. Note: Wireshark has a nice feature that allows you to plot the RTT for each of the TCP segments sent. Select a TCP segment in the “listing of captured packets” window that is being sent from the client to the gaia.cs.umass.edu server. Then select: Statistics->TCP Stream Graph-Round Trip Time Graph."

Dan Didapatkan data Responce pada:
```
Arrival Time: Oct 16, 2023 23:01:40.833444251 SE Asia Standard Time
```
Dari dua informasi diatas bisa didapatkan bahwa `RTT` atau Round Trip Time dari data yang di `POST` adalah `0.11015251s`.

## No.7
"What is the length (header plus payload) of each of the first four data-carrying TCP segments?"

Fisrt Frame Length 7
```
Frame 933: **1495 bytes** on wire (11960 bits), 1495 bytes captured (11960 bits) on interface en0, id 0
```
![image](https://github.com/AndrianTambunan/TCP-UDP/assets/100081922/430509bb-ce7c-4aaa-8f54-71d683cb7817)

Second Frame Length 7
```
Frame 179: **831 bytes** on wire (6648 bits), 831 bytes captured (6648 bits) on interface en0, id 0
```
