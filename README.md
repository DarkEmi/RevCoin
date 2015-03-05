# RevCoin
RevCoin : The secure digital currency

Reversible transactions in digital currencies
revcoin whitepaper

“Bitcoin won’t be the dominant system. When you talk about a domestic economy, you must have the idea of attributed transactions, where if you sent it to the wrong person you could actually get the transaction reversed.” 
Bill Gates
Abstract

Security in the digital currencies is one of the most important features. Physical wallet and multi signature allow for increased security, but there is still a lot of use case where hacks can happen and are not prevented by one of those two features. We will show that those hard case for security can be solved using chargeback. We propose a new protocol which includes a simple and efficient way to add chargeback into bitcoin transactions. This protocol can either be added on top of bitcoin, or be implemented as a new coin altogether.


Motivation behind TrustCoin


Bitcoin IS incredible

Bitcoin is incredible. It has a set of unique properties that no currency ever had before it. 

It has both the same feature than existing money, and an additional set of features that makes it so much better than any money that ever existed :

It has no physical existence, it can exist solely in the “numerical world”. This makes Bitcoin extremely easy and cheap to store, send, and secure.

Bitcoin is an insane store of value. It is even a better store of value than gold and precious metals because the amount of gold available is nearly infinite and more can always be mined especially if the price increase. It is, in the history of currency and of goods altogether, the first truly scarce resource with a fixed amount. Bitcoin is in this regard, comparable to the art market, where one piece of art is in unique supply.



False issue with bitcoin

One recurring concern bitcoins users express is the lack of anonymity from bitcoin. Some argue, that since the blockchain is essentially recording everything, that everything people do is basically transparent and that its impossible to launder funds or stay anonymous.

We object two criticism to this view :
One empirical : Despite the fact that everything in bitcoin, thief and hacker have never been identified and found following a blockchain analysis.
One theoretical : It is pretty easy to construct system or use bitcoin in a way that it is in fact anonymous.

It is however true that with a “naive” bitcoin usage, it is possible to not be anonymous. But basic things like not reusing address and mixing algorithms allow to be for all practical purposes, anonymous.

Most of the time, the issue of being identified are not linked to bitcoin usage but rather to service usage (for example using a service that requires identification with governments issued id and reusing sessions in browser). Even if someone use bitcoin without any taking any anonymization precaution, by simply ensuring that he uses services that don't know his personal information, he can stay effectively anonymous.

Several coins have been developed that aims to tackle this issue, we can cite Darkcoin (which introduced a in-protocol mechanism similar to coinjoin) and Monero (which has even greater anonymity feature).

However we feel that while these solutions are good, they tackle an almost non existent problem.

The real issue with the bitcoin protocol
“With great power comes great responsibility.”

The features of bitcoin are both incredible and powerful, but lets make some real world anology to see what the issue. So imagine the real world gold having a few of the bitcoins property. This would mean that if a tie

This problem of necessary increased security cost 

Possibles solutions

We thought of two main approach to implement chargebacks :

With a “god” : One or several “super user” could be choosen and be able to modify and revert transactions. This is the “paypal” model. Obviously since this solution is then completly centralised, it loose a lot of the interest of bitcoin. A better way to implement this would be to have a “elected god”, for example, one address could be “elected” by miner consensus as a “bitcoin police”l and have a right to modify, change and create new transactions freely, even without owning private key. 
This solution can pose several problems, one the main being that bitcoin is all about individual user freedom and this solution goes away from this philosophy. Indeed, if for example the majority of the network agree to “steal” from someone, this solution would essentially allow it. This would be democratic in the traditional sense of the term, as it would be possible to “force” tax or fees other all the users, despite the majority being potentially morally wrong.

With a “chargeback” : Chargeback allow for much greater levels of security. However, chargeback transactions may appear to destroy several of bitcoin philosophical aspect and hence are very often decried on bitcoin forums. For example, some might get weary that all transactions are not final and might be canceled, that all coins would not be ultimately fungible (since some would be canceled and some others none), and finally, that it would involved third parties for mediation of chargebacks.

My solution would :
Allow for freedom of use by users. User are free to keep using bitcoin “as is”, without any chargeback mechanism and with instantaneous transactions. 
Merchants can still accept payments with 100% certainty. As with all bitcoin related thing, a protocol based chargeback mechanism will tell exactly at what point a transaction is reversible and at what point it would not be. Hence, there is no added risk on the merchant side, except if he willingly choose to have an added risk.

I would argue that my solution is essentially a “cold storage” solution. For everyday purchase, it makes little sense to wait for transactions. However, its pretty rare that one bank, office, or indivudual needs to sends the integrity of its networth in a single instantaneous transactions.

It makes sense that sending a million dollar would rather be secure and reversible, rather than instantaneous.

Specific use case

We will compare specific 

Case 1 : 

The user is forced with violence to reveal his private key.








Case physical wallet (trezor, ledger….)

Physical wallets solution offer absolutely no protection against this. When threatened or forced, the user has absolutely no solution 

Use case 2 - The rogue employee

At an exchange or any bitcoin company, one of the critical employee is dishonest and will try to steal bitcoin.

Without any particular security, he can easily make it seems like an outside hack while pocketing the coins from the inside.

Probabilistic evaluation of risk

This is a little “unorthodox”

There is 3 distinct probability :

Probability of losing the private key
Probability of theft

The total probability of losing the bitcoins from an account is normally the sum of (probability of losing the private key) + probability of theft.

Thus all security methods have to account for both possibility and any “traditional” bitcoin safety method must account for both method.

While using the revcoin system, the loss probability becomes (more or less) this formula :
p(loss for X) = p(keyLost) + (p(theft) * p(loss for TrustAddress))

This allow two things : 
A beginner user can focus only and exclusively on “not forgetting the key” and still be secure. Because his security effectively rely on the security of his trust
Expert users (exchanges back office, business…) can form a very strong “link of trust” where if one wants to hack one, he need to hack all the exchanges.

  
 


Technical protocol

We will use two different terms for the two distinct set of address :

Standard addresses : Those addresses work exactly the same way as they do in bitcoind.

It is possible to use revcoin exactly in the same way as you would use bitcoin, by only using standard address, and accepting only confirmed transactions.

Cancelable addresses : Those addresses are address from which all the transactions (out of the daily limit) are cancelable.

A cancelable address is created out of a normal address. Once a normal address is converted into a cancelable address, it is not possible to turn it back again into a normal address.

The only time where you can 



A cancelable address

We propose a set of commands which can be either added on top of bitcoin, or implemented in a new coin (InvCoin) to add transaction cancellation features.

New commands

Command 1  -

createtrustaddress(string privateKey, string publicKey trustedAddresss, int NumberOfBlockBeforeCancellation, float DailyLimit)  

Command 2 -

canceltransaction(canceled_txid, privatekey)

If the transaction (txid) has not yet been. This create a new transaction on top of the previous which would essentially look like this :

It groups all the ouptput from (canceled_txid) and group them as input for a new transaction, which send the fund back to (pubAddr)

disableaddress (pubkey, privatekey)

Essentially, this is the command you will call once your address has been compromised and a thief has started to make new transactions with your private key. It essentially tell the network that the compromised address should not be used anymore.

This is the “cancel” command. This command will do both :
Cancel all the transactions from address (pubAddr) which are still time locked
Create a new transaction which will send all the bitcoins from (pubAddr) to (TrustAddr), by including all the unspent transactions to (pubAddr)
Any ulterior deposit into (pubAddr) should be considered directly “as if” deposited into (trustAddr). This remove the need to call wipeaddress several time.

Modified commands (this list is not exhaustive)

getbalance(address)

getbalance will display only the amount of bitcoin which are already in an address. An extra option should be added to be able to see balance of coins which are incoming (similar as running getbalance with 0 confirmation)

It is important to understand that TrustCoin is meant 

The “miner Attack” 

There is a possible exploitation to the mechanism of cancel transaction. Since the thief can own the private key, he can cancel the transaction himself, making the miner fee as big as he wish. As such, we should have a mechanism for determining the fee on a “cancel transaction” .

The mechanism should be such that if a transaction is sent back to another address, it is always included in the blockchain (we would not want a canceled theft to not be included in the blockchain)

I propose that the miner fee should be 4 times bigger than a standard fee, hence :
Its not possible to use someone else private key to send funds to miners


Conclusion

We proposed a solution for increasing bitcoin security which can be either implemented on top of bitcoin or as a new currency entirely. We showed that it increased security compared to all existing bitcoin security feature, in several use case.
We see the potential for the bitcoin technology, but due to experimental and instability reason, we suggest to try this idea on top of a new coin protocol.

We are looking for partners in this venture. We are looking both for at least a bitcoin / altcoin developer. Someone able to dig into the source code and add features. We are also looking for investors for creating this alt coin.
We have a sound and very simple business model. Contact me at support@btcoracle.com for 
more information or Emilien.Dutang on skype.
Thanks to Adrien Lafuma, my partner at btcoracle.com and masterxchange.com, for helping me with this idea.


