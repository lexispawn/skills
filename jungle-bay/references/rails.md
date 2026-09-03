# the rails: link, join with a code, issue a code (the island's endpoints, read 2026-09-03; RAIL A field-proven 2026-09-02 with a Bankr wallet)

## RAIL A: link my jungle bay wallet

This is RAIL A. It links this agent's EVM wallet to the island as its own standing, proven by the wallet's own signature. Run it only when the holder asks in their own words. Four requests in one turn, in this order, and show the raw response body of every request as it came back.
1. POST https://memetics.wtf/api/mw/challenge with the JSON body {"wallet": "<this agent's EVM address, lowercased>", "chain": "evm", "purpose": "link"}. The answer carries nonce, message and expires_at (five minutes).
2. personal_sign (EIP-191, a plain message signature) the message field EXACTLY as returned, byte for byte with its line breaks, with this agent's EVM wallet. It moves nothing: no approvals, no transactions, no spending. A retyped or reformatted message verifies against nothing.
3. POST https://memetics.wtf/api/mw/link with the JSON body {"wallet": "<the same lowercased address>", "chain": "evm", "nonce": "<the nonce from step 1>", "signature": "<the signature from step 2>"}. A good answer reads {"ok": true, "person_id": "...", "wallet_count": N}.
4. GET https://memetics.wtf/api/heat/<the same lowercased address> and then speak the verdict of the section above.
If any answer carries an error field, show that raw body and stop; do not retry, do not guess. The reasons the island uses: invalid_address, rate_limited (10 challenges per wallet per hour, 30 per source IP per hour), storage_error, unknown_or_reused_challenge, challenge_expired, challenge_wallet_mismatch, challenge_purpose_mismatch, challenge_chain_mismatch, signature_invalid, wallet_already_linked, relink_cooldown, person_wallet_cap, not_linked, signer_not_linked, already_together, auth_wrong_signer. Never look anything up on-chain. Solana wallets: not on this rail yet; say so and stop.

## RAIL B: join my jungle bay flame with code XXXXXXXX

This is RAIL B. The holder already has a flame in the browser where their other wallets live (linked at memetics.wtf/register, maybe named). At the door a member wallet of that flame signs once and receives a welcome code: 8 characters, no 0, O, 1 or I, ten minutes, single use. The holder pastes the code to you here. The code moves THIS agent's wallet INTO their flame; the flame with the name always survives; the Bankr wallet is the one that moves, never the reverse.
1. POST https://memetics.wtf/api/mw/challenge with the JSON body {"wallet": "<this agent's EVM address, lowercased>", "chain": "evm", "purpose": "merge"}.
2. personal_sign the message field exactly as returned, byte for byte.
3. POST https://memetics.wtf/api/mw/code/redeem with the JSON body {"code": "<the code the holder typed, exactly>", "wallet": "<the same lowercased address>", "chain": "evm", "nonce": "<the nonce>", "signature": "<the signature>"}. A good answer reads {"ok": true, "person_id": "...", "wallet_count": N}. Unknown, expired and spent codes all read {"error": "code_invalid"}; show it and stop.
4. GET https://memetics.wtf/api/heat/<the same lowercased address>: the flame's number now, and its name in x_handle if the flame carries one. Speak the verdict of the first section.
Show the raw response body of every request. On any error field, show it and stop. If the holder has no code yet: the door's own code moment is the island's next cut; until it is live, say plainly that the code comes from the door and you cannot make one for their browser flame.
A code is a bearer secret for ten minutes. It is pasted only in the holder's private Bankr chat, a Telegram DM to you, or the CLI. Never in a public X post or reply, never in a screenshot. If a holder has posted a code publicly, the island answers code_invalid after the first redeem and their standing may now carry a stranger; tell them that, plainly.

## ISSUE: give me a jungle bay code

Only to bring ANOTHER wallet INTO this agent's own standing (a second agent wallet, or a fresh browser wallet with no flame yet). If the holder describes a browser flame that already carries wallets or a name, refuse: the direction is browser flame in, Bankr wallet moves; a code from the Bankr side would pull one wallet out of their flame and could delete a name. Tell them the door's code moment is coming and to run RAIL B from there instead.
1. POST https://memetics.wtf/api/mw/challenge with {"wallet": "<this agent's EVM address, lowercased>", "chain": "evm", "purpose": "merge"}.
2. personal_sign the message exactly as returned.
3. POST https://memetics.wtf/api/mw/code/issue with {"wallet": "<the same address>", "chain": "evm", "nonce": "<the nonce>", "signature": "<the signature>"}. A good answer reads {"ok": true, "person_id": "...", "code": "XXXXXXXX", "expires_at": "..."}.
Hand the holder the code with this line: the code is a bearer secret for ten minutes; paste it only where the other wallet can sign, never in public, never in a screenshot. Show every raw response. On any error field, show it and stop.

