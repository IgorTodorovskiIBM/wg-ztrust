# ZTRUST keysigning at IBM TechXchange 2026

2:50 – 3:00 PM

Full Open Mainframe Project schedule: [Open Mainframe Project Pre-Conference Day 2026](https://openmainframeproject.org/event/join-us-for-open-mainframe-project-pre-conference-day-2026/)

The ZTRUST Working Group maintains a web of trust in the form of signed keys by members of the IBM Z community. In order to do this, members of the community must meet in person, confirm IDs, and sign each other's keys.

If you’re reading this and maintain a GPG or PGP that you wish to have signed, or would just like to learn more about the group and process, that's you!

## Instructions for Participating

### Share your key

At the very least: Upload your key to a keyserver, so it can be publicly referenced and retrieved by participants.

Preferred: Print out copies of your fingerprint to give out at meeting by using the following command to generate your fingerprint:

`gpg --list-secret-keys --fingerprint`

It should look something like this:

```
sec   rsa4096 2011-05-17 [SC]
      F1A1 2FEF 82A5 666C F9A4  A748 2FC7 6319 BC23 49FC
uid           [ultimate] Elizabeth Krumbach Joseph <lyz@princessleia.com>
ssb   rsa4096 2011-05-17 [E]
```

### At the event

Confirm your key on the keyserver or swap physical, printed fingerprints with other attendees

Everyone compares the name on the key with a physical ID (passport or other government-issued identification, such as a drivers license)

### At home

1. Retrieve the key(s) you wish to sign from keyservers, or [ZTRUST signing repository](https://github.com/openmainframeproject/wg-ztrust/tree/main/pgp/signing)

2. Sign keys by running: `gpg --sign-key FINGERPRINT`

Where "FINGERPRINT" is the fingerprint of the key you retrieved and are signing.

Compare all of the information displayed to the information you confirmed in-person, only sign the key if it matches exactly.

3. Send signed keys back to their owner.

For example: `gpg --armor --output owners-key.signed-by.my-key.asc --export FINGERPRINT`

And email that owners-key.signed-by.my-key.asc file to the owner.
