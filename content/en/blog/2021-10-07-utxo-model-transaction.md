---
title: UTXO Model Transaction
date: 2021-10-07T13:53:49.094Z
author: Ergo Foundation
authorPhoto: /img/uploads/1762.png
blogPhoto: /img/uploads/photo_2021-10-07_16-52-48.jpg
tags:
  - Building Ergo
---
<!--StartFragment-->

As the Ergo ecosystem grows, our community can now enjoy the functions for several of our key dApps. Ergo has a stablecoin protocol where users can mint SigUSD and SigRSV tokens. Ergo Auction House offers the ability to mint NFTs and ErgoDEX (Beta) allows you to swap tokens and provide liquidity. These are the very first, unique and complex DeFi dApps on the UTXO model - a model that Bitcoin pioneered. It has often been debated whether the UTXO model can express rich smart contracts, much like the Accounts model. That is why Ergo Platform built the ErgoScript language from scratch in an effort to progress on Bitcoin’s legacy.



*For an in-depth comparison about UTXO and Accounts models, please read our previous blog post:* [Ergo: Advancing on Bitcoin](https://ergoplatform.org/en/blog/2021-08-17-ergo-advancing-on-bitcoin/)



As an Ergonaut, you may have experienced some confusion if you have checked the explorer to view your transaction details. The UTXO model is essentially different from the Accounts model via the use of “boxes'' for data-keeping. In the Accounts model, there is a single account where you receive your coins. In the UTXO model however, every tx (transaction) creates a new box and your balance is the sum of all the boxes linked to your addresses.



To be clear, your Yoroi private key can consist of more than one box in a single address to hold your coins.

![](https://lh6.googleusercontent.com/qxEWrauKaD8yEXAjwXFzlikSNAXFeAxSPwuxUolS410Xf5HgOzJh_1vCL6YOfFfOyWnBhxLVIWZ0scz4BbIF9w4Tm_9aywTKo3EIrvG0zSPhCIPvLoyrlwgvZCHWHqEfXZb43klV=s0)



As you generate a new address, you will create a secondary box to hold your coins. After it is created, you can send funds to this new address and your funds will be seen as one with your private key. You can create an infinite number of new boxes to hold your coins. As such, every receiving and spending action will also create an additional unique box.



This feature can create misconceptions by the user at first glance. When you make a transaction, the network scans your “boxes” to verify if you have your tokens and then initiates the transaction. 



Things get complex after this point because you can not guess which boxes are going to be spent. Imagine you have three different receiving addresses. You received a couple of coins in each of them and you want to spend some of your coins. In a Yoroi wallet, you can hold any Ergo native coins such as SigRSV or SigUSD. When you initiate a transaction that accesses the boxes of these coins, you will see that they are taken away and then redeposited. Recently, an Ergonaut raised the following [question](https://www.reddit.com/r/ergonauts/comments/prn7x3/comment/hdty87z/?utm_source=share&utm_medium=web2x&context=3): 



“I just created a Yoroi Nightly wallet. I transferred 31 Erg from my main Yoroi wallet to the Yoroi Nightly wallet. The transaction shows 31 Erg plus a small fee, 0.0011. But it also says +92,000 SigRSV. My balance shows no change in SigRSV. What is the meaning of the +92,000 SigRSV in the transaction?”



Let’s take a look of the details of this particular [transaction](https://explorer.ergoplatform.com/en/transactions/143f5ba0ee1482d332d1020c94f261399f220c7f4523063ade8290c478acbd29):



![](https://lh5.googleusercontent.com/HOFhlYx5l3wvUzET-wa9E4dhU8az4srODa_4n09qZm3y-gWQz1L9Obw5qobgQM5Bthokn8SYMuO13cLDNEW5fqbboSj3qAwf2rzYH1rHkyvaoDsIMSDa3zwJU31s5XLEc_n5VbZ0=s0)



To make a transaction of 31 ERG,  the wallet selected three of the boxes with ERG:

* A box containing 0.029595 ERG that was received on 07/19/21
* A second box containing 19.76 ERG that was received on 07/19/21
* A third box containing 208.26 ERG that was received on 06/09/21 



On the left section of the image above, you will see approximately 228 ERG taken while on the right section you will see 31 ERG sent and 197 ERG redeposited to your wallet.



So your wallet used three of your boxes to spend the desired amount. This action includes all the assets in that box to the transaction. 



After the desired amount is spent, your funds are simply refunded to your address in a newly created UTXO box or boxes. Spending any coin in a box therefore means spending the whole box and creating a new UTXO box, which is why you see your tokens are taken away and then redeposited.



The selection of which boxes to spend is a secret of the wallet’s random selection strategy. Whatever coins are in the selected boxes, be it SigRSV, SigUSD or NFT, will be displayed as in the example. 



### To sum up: 



The Accounts model contains a single box and this box is not spent. It remains the same so non-related coins will remain unaffected.



The UTXO model on the other hand contains a set of boxes that represents the total amount of the users balance and the unspent transaction output has to change with each spending transaction.  



You may see a long list of tokens when swapping just 5 SigRSV as below:![](https://lh6.googleusercontent.com/wK-uprlqrj6wKt74AODkxBt6xR5Dey_qGB4kclXm5OuhWz2nfIuBTZm412oFA1h0OHXRi_oGcx6y7jR6A6kRcgpAUU7vSaQrfAMY6lKzdzy8THl2Hh2uEMzHjs5M5Sdlly6DO8f4=s0)



This is just how UTXO model Transaction works - its storage is different from the Accounts model. In the UTXO model, coins will be stored in one-use UTXO boxes and not in long-living accounts.



<!--EndFragment-->