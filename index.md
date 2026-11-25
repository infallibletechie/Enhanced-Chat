<html>
	<script type='text/javascript'>
	function initEmbeddedMessaging() {
		try {
			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'
			
			const CHAT_ORIGIN = "https://infallibletechieagentforce-dev-ed.develop.my.site.com";
			const KEY = "chatPrechatPrompt";
			
			// 1. Store when the LWC posts it
			window.addEventListener("message", (e) => {
			    if (e.origin !== CHAT_ORIGIN || e.data?.source !== "prechat") return;
			    const prompt = e.data.value["How can I help you?"];
			    try { sessionStorage.setItem(KEY, prompt); } catch (err) { /* storage blocked */ }
			    window.pendingPrompt = prompt;   // in-memory fallback
			});
			
			// 2. Use it when the first bot message is sent
			window.addEventListener("onEmbeddedMessagingFirstBotMessageSent", (e) => {
			    let prompt = window.pendingPrompt;
			    try { prompt = prompt ?? sessionStorage.getItem(KEY); } catch (err) {}
			
			    console.log("First bot message sent. Prompt was:", prompt);
			    console.log("Event detail:", e.detail);   // SSE payload
			    embeddedservice_bootstrap.utilAPI.sendTextMessage("Text")
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
			        try { sessionStorage.removeItem(KEY); } catch (err) {}
			    })
			);
			embeddedservice_bootstrap.init(
				'00DgL000000YRFe',
				'Enhanced_Chat',
				'https://infallibletechieagentforce-dev-ed.develop.my.site.com/ESWEnhancedChat1787594397393',
				{
					scrt2URL: 'https://infallibletechieagentforce-dev-ed.develop.my.salesforce-scrt.com'
				}
			);
		} catch (err) {
			console.error('Error loading Embedded Messaging: ', err);
		}
	};
</script>
<script type='text/javascript' src='https://infallibletechieagentforce-dev-ed.develop.my.site.com/ESWEnhancedChat1787594397393/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>
</html>
