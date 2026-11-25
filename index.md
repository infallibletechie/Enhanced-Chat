<script type='text/javascript'>
	function initEmbeddedMessaging() {
		try {
			embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

            /* START:: Conversation Routed Listener */
            window.addEventListener("onEmbeddedMessagingPreChatSubmitted", (event) => {
                console.log( "Conversation Routed" );
                console.log( "Event detail: ", JSON.stringify( event.detail ) );

                /*embeddedservice_bootstrap.utilAPI.sendTextMessage('Transferrred')
                    .then(() => {
                        console.log("Message sent");
                    })
                    .catch(() => {
                        console.log("Message not sent");
                    })
                    .finally(() => {
                        console.log("Message sent - finally");
                    });*/
            });
            /* END:: Conversation Routed Listener */
			
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
