# Refactor blackjack rules and dealer hit condition

**Current version:** V1  
**Last updated:** 2026-04-30T00:42:04.026258+00:00  
**Last approved by:** — (_2026-04-28T02:22:45.915649+00:00_)  
**Source PR:** https://github.com/Venkata-Bhumika-Guthi/Testing/pull/13

## Current content

# PR-13: Refactor blackjack rules and dealer hit condition
## Summary uday
This pull request modifies the blackjack game logic to change the dealer's hitting condition from 17 to 18, making the dealer more aggressive.

## Why this change exists
The change aims to slightly increase the house edge, making it harder for players to win by adjusting the dealer's behavior.

## What changed (by area)
- **File Modified**: `blackjack`
  - Removed comments related to the blackjack check and double down option.
  - Updated the dealer's hitting condition from `while hand_value(dealer) < 17:` to `while hand_value(dealer) < 18:`.

## How to verify / test
To verify the changes, run the blackjack game and observe the dealer's behavior. The dealer should now hit until reaching a hand value of 18.

## Operational notes (rollout, migrations, feature flags)
**Not specified in PR materials.**

## Risks / edge cases
Changing the dealer's hitting condition may affect game balance and player experience. Testing should ensure that the new logic does not introduce unintended gameplay issues.

## Follow-ups
**Not specified in PR materials.**

## References
- PR: [https://github.com/Venkata-Bhumika-Guthi/Testing/pull/13](https://github.com/Venkata-Bhumika-Guthi/Testing/pull/13)

---

## Source evidence (system)

Structured provenance for reviewers (also stored in `source_metadata`):

```json
{
  "pr_title": "Refactor blackjack rules and dealer hit condition",
  "pr_url": "https://github.com/Venkata-Bhumika-Guthi/Testing/pull/13",
  "pr_number": 13,
  "repo": "venkata-bhumika-guthi/testing",
  "merge_commit_sha": "4e0cd6f1143e5d5fdd3f419a308b524394275fd4",
  "commits": [
    {
      "sha": "ab93ad2",
      "message": "Refactor blackjack rules and dealer hit condition"
    }
  ],
  "changed_files": [
    {
      "filename": "blackjack",
      "status": "modified",
      "additions": 1,
      "deletions": 3
    }
  ],
  "diff_summary_excerpt": "diff --git a/blackjack b/blackjack\nindex 97100e8..9de9538 100644\n--- a/blackjack\n+++ b/blackjack\n@@ -40,7 +40,6 @@ def blackjack():\n         dealer = deal()\n         show(player, dealer)\n \n-        # Blackjack check\n         if is_blackjack(player):\n             show(player, dealer, hide=False)\n             print(\"\\n\ud83c\udca1 BLACKJACK! You win 1.5x!\")\n@@ -50,7 +49,6 @@ def blackjack():\n                 break\n             continue\n \n-        # Double down option\n         doubled = False\n         if hand_value(player) in [10, 11] and balance >= bet:\n             choice = input(\"\\nDouble down? (y/n): \").lower()\n@@ -71,7 +69,7 @@ def blackjack():\n \n         print(\"\\n-- Dealer's turn --\")\n         show(player, dealer, hide=False)\n-        while hand_value(dealer) < 17:\n+        while hand_value(dealer) < 18:  # \u2190 Dealer now hits until 18 (was 17)\n             dealer.append(random.choice(deck))\n             show(player, dealer, hide=False)\n \n",
  "pr_summary": "- Title: Refactor blackjack rules and dealer hit condition\n- The dealer now hits until reaching 18 instead of 17.\n- This change makes the dealer more aggressive.\n- The adjustment slightly increases the house edge.\n- It makes it harder for players to win.\n- Affected file: `blackjack`.\n- Commit message: \"Refactor blackjack rules and dealer hit condition\".\n- Code changes include modifying the dealer's hit condition in the game logic.",
  "change_classification": {
    "labels": [],
    "skip_score": 0.0,
    "feature_score": 0.25
  },
  "documentation_rationale": "Generated documentation draft from merged PR materials.",
  "decision_reason": "New feature affecting game rules not covered by existing documentation."
}
```


## Source evidence (summary)

- **pr_number:** 13
- **pr_url:** https://github.com/Venkata-Bhumika-Guthi/Testing/pull/13
- **decision_reason:** New feature affecting game rules not covered by existing documentation.

## Version history

- [V1](./versions/v1.md) — _imported_
