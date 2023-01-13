# Password Encryption

---
## Security Service

```java
public class SecurityService {

    // generate random secure salt key
    public byte[] generateSalt() {
        SecureRandom random = new SecureRandom();
        byte[] salt = new byte[16];
        random.nextBytes(salt);
        return salt;
    }

    // SHA-512 hashing algorithm to encrypt password with salt key
    public byte[] hashingMethod(String password, byte[] salt) throws NoSuchAlgorithmException {
        MessageDigest md = MessageDigest.getInstance("SHA-512");
        md.update(salt);
        return md.digest(password.getBytes(StandardCharsets.UTF_8));
    }
}
```

## Validate Login

```java
public Optional<Principal> validateLogin(LoginRequest req) {
        return userRepo.findAll()
                .stream()
                .filter(u -> {
                    byte[] salt = u.getSalt();
                    byte[] hashedPassword = u.getPassword();
                    try {
                        return u.getUsername().equals(req.getUsername()) &&
                                Arrays.equals(hashedPassword, securityService.hashingMethod(req.getPassword(), salt));
                    } catch (NoSuchAlgorithmException e) {
                        e.printStackTrace();
                    }
                    return false;
                }).findFirst()
                .map(Principal::new);
    }
```