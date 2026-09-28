### Social Media Platform  
Users of a social-media platform are identified by a unique user identifier. The platform also stores each user’s unique username, email, password hash, join date, one or more profile pictures, and a short bio. Users create **Posts**. Each post is identified by a unique post identifier and records its content, timestamp, visibility setting (public or friends-only), and a derived like count. Users can comment on posts. Each **Comment** is distinguished within its post by a comment identifier and also stores the comment text, timestamp, and derived like count. Users can like posts or comments; each like records the exact timestamp it was made. Users can also follow other users; the follow relationship stores the date the follow began and whether notifications are enabled.

<details>
<summary>Social Solution</summary>

- Entities: **User**, **Post**, **Comment** (weak on Post), **Like** (weak on Post/Comment + User)  
- Relationships:  
  - **Creates** (User 1 : N Post) – total on Post  
  - **CommentsOn** (User 1 : N Comment) – total on Comment  
  - **Follows** (User M : N User) – recursive  
  - **Likes** (User M : N Post/Comment) → **Like** entity  
- Attributes:  
  - User: userID (PK), username, joinDate  
  - Post: postID (PK), content, timestamp  
  - Comment: commentID (partial key), text, timestamp  

</details>
