#Ruby Sinch Auth Gem for the Javascript SDK

You can use the gem `sinch_auth` to generate a user ticket that authenticates users through the Sinch Javascript SDK. First, install the gem:

    $ gem install sinch_auth
    
To use:

    sinchAuth = SinchAuth.new
    ticket = sinchAuth.get_auth_ticket(username, expires_in, key, secret)
    
Where username is a string that uniquely identifies the current user, expires_in is the number of seconds the ticket expires in, and key and secret are your app key and secret from the Sinch dashboard.

If you do not yet have a key and secret, sign up for a free Sinch developer account at [www.sinch.com/signup](https://www.sinch.com/signup). Once logged in, you will see a button to create a new app. This generates a key and secret for you.

##Use the Ticket

In the view where you want to use the Sinch client, you will create a new Sinch client and start it with the ticket you just generated. Make sure to use the same app key that you used to generate the ticket.

    <script>
      sinchClient = new SinchClient({
        applicationKey: "your_app_key",
        capabilities: {messaging: true, calling: true},
        startActiveConnection: true,
        onLogMessage: function(message) {
          console.log(message.message);
        },
      });

      sinchClient.start({"userTicket":ticket});
    </script>
    
Once the client is started, you can use it to make browser-browser phone calls, browser-phone calls, and send web-web instant messages. Follow the tutorials below to build these features:

- [Browser-browser calling](https://www.sinch.com/tutorials/using-sinch-js-sdk-make-voice-calls/)
- [Browser-phone calling](https://www.sinch.com/tutorials/turn-browser-phone-js-sdk/)
- [Instant messaging](https://www.sinch.com/tutorials/build-instant-messaging-app-sinch-javascript/)
