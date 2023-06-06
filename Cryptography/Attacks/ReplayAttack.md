## A replay attack occurs when a cybercriminal eavesdrops on a secure network communication,intercepts it, and then frudulently delays or resends it to misdirect the receiver into doing what the hacker wants. The added danger of replay attacks is that a hacker doesn't even need advanced skills to decrypt a message after capturing it from the network. The attack could be successful simply by resending the whole thing.

# How it works

## Consider this real-world example of an attack. A staff member at a company asks for a financial transfer by sending an encrypted message to the company's financial administractor. An attacker eavesdrops on this message, campures it, and is now ina position to resend it. Because its an authentic message that has simply been resen, the message is already correctly encrypted and looks legitimate to the financial administrator.

## In this scenario, the financial administrator is likely to respons to this new request unless he or she has a good reason to be suspicious. That response could include sending a large sum of money to the attacker's bank account.

# Stopping a Replay Attack

# Preventing such an attack is all about having the right method of encryption. Encrypted messages carry "keys" withing them, and when they're decoded at the end of the transmission, they open the message. In a replay attack, it doesn't matter if the attacker who intercepted the original message can read or decipher the key. All he or she has to do is capture and resend the entire thing - message and key -- together

## To counter this possibility, both sender and receiver should establish a completely random session key, which is a type of code that is only valid for one transaction and con't be used again.

## Another preventative measure for this type of attack is using timestamps on all messages. This prevents hackers from resending messages send longer ago then a certain length of time, thus reducing the window of opportunity for an attacker to eavesdrop, siphon off the message, and resend it.

## Another method to avoid becoming a victim is to have a password for each transaction that's only used once and discarded. That ensures that even if the message is recorded and resent by an attacker, the encryption code has expired and no longer works.

