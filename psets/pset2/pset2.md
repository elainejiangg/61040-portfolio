# [Problem Set 2: Composing Concepts](https://61040-fa25.github.io/assignments/problem-set-2)

_Due Sep 21, 2025 11:59 PM_

## Concept Questions
 1. #### Contexts

   > Contexts will be for each `shortUrlBase`. It ensure each shortUrlSuffix to register with the shortUrlBase is unique. In other words, it guarenteeds the precondition of the register action of UrlShortener: "no shortening exists for shortUrlBase/shortUrlSuffix"

 2. #### Storing used strings

  >  The used set is necessary to guarantee that each generated nonce is unique within its context. For a counter-based implementation, the current counter maps to the size of set of previously generated string values, given that each time we call generate (i.e., add to our set a string that was not previously used but will now be), we increment the counter.

 3. #### Words as noces

   > One advantage of using words as nonces is that they are easier to remember, pronounce, and type, making the short URLs more user-friendly. One disadvantage is that the total number of available nonces is smaller and more predictable, which increases the chance of accidental or malicious discovery by unintended users. I would modify NonceGeneration to allow each context to be configured with a memorable flag and an optional dictionary of words. If memorable is set to True, the generate action would return a nonce composed of unused dictionary words; otherwise, it would fall back to a standard generation method, with the effect remaining the same—returning a nonce not already used and adding it to the used set.

 ## Synchronization Questions
### 1. Partial matching
   > The generate sync does not include the `targetUrl` because that is a separate concept covered in the register sync. The generate sync focuses only generating unique, unused nouce for it.

### 2.  Omitting names

  > The name omission convention is only used when the variable name matches the argument or result name exactly. When they differ, such as in the case of nonce being passed as `shortUrlSuffix`, explicit naming avoids confusion. It's also necessary when passing fixed values (like seconds: 3600) or generally when maintaining clarity across sync clauses to show how values flow between actions.


### 3. Inclusion of request

> The request action is included in the first two syncs because they directly respond to user input from `Request.shortenUrl`, using the data provided (like `targetUrl` and `shortUrlBase`). In contrast, the third sync doesn't depend on the user request. Instead, it follows the completion of `UrlShortening.register`, using the resulting `shortUrl` to trigger `setExpiry` as a system-side effect.

### 4. Fixed domain

   > To use a fixed domain like “bit.ly,” I would remove shortUrlBase from all the when clauses and just hardcode "bit.ly" as the value for shortUrlBase in the then clauses of the relevant syncs. This simplifies the logic by treating the base domain as a constant rather than something the user has to provide.

### 5.  Adding a sync

   ``` 
   sync deleteExpiredResource

   when ExpiringResource.expireResource(): (resource: shortUrl)

   then UrlShortening.delete(shortUrl)
```



## Extending the design
### 1. New Concepts

```
concept: UrlAnalytics [ShortUrl]

purpose: track the number of times each short URL is is accessed

principle: each time a short URL is looked up, its analytics count increases

state:
  a set of ShortUrls with/mapped to
    a count Number

actions;
  increment (shortUrl: ShortUrl)
    effect increases the count for shortUrl by 1

  getCount (shortUrl: ShortUrl): (count: Number)
    requires shortUrl is associated with requesting user
    effect returns the count for shortUrl 
 ```

 ```
 concept: UrlOwnership [User]

purpose: keep track of which user owns which short URLs

principle: only the owner of a short URL may access its analytics

state
  a set of Users with
    a set of owned ShortUrls

actions
  assign (user: User, shortUrl: ShortUrl)
    effect adds shortUrl to user’s owned set

  verifyOwnership (user: User, shortUrl: ShortUrl): (ok: Bool)
    effect returns True if shortUrl is in user’s owned set
```

### 2. Three Syncs
```
sync assignOwner

when
Request.shortenUrl (user, shortUrlBase, targetUrl)
UrlShortening.register (): (shortUrl)
then
UrlOwnership.assign (user, shortUrl) 
```
```
sync trackLookup

when UrlShortening.lookup (shortUrl)
then UrlAnalytics.increment (shortUrl)
```

```
sync viewAnalytics

when
Request.viewAnalytics (user, shortUrl)
Ownership.verifyOwnership (user, shortUrl): (ok)
then
if ok then UrlAnalytics.getCount (shortUrl)
```

### 3. Feature Extensions

- **Allowing users to choose their own short URLs**  
> This can be supported by introducing a `UserChoice` concept that lets users propose a custom suffix. A sync would first check if the suffix is available under the given base, and if so, pass it to `UrlShortening.register`; otherwise, fallback to automatic nonce generation or notify the user that it is unavailable. This separation keeps registration logic modular and avoids overloading `UrlShortening` wih validation concerns.

- **Using the “word as nonce” strategy to generate more memorable short URLs**  
> A separate `WordNonceGeneration` module could generate aliases using combinations of words from a curated dictionary, enforcing a minimum entropy threshold. Since this module would simply replace the default nonce generator, no changes would be needed to other concepts like `UrlShortening` or `Analytics`. This approach enhances usability without sacrificing design modularity.

- **Including the target URL in analytics**  
> A new `TargetUrlAnalytics` concept could be added to track access counts grouped by the final destination (e..g., `targetUrl`), in addition to individual `shortUrl` counts. During a lookup, both counters would be incremented, assuming the user has ownership rights. This would give users a consolidated view of traffic across different aliases pointing to the same resource.

- **Generate short URLs that are not easily guessed**  
> This could be done by creating a `SecureNonceGeneration` concept that applies minimum randomness or length rules depending on the domain. If a generated string is too short or easy to guess, it gets regenerated. This adds protection without needing changes to other parts of the system.

- **Support reporting analytics to creators who haven't registered**  
> This feature should be avoided, as it conflicts with the design principle that analytics should be private to the owner. Supporting anonymous or unregistered access would weaken security guarantees and require less reliable mechanisms like public tokens or shared accounts, which are difficult to manage safely without more extensions.
