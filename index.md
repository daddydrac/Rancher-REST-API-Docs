<h2 id="1">Authentication</h2>

<h3>1.0 Logging into Rancher Locally</h3>

  <strong>1.1 API Route:</strong> 
  ``` 
  https://127.0.0.1/login
  
  ```

  <strong>1.2 Query String Params:</strong>
  ``` 
  action: login 
  
  ```

  <strong>1.3 Fully Qualified Route:</strong> 
  ``` 
  https://127.0.0.1/v3-public/localProviders/local?action=login 
  
  ```

  <strong>1.4 Payload:</strong>
  ```
  {
    username: "admin"
    password: "supersecret"
    description: "UI Session"
    responseType: "cookie"
    ttl: 57600000
    labels: {ui-session: "true"}
    ui-session: "true"
  }
  ```
    
  <strong>1.5 CRSF and Session Cookies</strong>
  In the header requests, you'll need add (as all one line): 
   ```
   Cookie: R_USERNAME=admin; 
   CSRF=f93a4bdb7f; 
   R_SESS=token-8blls:pvwss586wwdd46bxgcl7bghkkbbgqgc7hqgkx9rzsw65sgbsd5wzmt
   ```
  
  ![](assets/images/cookies-auth.png)

  <strong>1.6 Local Auth REST API schema:</strong>
```
{
  "actions": {
  "login": "…/v3-public/localProviders/local?action=login"
},
  "baseType": "authProvider",
  "creatorId": null,
  "id": "local",
  "links": {
  "self": "…/v3-public/localProviders/local"
},
  "type": "localProvider"
}
 ```















---
layout: default
---

Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](./another-page.html).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
