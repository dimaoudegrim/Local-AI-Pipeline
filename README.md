# Local-AI-Pipeline
Local AI Pipeline with private and secure connection between Desktop to remote phones and laptop.
- The pipeline:
1.	On a Desktop with 16 GB Vram (AMD GPU) I have LM studio or Lmstudio bionic with Gemma 4 26b a4b qat. It act as a server with exposed api to the local network.
2.	On a raspberry pi on the local network I have a docker with open webui on it that connected to the api.
3.	For https I have on the raspberry pi a component called caddy.
4.	The open webui is set to enable web search with a toggle on the chat itself. The interface set to temporary chats without saving chats. The model set to not remember memories or checking older chats.
5.	On the raspberry pi installed Twingate connector as ZTNA. On twingate I set a resource with specific port and alias for the internal domain name.

# Android setup
6.	On Android phone I've set inside a secure folder the twingate app, so it won't interfere with the tunneling protocol  I have on the standard profile (Check point harmony mobile MTD).
7.	I've installed Caddy generated ca cert on the secure folder. I've enable the debug secret menu on Firefox on the secure folder, so I would be able to set firefox to use third party CA certificates. 
8.	Connecting to Twingate via fingerprint and from there to the https internal site I've set of open webui.
<img width="1300" height="719" alt="1790438439576" src="https://github.com/user-attachments/assets/a86ca4c4-a6ee-4905-98b2-f4758e221b54" />

# Integration as chat bot within Firefox (Open webui).
<img width="2718" height="1468" alt="local ai browser" src="https://github.com/user-attachments/assets/1a17464b-a354-45a9-bc53-8d33a8f32580" />
Set the following configurations, just adjust URL and queries to your needs:

* Enter about:config
  
* browser.ml.chat.provider  = https://example.com:3000/?web-search=true
* browser.ml.chat.prompts.{0} = true
* browser.ml.chat.prompts.{1} = true
* browser.ml.chat.prompts.{2} = true
* browser.ml.chat.prompts.{3} = true
* browser.ml.chat.prompts.0 = {"label": "סיכום בעברית", "value": "Please summarize the content of this page in Hebrew. URL: %url%"}
* browser.ml.chat.prompts.1 = {"label": "חוות דעת על הדף", "value": ",תן חוות דעת על התוכן כאן. URL: %url%"}
* browser.ml.chat.prompts.2 = {"label": "תמצית סימון", "value": ",תצמצת לי את התוכן המסומן. Selection: %selection%"}
* browser.ml.chat.prompts.3 = {"label": "חוות דעת על הסימון", "value": ",תן חוות דעת על התוכן כאן. Selection: %selection%"}
