# A PGP Business Card

The purpose of exchanging and cross-signing PGP keys is to confirm
ownership of the keys. PGP keys are used for cryptographic signing of
code and other computer files as well as for delivering private email.

Consider carrying a business card or similar printed media
containing your PGP key fingerprint. When you encounter PGP users
at conferences (or in any public venue), give them your card.
This is sometimes called an "opportunistic key exchange"
and is less tedious than a formal key signing party.
In-person exchange of key fingerprints is the most secure way
to confirm true key ownership.

It is NOT discourteous to also present, or to ask for, government-issued
or similarly strong formal identity, even if you and the other person
know each other well. Don't be afraid to ask to see their driver's license.

Remember that PGP is not just for email, but also for
cryptographically signing files or any similar electronic media.
Cross-signed PGP keys are signifantly more trustworty than unsigned keys.

## Anything on Paper

Paper is highly tamper evident. It may seem low tech,
but that does not mean it is impractical. Quite the opposite.
It is actually less vulnerable to tampering by an attacker
even than removable electronic media that you have aggressively kept safe.

Have multiple copies of your fingerprint media so that you can give
the paper or card to any number of other people.

## The "Card"

Your "card" should perhaps *not* have your public key itself
so that the recipient will be required to use more than one channel.
It could be an actual business card in the traditional sense or even
just a slip of paper. It should *not* be an electronic business card
because electronic delivery can be intercepted, tampered with, or compromised.

Consider making a QR code of your PGP key fingerprint.
(Not of the key itself.) That may facilitate reading the fingerprint
for some recipients, and yet it retains the tamper-evident attribute.

## Also on the Network

The whole point of a public key is ... well ... that it be distributed
*publicly*. There *are* privacy concerns, so you might not want to upload
your public key to the key servers, but you *should* make it available
electronically. This provides a secondary channel for people with whom
you share your key to acquire and verify it. You can also email your
public key to peers; they can confirm your key with the fingerprint.

You might consider putting your public PGP key on a web site that you
control. If privacy is an issue, such a web site or page should be away
from the prying eyes of the robots. The nature of public key cryptography
means that you are *not* at risk of someone hijacking your *private* key.
You might even want to put your public key on social media.

This does not mean that you should upload the public keys of others.
Don't. Leave the uploading of public keys to the owners of those keys.

## Accepting Their Key

When you get a card or slip of paper with someone's PGP key fingerprint,
do not accept and sign their key immediately. Wait until you are in a
private location with your own laptop or other personal computer.
When you have full control, confirm that the fingerprint of their
PGP public key matches the fingerprint that you received in person.

It is best if you can retrieve the other person's public key via some
channel other than the business card. (Hopefully they will have published
their key somewhere that you can get it, much like *you* are urged to do
in previous paragraphs.) Email is a good choice for this "other channel"
given that you obtained the fingerprint in person (and on paper).

Using GPGv2, you will need to `--import` the other person's public key
before you can display the `--fingerprint`. This is normal. If the fingerprint
does not match, then simply delete the recently-added (but wrong) public key.

## Signing Their Key

Unless requested otherwise, you should sign the other person's public
key with your private key. Once their key is signed with *your* key,
you should `--export` their public key and deliver it back to the owner.
When they `--import` their own key (that you have exported after signing)
it will now have your signature (that they just imported). In the future,
others using their public key will see your signature and have that much
more assurance of their key's veracity.

The more signatures on your public key (or on theirs), the stronger grows
the web of trust. This is true for you and for the person with whom
you exchange fingerprints.

If you are confident about the fingerprint hand-off, use the
`--default-cert-level 3` option when signing, providing stronger assurance
to other consumers of the trust web.

Email the signed key to the owner, but do not upload keys of others
to the publicly-facing key servers unless asked to do so by the key owner.

## Commands to Issue

To display your public key fingerprint for printing:

    gpg --fingerprint your-key-ID

The fingerprint itself is simply a hash of the key material,
but is sufficiently unique for strong assurance of trustworthiness,
much stronger than the 16-hex-digit "key ID" used for convenience.

To share your public key:

    gpg --armor --export your-key-ID > your-key-ID.asc

To import the public key of another person, get their public key
into a file and then:

    gpg --import their-public-key

 ... which may or may not have a `.asc` filename extension.

Note: When importing older PGP keys, you may need to soften the default
key and signature requirements:

    gpg --allow-weak-key-signatures --import their-public-key

Confirm that the fingerprint of this newly imported key matches
the fingerprint shown on *their* business card. If it does not match,
then delete it from your public keyring and DO NOT SIGN IT: stop here.

But if the fingerprint DOES match, then ...

To sign someone else's public key (after importing it to your keyring):

    gpg --default-cert-level 3 --sign-key their-public-key

To export the newly-signed public key of another so that you can
send it back to them (now with your signature):

    gpg --armor --export their-key-ID > their-key-ID.asc

You can attach the file to email and send it to the owner.
If your email client supports PGP, you should import their public key
to your email client and encrypt the message using their public key.
It's an extra safety measure: only the owner can read the email
with the attachment (even though the risk from public key capture is low).


