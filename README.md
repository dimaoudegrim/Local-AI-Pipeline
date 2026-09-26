# Local-AI-Pipeline
Local AI Pipeline with private and secure connection between Desktop to remote phones and laptop.
- The pipeline:
1.	On a Desktop with 16 GB Vram (AMD GPU) I have LM studio or Lmstudio bionic with Gemma 4 26b a4b qat. It act as a server with exposed api to the local network.
2.	On a raspberry pi on the local network I have a docker with openweb ui on it that connected to the api.
3.	For https I have on the raspberry pi a component called caddy.
4.	The open webui is set to enable web search with a toggle on the chat itself. The interface set to temporary chats without saving chats. The model set to not remember memories or checking older chats.
5.	On the raspberry pi installed Twingate connector as ZTNA. On twingate I set a resource with specific port and alias for the internal domain name.
6.	On Android phone I've set inside a secure folder the twingate app, so it won't interfere with the tunneling protocol  I have on the standard profile (Check point harmony mobile MTD).
7.	I've installed Caddy generated ca cert on the secure folder. I've enable the debug secret menu on Firefox on the secure folder, so I would be able to set firefox to use third party CA certificates. 
8.	Connecting to Twingate via fingerprint and from there to the https internal site I've set of open webui.
<img width="1300" height="719" alt="1790438439576" src="https://github.com/user-attachments/assets/a86ca4c4-a6ee-4905-98b2-f4758e221b54" />
