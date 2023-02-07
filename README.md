# Instagram-User-Analytics-Project
            select username,Min(created_at)
            from users
            group by created_at limit 5; 
            select username 
               from users 
            where id Not in (select user_id from photos)
               order by username;
            Select 
            users.id as user_id,username,
            photos.id as photo_id,
            photos.image_url, count(*) as total_likes_count
        from photos
           Join likes on photo_id = likes.photo_id
        join users on users.id = photos.user_id
        group by photo_id
        order by total_likes_count desc limit 1;
        tag_name, tags.id,
       count(*) as total_tags
          from tags
              join photo_tags on tags.id = photo_tags.tag_id
       group by tags.id
       order by total_tags desc
       limit 5;
       WITH CTE as  
       (select 
       u.id as userid,
       count(p.id) as photoid
       from ig_clone.users u
       left join 
       ig_clone.photos p
       on u.id = p.user_id
       group by u.id)
       select sum(photoid) as total_photos,
       count(userid) as total_users,
       sum(photoid)/count(userid) as post_per_user from CTE
       where photoid > 0;
       select count(*) from ig_clone.photos;
      select users.id as user_id,
            users.username,
            count(*) as total_user_likes
            from users 
            join likes 
            on users.id = likes.user_id
            group by users.id 
            having total_user_likes = 257
            ;


