---
tags: [Notebooks/User Administration]
title: Basics (FSOpen2022)
created: '2022-07-19T06:59:13.150Z'
modified: '2022-07-19T12:48:13.512Z'
---

# Basics (FSOpen2022) 

### Rationale
Deleting and editing a note should only be allowed for the user who created it.

### Relational Database Way
To achieve this one-to-many relationship, the id of the user would be stored in the resource table as a foreign key.

### NoSQL way
1. The resource would contain a reference key to the user who created it. 
```js
[
  {
    content: 'HTML is easy',
    important: false,
    _id: 221212,
    user: 123456,
  },
  {
    content: 'The most important operations of HTTP protocol are GET and POST',
    important: true,
    _id: 221255,
    user: 123456,
  }
]
```

2. The user would store an array of the ids of the resources they have created.
```js
[
  {
    username: 'mluukkai',
    _id: 123456,
    notes: [221212, 221255],
  },
  {
    username: 'hellas',
    _id: 141414,
    notes: [221244],
  },
]
```

3. The resources the user created would be stored in the users collection itself.
```js
[
  {
    username: 'mluukkai',
    _id: 123456,
    notes: [
      {
        content: 'HTML is easy',
        important: false,
      },
      {
        content: 'The most important operations of HTTP protocol are GET and POST',
        important: true,
      },
    ],
  },
  {
    username: 'hellas',
    _id: 141414,
    notes: [
      {
        content:
          'A proper dinosaur codes with Java',
        important: false,
      },
    ],
  },
]
```

## Creating Users

Implement a route for creating new users:
send a POST request to `/api/users`

Create a new User document with a hashed password using `bcrypt`
```bash
npm i bcrypt
```

Add validation that the username is unique and is in the desired format:
```js
const existingUser = await User.findOne({ username });

if (existingUser) {
  return response.status(400).json({
    error: 'username must be unique'
  })
};
```

## Creating a new resource

#### Resource is assigned to the user who created it:

1. Find a reference to the user by ID
2. Add the users ID to the `user` attribute of the resource
3. Save the resource
4. Add the id of this saved resource to the array of resource id's of the user 


```js
notesRouter.post('/', async (request, response, next) => {
  const body = request.body

  const user = await User.findById(body.userId)

  const note = new Note({
    content: body.content,
    important: body.important === undefined ? false : body.important,
    date: new Date(),
    user: user._id
  })

  const savedNote = await note.save()
  user.notes = user.notes.concat(savedNote._id)
  await user.save()
  
  response.json(savedNote)
})
```

## Sending a GET request to /api/users

When a GET request is made, the server should return the User objects along with the resource's they created and not just their ID. In a relational database, this functionality is done using the JOIN query. However, document databases do not support JOINs. 

#### Mongoose Populate

The `populate` method of Mongoose acts as a JOIN by doing multiple queries:
```js
usersRouter.get('/', async (request, response) => {
  const users = await User
    .find({}).populate('notes')

  response.json(users)
})
```

Limiting the fields you want to include in the references resource documents: 



