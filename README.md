# OTRS-Ticket-Notification-To-Telegram-Agent
- Built for OTRS CE v 6.0.x
- Send a PERSONAL telegram notification to agent upon ticket action. E.g: TicketQueueUpdate

1. A telegram bot must be created by chat with @FatherBot and obtain the token via Telegram.

2. Update the telegram bot token at System Configuration > TicketTelegramAgent::Token

3. Admin must create a new Generic Agent (GA) with option to execute custom module.


Execute Custom Module => Module => Kernel::System::Ticket::Event::TicketTelegramAgent
	
[MANDATORY PARAM]
	
Param 1 Key => ChatIDField   
Param 1 Value => UserComment  
#Which user field that hold the chat id. This value must be present
	
Param 2 Key => RCPT  
Param 2 Value => Owner;Responsible;CreateBy;RW  
#Either one of this value must be present.
	
Param 3 Key => RCPTRole  
Param 3 Value => *Role name separated by semicolon (;)  
#This value must be present. Can be anything.
	
Param 4 Key => RCPTAgent  
Param 4 Value => *Specific agent username / login name separated by semicolon (;)  
#This value must be present. Can be anything.  
	
Param 5 Key => Text1  
Param 5 Value => *Text to be sent to the user.  
#Also support OTRS ticket TAG only. bold, newline must be in HTML code.  
#Also support <OTRS_NOTIFICATION_RECIPIENT_UserFullname>, <OTRS_OWNER_UserFullname>, <OTRS_RESPONSIBLE_UserFullname> and <OTRS_CUSTOMER_UserFullname> tag.
	
[OPTINAL PARAM]
	
Param 6 Key => Text2  
Param 6 Value => *Additional text to be sent to the user.  
#Also support OTRS ticket TAG only. bold, newline must be in HTML code.  
#Also support <OTRS_NOTIFICATION_RECIPIENT_UserFullname>, <OTRS_OWNER_UserFullname>, <OTRS_RESPONSIBLE_UserFullname> and <OTRS_CUSTOMER_UserFullname> tag.
	
	
4. Obtain the telegram chat_id for the agent, and update it into Agent Profile in Comment field. 	

- Based on Generic Agent, UserComment field has been selected as chat id field  
- An agent must start the conversation with the created telegram bot (no 1) first by using telegram.  
- By using  https://api.telegram.org/botYOURTOKENHERE/getUpdates , we can obtain the chat_id of the agent.

[![download-1.png](https://i.postimg.cc/QNf20txj/download-1.png)](https://postimg.cc/14N7zyqd)	
	
