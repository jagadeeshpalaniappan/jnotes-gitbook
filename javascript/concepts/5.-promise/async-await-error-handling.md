# Async / Await -Error Handling



{% tabs %}
{% tab title="try/catch" %}


```javascript
async function userProfile() {
  try {
    let user = await getUser();
    let friendsOfUser = await getFriendsOfUser(userId);
    let posts = await getUsersPosts(userId);

    showUserProfilePage(user, friendsOfUser, posts);
  } catch(e) {
    console.log(e);
    // ***** But how do you know which fetch call failed? *****
  }
}
```
{% endtab %}

{% tab title="individual-catch" %}
```javascript
async function userProfile() {
  let user = await getUser().catch(e => console.log('Error: ', e.message));
  let friendsOfUser = await getFriendsOfUser(userId).catch(e => console.log('Error: ', e.message));
  let posts = await getUsersPosts(userId).catch(e => console.log('Error: ', e.message));
  
  showUserProfilePage(user, friendsOfUser, posts);
}

```

The solution above will handle individual errors from the requests, but its a mix of patterns. There should be a cleaner way to use async/await without using `.catch` method
{% endtab %}

{% tab title="use: util fn" %}
### Here's my solution to a better async/await error handling

```javascript
// Utitlity Fn:
const handle = (promise) => {
  return promise
    .then(data => ([data, undefined]))
    .catch(error => Promise.resolve([undefined, error]));
}

async function userProfile() {

  let [user, userErr] = await handle(getUser());
  if(userErr) throw new Error('Could not fetch user details');

  let [friendsOfUser, friendErr] = await handle(getFriendsOfUser(userId));
  if(friendErr) throw new Error('Could not fetch user\'s friends');

  let [posts, postErr] = await handle(getUsersPosts(userId));
  if(postErr) throw new Error('Could not fetch user\'s posts');

  showUserProfilePage(user, friendsOfUser, posts);
}
```
{% endtab %}
{% endtabs %}







{% embed url="https://dev.to/sobiodarlington/better-error-handling-with-async-await-2e5m" %}



