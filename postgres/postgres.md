# PostGreSQL

---

## Password Encryption

### Extention

```sql
CREATE EXTENSION pgcrypto;
```

### Insert Query

```sql
INSERT INTO users (email, password)
VALUES ('johndoe@mail.com',
        crypt('johnspassword', gen_salt('bf')));
```

### Select Query

```sql
SELECT id
FROM users
WHERE email = 'johndoe@mail.com'
  AND password = crypt('johnspassword', password);
```