<html>
	<script type='text/javascript'>
	function initEmbeddedMessaging() {
		try {
			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

            ["onEmbeddedMessagingReady",
			 "onEmbeddedMessagingPreChatLoaded",
			 "onEmbeddedMessagingPreChatSubmitted",
			 "onEmbeddedMessagingConversationStarted"].forEach(name =>
			  window.addEventListener(name, e => console.log(name, e.detail))
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
