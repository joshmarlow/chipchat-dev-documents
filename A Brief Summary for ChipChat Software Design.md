# ChipChat Software Design
This a brief summary from the App Functions description. A very first edition of the software design doc.
## Models
### User:
User session:
1. Chipchat id (E.g. @e12345677)
2. Database id
3. User token (used for some actions, such as updating profile info and changing the info for the group you owned)
4. Phone number -> SignIn
5. Nickname: user defined name
6. Chat group ids: Joined chat groups
7. Host group ids ? 
8. Chat history for a user ? (<message contains user id> or <user contains message id>) (MongoDB?)
9. Blocked user ids
10. Friends ids
11. Stories (posts): all posts sent by user in all chat groups
12. Notifications: (hard)
    1. New friend requests
    2. Mentions
    3. New stories under the group you joined
13. Information be shown in user profile page:
    1. Private info: the info only visible for the account owner:
        1. Blocked user ids (No.8 above)
        2. Phone number (No.3 above)
        3. Joined chat group ids (No.5 above)
        4. Host group ids (No.6 above)
    2. Public info: visible for others
        1. Nickname (No.4 above)
        2. User's ChipChat id (No.1 above)
        3. oined chat groups (No.5 above)
        4. All friends (only friends can see) (No.9 above)
        5. All stories (posts) (No.11 above)
        
Things not mentioned in App Functions description:
1. User joined date, timestamp


### Topic（Category）(E.g. #music)
1. Topic id
2. Topic name
3. Chat group ids belongs to this topic
 
### Public chat group (the chat group under a topic).
1. Chat group id -> sharable
    1. id, QR code
    2. Generate an invitation url
2. Chat group topic (category E.g. #music)
3. Description (changeable)
4. Chat group name (changeable)
5. Chat group image (image url)
6. Chat group location (zip code) (optional)
7. Topic id or topic name
8. Host member id
9. Member ids
10. Stories (Posts) ids
11. Messages (chats)

### private chat group (2 ~ more people)
Just a chat group, without topic

### Chat message                  
1. Message id
2. Timestamp
3. Owner id
4. Group id ?
5. Type (photo, text, video)
6. Content (text, photo, video)
 
### Story (post) (comments)
1. Story id
2. Timestamp
3. Content (test, images, hashtag<later>)
4. Parent Story id (reply to a story)
5. Comments ids (Comments are also story?)
6. Only two layers, if you wish to reply someone's comments, @mention the user in your comments.
7. hit count

## Log in
1. Step 1: User input the phone number
2. Step 2: server generates the temporary token, send to user by message (6 digits) (use smsgateway service)
3. Step 3: phone and token register and login
4. Step 4: return a user-token (auto renew the token)


## Hashtag and Mention
1. Currently no hashtag in user stories
2. Mention a user, and send notification.

## Share Story (only the main story)
1. Share the story inside the app (Story id and group id)
2. Share to the outside. url and story summary.


## Search
1. Input a search term, return all things (public chat group, stories, topic, people...)

## Recommendation (Machine learning)
Based on the topic you like and other things to recommend the hot stories to users.









