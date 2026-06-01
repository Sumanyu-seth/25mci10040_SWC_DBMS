Acceptance Rate By Date:
```sql
SELECT
    sent.date,
    AVG(CASE WHEN accept.action = 'accepted' THEN 1 ELSE 0 END)
FROM
    fb_friend_requests AS sent
LEFT JOIN fb_friend_requests AS accept
    ON
        sent.user_id_sender = accept.user_id_sender
        AND accept.action = 'accepted'
WHERE sent.action = 'sent'
GROUP BY 1;
```
<img width="1641" height="696" alt="Screenshot 2026-05-31 153507" src="https://github.com/user-attachments/assets/c5591949-2bd5-4226-90b3-a2db852cc3f0" />
