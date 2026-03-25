<html>
<script type='text/javascript'>
    function initEmbeddedMessaging() {
        try {
            embeddedservice_bootstrap.settings.language = 'en_US'; // For example, enter 'en' or 'en-US'

            /* START:: Conversation Routed Listener */
            window.addEventListener("onEmbeddedMessagingConversationRouted", (event) => {
                console.log( "Conversation Routed" );
                console.log( "Event detail: ", JSON.stringify( event.detail ) );
            });
            /* END:: Conversation Routed Listener */

            embeddedservice_bootstrap.init(
                '00DgL00000DFmfx',
                'Enhanced_Chat_V2',
                'https://infallibletechiechat-dev-ed.develop.my.site.com/ESWEnhancedChatV21767569974081',
                {
                    scrt2URL: 'https://infallibletechiechat-dev-ed.develop.my.salesforce-scrt.com'
                }
            );
        } catch (err) {
            console.error('Error loading Embedded Messaging: ', err);
        }
    };
</script>
<script type='text/javascript' src='https://infallibletechiechat-dev-ed.develop.my.site.com/ESWEnhancedChatV21767569974081/assets/js/bootstrap.min.js' onload='initEmbeddedMessaging()'></script>
</html>
