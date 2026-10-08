# the rails: link, join with a code, the Solana wallet by one exact send, the name code, issue a code (the island's endpoints, read 2026-10-08; RAIL A field-proven 2026-09-02 with a Bankr wallet; RAIL B order fixed 2026-09-03: link first; RAIL C, RAIL B-SOL and RAIL N added 2026-10-08, ONE ROAD)

Every rail runs only in the holder's private chat with you, a direct message, or the CLI. Show the raw response body of every request as it came back. On any error field, show it and stop, unless the rail below names that error as a continue.

## RAIL A: link my jungle bay wallet

This is RAIL A. It links this agent's EVM wallet to the island as its own standing, proven by the wallet's own signature. Four requests in one turn, in this order.
1. POST https://memetics.wtf/api/mw/challenge with the JSON body {"wallet": "<this agent's EVM address, lowercased>", "chain": "evm", "purpose": "link"}. The answer carries nonce, message and expires_at (five minutes).
2. personal_sign (EIP-191, a plain message signature) the message field EXACTLY as returned, byte for byte with its line breaks, with this agent's EVM wallet. It moves nothing: no approvals, no transactions, no spending. A retyped or reformatted message verifies against nothing.
3. POST https://memetics.wtf/api/mw/link with the JSON body {"wallet": "<the same lowercased address>", "chain": "evm", "nonce": "<the nonce from step 1>", "signature": "<the signature from step 2>"}. A good answer reads {"ok": true, "person_id": "...", "wallet_count": N}. {"error": "wallet_already_linked", "person_id": "..."} means this wallet already stands on a flame: that is linked too; continue.
4. GET https://memetics.wtf/api/heat/<the same lowercased address> and then speak the verdict (the first section of SKILL.md), unless a longer road continues below.
The reasons the island uses: invalid_address, rate_limited (ten calls per wallet per hour, a shared limit per source IP), storage_error, unknown_or_reused_challenge, challenge_expired, challenge_wallet_mismatch, challenge_purpose_mismatch, challenge_chain_mismatch, wrong_signer, recover_failed, signature_not_hex_wrong_lane, wallet_already_linked, relink_cooldown, person_wallet_cap, not_linked, signer_not_linked, already_together, auth_wrong_signer, authorizing_wallet_not_linked. Never look anything up on chain on this rail.

## RAIL B: join my jungle bay flame with code XXXXXXXX

This is RAIL B. The holder already has a flame in the browser where their other wallets live (linked at memetics.wtf/register, maybe named). At the door a member wallet of that flame signs once and receives a welcome code: 8 characters, no 0, O, 1 or I, ten minutes, single use. The holder pastes the code to you here. The code moves THIS agent's EVM wallet INTO their flame; the flame with the name always survives; the Bankr wallet is the one that moves, never the reverse.
0. RAIL A first: this agent's EVM wallet must have a standing before it can move. When THE ROAD already ran RAIL A this turn, do not run it again (every call counts against the wallet's ten per hour). {"ok": true, ...} or {"error": "wallet_already_linked"} both mean linked: continue. Any other error: show it and stop here, before the code is spent (the island takes the code before it checks the wallet, so a redeem from an unlinked wallet reads not_linked and burns the code).
1. POST https://memetics.wtf/api/mw/challenge with the JSON body {"wallet": "<this agent's EVM address, lowercased>", "chain": "evm", "purpose": "merge"}.
2. personal_sign the message field exactly as returned, byte for byte.
3. POST https://memetics.wtf/api/mw/code/redeem with the JSON body {"code": "<the code the holder typed, exactly>", "wallet": "<the same lowercased address>", "chain": "evm", "nonce": "<the nonce>", "signature": "<the signature>"}. A good answer reads {"ok": true, "person_id": "...", "wallet_count": N}. {"error": "already_together"} means this wallet already stands on that flame: continue. Unknown, expired and spent codes all read {"error": "code_invalid"}; say so and stop.
4. Continue with RAIL C (the Solana wallet) and RAIL N (the name), then speak once.
A code is a bearer secret for ten minutes. It is pasted only in the holder's private Bankr chat, a Telegram DM to you, or the CLI. Never in a public X post or reply, never in a screenshot. If a holder has posted a code publicly, the island answers code_invalid after the first redeem and their standing may now carry a stranger; tell them that, plainly.

## RAIL C: this agent's Solana wallet onto the same flame, by one exact send

This is RAIL C. Bankr signs plain messages only with its EVM wallet, so the Solana wallet proves itself the one way a wallet can without a signed message: by one exact send its own key signs. The island names the amount and the destination (the wallet itself: nothing leaves the holder but the network fee), finds the send on the chain, checks the wallet signed it, and joins the wallet onto the flame this agent's EVM wallet rides. The EVM wallet vouches with one signed message of its own. Runs after RAIL A (and after RAIL B when there was a code), never before.
0. GET https://memetics.wtf/api/heat/<this agent's Solana address> and GET https://memetics.wtf/api/heat/<this agent's EVM address, lowercased>. When both answer the same degrees, the same tier and the same x_handle (a string or null on both), and the EVM wallet is linked, the two already read as one flame: skip RAIL C, nothing to send. Otherwise:
1. POST https://memetics.wtf/api/mw/challenge with the JSON body {"wallet": "<this agent's Solana address, exact base58>", "chain": "svm", "purpose": "link", "proof": "transfer"}. The answer carries nonce, message, expires_at (fifteen minutes), "proof": "transfer", "send": {"sol": "<the exact amount as text>", "lamports": N, "from": "<the wallet>", "to": "<the destination>"} and words.
2. Make that one send, exactly: send <send.sol> SOL from this agent's Solana wallet to <send.to> on Solana. Exactly the amount in send.sol, never rounded, never a different token, never a different address (send.to is this agent's own Solana address unless the island names another). Wait for the send to confirm. If the send is refused (a spend limit, a recipient rule, a paused wallet, no SOL for the fee), show the refusal and stop; nothing was linked.
3. POST https://memetics.wtf/api/mw/challenge with {"wallet": "<this agent's EVM address, lowercased>", "chain": "evm", "purpose": "link"}; personal_sign the message exactly as returned. This is the vouch: a wallet already on the flame says the Solana wallet belongs beside it.
4. POST https://memetics.wtf/api/mw/link with the JSON body {"wallet": "<the Solana address>", "chain": "svm", "nonce": "<the nonce from step 1>", "signature": "<the send's own transaction signature, the base58 id your send answered with; "transfer" if you do not have it>", "auth": {"wallet": "<this agent's EVM address, lowercased>", "chain": "evm", "nonce": "<the nonce from step 3>", "signature": "<the signature from step 3>"}}. No person_id: the island joins the Solana wallet onto the vouching wallet's own flame. With the transaction signature the island reads that one transaction; without it the island searches the wallet's recent sends.
   {"ok": true, "person_id": "...", "wallet_count": N}: both wallets stand together. Done.
   {"error": "send_not_found"}: the send has not reached the island's view of the chain yet. Nothing was spent: neither nonce nor the vouch. Wait fifteen seconds and repeat step 4 with the same body (the same two nonces and the same vouch signature), up to four times. Still send_not_found after that: say the send did not land where the island looks, show the send's result, and stop.
   {"error": "wallet_already_linked", "person_id": "...", "together": true}: the Solana wallet already stands on this flame. Done.
   {"error": "wallet_already_linked", "person_id": "...", "together": false}: the Solana wallet stands on another flame. Say so; one more code from memetics.wtf/register moves it (RAIL B-SOL).
   {"error": "authorizing_wallet_not_linked"}: the EVM wallet is on no flame; run RAIL A and start RAIL C again.
   Any other error (send_not_in_tx, tx_failed, send_too_old, transfer_reused, tx_signature_invalid, wallet_not_a_signer, tx_bytes_missing, chain_read_failed, transfer_proof_mismatch, challenge_expired): show it and stop. A fresh challenge names a fresh amount; the old send is not reused.
Never send any amount but the exact one named, to any address but the one named. Never send twice for one challenge. The send is the proof; a transaction signature never needs to travel through the holder.

## RAIL B-SOL: move my solana wallet onto my flame with code XXXXXXXX

This agent's Solana wallet already stands on another flame (RAIL C answered together false) and the holder brought one more code from the flame they keep. The code moves the Solana wallet INTO that flame; the proof is one exact send, as in RAIL C.
1. POST https://memetics.wtf/api/mw/challenge with {"wallet": "<this agent's Solana address, exact>", "chain": "svm", "purpose": "merge", "proof": "transfer"}. Read send.sol and send.to from the answer.
2. Make that one send, exactly, and wait for it to confirm (RAIL C step 2).
3. POST https://memetics.wtf/api/mw/code/redeem with {"code": "<the code, exactly>", "wallet": "<the Solana address>", "chain": "svm", "nonce": "<the nonce>", "signature": "<the send's own transaction signature; "transfer" if you do not have it>"}. {"ok": true, ...}: moved. {"error": "send_not_found"}: the island looks for the send before it touches the code, so nothing was spent; wait fifteen seconds and repeat step 3 with the same body, up to four times. {"error": "code_invalid"}: spent or expired; say so and stop. Any other error: show it and stop.
4. GET https://memetics.wtf/api/heat/<this agent's EVM address, lowercased> and speak the verdict.

## RAIL N: the name, by a code the wallet signs for

The name needs two proofs: a wallet signature (this agent's EVM wallet gives it here) and an X sign-in (only the holder can give it, in a browser). The island joins the two on its own box: one signature here makes a six-character code that lasts fifteen minutes; the holder opens memetics.wtf/name in any browser where they use X, signs in, types the code, and the name is on. You never sign in as anyone and never type a handle.
0. This agent's EVM wallet must be linked (RAIL A). Its flame must carry no name yet, or the holder asked for a new name (rename).
1. POST https://memetics.wtf/api/mw/challenge with {"wallet": "<this agent's EVM address, lowercased>", "chain": "evm", "purpose": "claim"}.
2. personal_sign the message exactly as returned.
3. POST https://memetics.wtf/api/mw/name-code with {"wallet": "<the same lowercased address>", "chain": "evm", "nonce": "<the nonce>", "signature": "<the signature>"}; for a new name on a flame that already carries one, add "rename": true. A good answer reads {"ok": true, "code": "ABC234", "expires_at": "...", "ttl_seconds": 900, "length": 6}.
   {"error": "person_already_claimed"}: the flame already carries a name and this was not a rename; say the name from the heat read and that "changed my name on X" is the road to a new one. {"error": "not_linked"}: run RAIL A first. Any other error: show it and stop.
4. Hand the holder the code with these three lines, in the private chat only:
   your name goes on with one X sign-in. the code: <CODE>. it lasts fifteen minutes and works once.
   open memetics.wtf/name in any browser where you use X, tap Sign in with X, type the code.
   the signature your wallet already gave puts the name on. nothing moves.
   For a rename add: sign in there as your new name; if the page shows the old one, tap Not you? Sign in with another X first.
A name code is a bearer secret for fifteen minutes: private chat, DM or CLI only, never a public post, reply or screenshot.

## ISSUE: give me a jungle bay code

Only to bring ANOTHER wallet INTO this agent's own standing (a second agent wallet, or a fresh browser wallet with no flame yet). If the holder describes a browser flame that already carries wallets or a name, refuse: the direction is browser flame in, Bankr wallets move; a code from the Bankr side would pull one wallet out of their flame and could strand a name. Tell them to tap Get a code at memetics.wtf/register and paste its line 2 here instead.
1. POST https://memetics.wtf/api/mw/challenge with {"wallet": "<this agent's EVM address, lowercased>", "chain": "evm", "purpose": "merge"}.
2. personal_sign the message exactly as returned.
3. POST https://memetics.wtf/api/mw/code/issue with {"wallet": "<the same address>", "chain": "evm", "nonce": "<the nonce>", "signature": "<the signature>"}. A good answer reads {"ok": true, "person_id": "...", "code": "XXXXXXXX", "expires_at": "..."}.
Hand the holder the code with this line: the code is a bearer secret for ten minutes; paste it only where the other wallet can sign, never in public, never in a screenshot. Show every raw response. On any error field, show it and stop.
