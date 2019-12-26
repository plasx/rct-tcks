

# Setup
installing dependencies:

    brew install python3
    brew install pipenv
    cd rct-tcks
    pipenv install
    
    
    
# Creating tracks via Django Shell
    
    cd app
    python manage.py shell
    
Then in the shell, create a sample track as such:

    from tracks.models import Track
    Track.objects.create(title="Track 1", description="Track 1 Description", url="https://track1.com")

#Using GraphiQL UI
Using GraphiQL via http://localhost:8000/graphql/
 
### Create a User

    mutation {
      createUser(username: "DanX", password: "1234", email: "dan@dan.com") {
        user {
          id
          username
          password
          email
          dateJoined
        }
      }
    }

### Get User

    query {
      user(id: 1){
        id
        password
        email
        username
        dateJoined
      }
    }

### Get Token

    mutation {
      tokenAuth(username:"DanX", password: "1234"){
        token
      }
    }

### Get users info  with JWT token
HEADER:

    Content-Type: application/json
    Authorization: JWT  <token>
*Note: Token would look like this: `JWT  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6IkRhblgiLCJleHAiOjE1NzcyOTM3MDEsIm9yaWdJYXQiOjE1NzcyOTM0MDF9.M34DhT3iG2QhEzFK8d--v6o8BibFP9LabrMJ1xAlcqw`*

BODY:

    {
      me {
        id
        username
        email
      }
    }
   
### updating tracks

    mutation {
      updateTrack(trackId: 4, title: "Track5", description: "Track5 description", url: "http://track5.com" ){
        track {
          id
        }
      }
    }

### like a track

    mutation{
      createLike(trackId:4){
        track{
          id
        }
      }
    }