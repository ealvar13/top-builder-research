# Top Builder Round 2 Research

## Introduction

Our most requested feature for usability is the ability to send users Bitcoin rewards if they don’t have a Lightning Address. This would broaden the reach of our surveys and quizzes for site operators and likely make the tool overall more effective and popular.

We think there are a few ways to go about this:

1. **Make them a Lightning Address:** If the user doesn’t have a Lightning Address, set one up for them and email them instructions for claiming their reward.
2. **Send them an LNURLw link by email:** If the user doesn’t have a Lightning Address, email them an LNURL withdrawal code that they can use to claim their reward.
3. **At the completion of the quiz, present them an LNURLw link on screen:** If the user doesn’t have a Lightning Address, after they submit the quiz we could present them with an LNURLw link they could scan with (almost) any Bitcoin Lightning wallet.

In order to make these alternatives easy to implement by site operators, we’d like to minimize any additional configuration on their part. From the site operators' perspective, we want to make sure any solution we implement can be 100% supported by either BTCPay Server or Alby Wallet. However, we will need to assume that their site is properly configured for sending emails to users for Options 1 and 2.

Next, we’ll analyze each of the 3 alternatives in greater detail and weigh the pros and cons.

## Alternative 1: Make the User a Lightning Address
We would aim to provide a UI similar to this page: https://getalby.com/lightning-address .  Note that linking straight to this is an option for us, however it requires an invite code and is likely to discourage users from taking our quizzes.

This process is possible via [LNBits API](https://legend.lnbits.com/docs#/usermanager/Create_wallet_for_user_usermanager_api_v1_wallets_post) and also seems to be possible with the [Speed Wallet API](https://www.speed.dev/docs/receive-payments/payment-addresses/create-a-payment-address). 

The cool part about this is that a user could have their own LN wallet and address in just a couple of clicks. The downside is that LNBits wallets require the user to save the URL or lose the wallet.   Also, we’d be dependent on a third party to manage liquidity & uptime for their LNBits instance.

Pros:
- A user could have their own LN wallet and address in just a couple of clicks.

Cons:
- LNBits wallets require the user to save the URL or lose the wallet.
- Dependence on a third party to manage liquidity & uptime for their LNBits instance.

## Alternative 2: Send an LNURLw Link by Email

This would provide an easy user interface as well as a means for site operators to collect email addresses for promotions. We’ve had a suggestion by the Alby Team for a process that could make this work without the need for extra configuration by the site operator. This would involve a combination of the [LightSats API](https://lightsats.github.io/Lightsats-API-docs/#create-a-tip-tip-group) and the existing [Alby API](https://guides.getalby.com/developer-guide/v/alby-wallet-api/reference/api-reference/payments).

Alby also made us [a feature request](https://feedback.getalby.com/-request-a-feature/posts/allow-for-lnurl-withdraw-voucher-creation) to have this functionality supported natively in their API.

Pros:
- Opens our software up to a much wider userbase.
- The reward can be set to expire so that funds aren’t hanging around unclaimed.

Cons:
- We’ll need to design the UI on the backend and frontend to make these alternatives intuitive for users and site operators.
- Adds an element of complexity to the UI.

## Alternative 3: Present an LNURLw at the End of the Quiz

At the end of the quiz, we can present the user with an LNURLw code that they can use to redeem their sats with most Lightning wallets.

Pros:
- Easy to implement.

Cons:
- Presents a risk of being farmed by users for repeat rewards.
- Could reduce the usability of our plugin for certain users or groups.

## Conclusion

Weighing these alternatives, we believe the best option is to send a LNURLw link by email. 

This option offers the best trade-off between broadening the user base, keeping the software resilient, reducing dependencies on third parties, and requiring little extra configuration from the site operator. We will need to carefully design the UI on the front and backend to keep the flow intuitive and simple.

Analysis of these alternatives has been a great learning experience for us, and we are looking forward to implementing these improvements in future versions of the Bitcoin Mastermind plugin.

