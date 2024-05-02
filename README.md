## Blogging Site Mini Project

### Models
- Author Model
```
{ fname: { mandatory}, lname: {mandatory}, title: {mandatory, enum[Mr, Mrs, Miss]}, email: {mandatory, valid email, unique}, password: {mandatory} }
```
- Blogs Model
```
{ title: {mandatory}, body: {mandatory}, authorId: {mandatory, refs to author model}, tags: {array of string}, category: {string, mandatory, examples: [technology, entertainment, life style, food, fashion]}, subcategory: {array of string, examples[technology-[web development, mobile development, AI, ML etc]] }, createdAt, updatedAt, deletedAt: {when the document is deleted}, isDeleted: {boolean, default: false}, publishedAt: {when the blog is published}, isPublished: {boolean, default: false}}
```

### Author APIs /authors
- Create author
  `Endpoint: BASE_URL/authors`

### POST /blogs
- Create a blog

### GET /blogs
- Returns all blogs in the collection that aren't deleted and are published

### PUT /blogs/:blogId
- Updates a blog by changing the its title, body, adding tags, adding a subcategory.

### DELETE /blogs/:blogId
- Delete blogs

### DELETE /blogs?queryParams
- Delete blog documents by category, authorid, tag name, subcategory name, unpublished


- Added authentication and authroisation feature

### POST /login
- author to login with their email and password. On a successful login attempt return a JWT token contatining the authorId

### Authentication
- Added authorisation implementation for the JWT token that validates the token before every protected endpoint is called. If the validation fails, return a suitable error message with a corresponding HTTP status code
- Protected routes are create a blog, edit a blog, get the list of blogs, delete a blog(s)
- Used a middleware for authentication purpose.


## Response

### Successful Response structure
```yaml
{
  status: true,
  data: {

  }
}
```
### Error Response structure
```yaml
{
  status: false,
  msg: ""
}
```





## Collections
### Blogs
```yaml
{
  "title": "How to win friends",
  "body": "Blog body",
  "tags": ["Book", "Friends", "Self help"],
  "category": "Book",
  "subcategory": ["Non fiction", "Self Help"],
  "published": false,
  "publishedAt": "", // if published is true publishedAt will have a date 2021-09-17T04:25:07.803Z
  "deleted": false,
  "deletedAt": "", // if deleted is true deletedAt will have a date 2021-09-17T04:25:07.803Z,
  "createdAt": "2021-09-17T04:25:07.803Z",
  "updatedAt": "2021-09-17T04:25:07.803Z",
}
```

#### Refer https://jsonplaceholder.typicode.com/guide/ for some fake blogs data.

#### Note: Create a group database and use the same database in connection string by replacing `groupXDatabase`
