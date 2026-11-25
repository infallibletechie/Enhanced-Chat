<html>
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
