<html>
	<script type='text/javascript'>
	function initEmbeddedMessaging() {
		try {
			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

            window.addEventListener("message", (e) => {
			    if (e.data && e.data.source === "prechat") {
			        console.log("from:", e.origin, "value:", e.data.value);
			        // e.g. window.userPrompt = e.data.value["How can I help you?"];
			    }
			});
			
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
