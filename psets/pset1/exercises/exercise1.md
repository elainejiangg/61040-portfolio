
# Exercise 1: Reading a concept

*Deliverables: Succinct answers to each of the questions.*

## Questions
1. _**Invariants.** What are two invariants of the state? (Hint: one is about aggregation/counts of items, and one relates requests and purchases). Say which one is more important and why; identify the action whose design is most affected by it, and say how it preserves it._
    
    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">

    a. Arregation Invariant: For any item in a registry, the sum of purchase counts cannot be greater than the original requested count
    
    b. Request/Purchase Consistency Invariant: Every purchase must correspond to an existing request in existing active registry

    The Consistency invariant is more important. This invariants lends itself to the Arregation Invariant: the request for a purchase must exist in the first place to even check the arregation invariant. The action most affected by this invariant is purchase, which preserves it by requiring that the registry is active and that a valid request for the item exists before recording a purchase.
    </div>

2. _**Fixing an action.** Can you identify an action that potentially breaks this important invariant, and say how this might happen? How might this problem be fixed?_

    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">
    a. The `removeItem` action can break the consistency invariant by deleting a request that already has associated purchases. This would orphan those purchases. To fix this, `removeItem` should be restricted so it only works if no purchases exist for the item, or it should refund/notify purchasers that that item was removed.
    </div>

3. _**Inferring behavior.** The operational principle describes the typical scenario in which the registry is opened and eventually closed. But a concept specification often allows other scenarios. By reading the specs of the concept actions, say whether a registry can be opened and closed repeatedly. What is a reason to allow this?_

    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">
    a. Yes, a registry can be opened and closed repeatedly. The `open` action only requires that the registry exists and is not currently active, and `close` requires that it is active, so there is no restriction preventing toggling the state multiple times. Allowing this behavior provides flexibility for the recipient, such as temporarily closing the registry to make edits or prevent purchases during a private period, and then reopening it later when they are ready to receive gifts again.
    </div>

4. _**Registry deletion.** There is no action to delete a registry. Would this matter in practice?_

    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">
    a. Yes, the lack of a delete action could matter in practice. Over time, users may accumulate old or inactive registries that clutter the system or their account. Keeping the data over time may also pose data privacy/legal concerns. 
    </div>

5. _**Queries.** What are two common queries likely to be executed against the concept state? (Hint: one is executed by a registry owner, and one by a giver of a gift.)_

    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">
    a. A common query by a registry owner is to view which items have been purchased and by whom, allowing them to track the gifts they received. A common query by a purchaser is to see which requested items are still available for purchase (i.e., have count > 0).
    </div>

6. _**Hiding purchases.** A common feature of gift registries is to allow the recipient to choose not to see purchases so that an element of surprise is retained. How would you augment the concept specification to support this?_

    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">
    a.The Registry would include a `hideFromRecipient Flag` field defaulted to False. We then add a `sethideFromRecipient(registry: Registry, mode: Flag)` action to toggle this setting. When `hideFromRecipient` is True, any queries about purchases from the registry owner would require that `hideFromRecipient` to be False to return the queries. Once the registry is closed, these queries will now work regardless if `hideFromRecipient` was True or False.
    </div>

7. _**Generic types.** The User and Item types are specified as generic parameters. The Item type might be populated by SKU codes, for example. Explain why this is preferable to representing items with their names, descriptions, prices, etc._

    <div style="border: 1px solid #ccc; padding: 10px; background-color: #f9f9f9;">
    a. Using generic Item types is preferable because allows for separation of concerns. In other words, the GiftRegistration concept handles only the logic of tracking requests and purchases, while item details (names, descriptions, prices) are managed by a separate product catalog system. Moreover, some items might have similar names (i.e., IPhone 17 vs Apple IPhone 17) may be mistaken as different items if name-based system is used, when they should refer the same items. Using SKU codes standardizes items and eliminates this duplication ambiguity.
    </div>
---

<div align="center">
  <a href="./exercise2.md">➡️ Go to Exercise 2</a>
</div>

<div align="center" style="margin-top: 1em;">
  <a href="../pset1.md">🏠 Go to Pset 1 Table of Contents</a>
</div>