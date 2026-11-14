# Birthday Wishlists

Live at **https://birthday-wishlists-7c5e73.web.app**

A shared birthday wishlist for friends. Anyone with the link can view every list. Each person can edit only their own list,
from the browser they created it in.

- `docs/index.html` is the whole site
- `firestore.rules` holds the database rules. Each list stores a hash of a private key kept in its owner's browser,
  and changes are accepted only with the matching key.
- Hosting and the database run on Firebase's free Spark plan, project `birthday-wishlists-7c5e73`.

To redeploy after a change: `firebase deploy --project birthday-wishlists-7c5e73`
