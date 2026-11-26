<html>
	<script type='text/javascript'>
		function initEmbeddedMessaging() {
			try {
				embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'
				
				const CHAT_ORIGIN = "https://ne1795216183744.my.site.com";
				const KEY = "chatPrechatPrompt";
				
				// 1. Store when the LWC posts it
				window.addEventListener("message", (e) => {
				    if (e.origin !== CHAT_ORIGIN || e.data?.source !== "prechat") return;
				    const prompt = e.data.value["How can I help you?"];
				    try { 
						sessionStorage.setItem(KEY, prompt); 
					} catch (err) { 
						console.warn(err);
					}
				    window.pendingPrompt = prompt;   // in-memory fallback
				});
				
				// 2. Use it when the first bot message is sent
				window.addEventListener("onEmbeddedMessagingFirstBotMessageSent", (e) => {
				    let prompt = window.pendingPrompt;
				    try { 
						prompt = prompt ?? sessionStorage.getItem(KEY); 
					} catch (err) {
						console.warn(err);
					}
				
				    console.log("First bot message sent. Prompt was:", prompt);
				    console.log("Event detail:", e.detail);   // SSE payload
				    embeddedservice_bootstrap.utilAPI.sendTextMessage(prompt)
				      .then(() => {
				        console.log('Message Sent');
				      }).catch(() => {
				        console.log('Message not Sent');
				      }).finally(() => {
				        console.log('Message Sent Finally');
				      });
				});
				
				// 3. Clean up when the conversation or window ends
				["onEmbeddedMessagingConversationClosed", "onEmbeddedMessagingWindowClosed"].forEach(name =>
				    window.addEventListener(name, () => {
				        window.pendingPrompt = null;
				        try { 
						sessionStorage.removeItem(KEY); 
						} catch (err) {
							console.warn(err);
						}
				    })
				);
				
				embeddedservice_bootstrap.init(
					'00Dg700000Rtlht',
					'Chat',
					'https://ne1795216183744.my.site.com/ESWChat1795635463722',
					{
						scrt2URL: 'https://ne1795216183744.my.salesforce-scrt.com'
					}
				);
			} catch (err) {
				console.error('Error loading Embedded Messaging: ', err);
			}
		};
	</script>
	<script type='text/javascript' src='https://ne1795216183744.my.site.com/ESWChat1795635463722/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>
</html>
