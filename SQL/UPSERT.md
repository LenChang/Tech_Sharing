# Overview
> INSERT … ON DUPLICATE KEY UPDATE

# MySQL
```
INSERT INTO BLOGPOSTs
    (
        postId, postTitle, postPublished
    )
VALUES
    (5, 'Python Tutorial', '2019-08-04')
ON DUPLICATE KEY UPDATE
    postId = 5, postTitle = 'Python Tutorial', postPublished = '2019-08-04';

-- Print all rows
SELECT 
    *
FROM
    BLOGPOSTs;
```

# Reference
- https://www.techbeamers.com/mysql-upsert/
