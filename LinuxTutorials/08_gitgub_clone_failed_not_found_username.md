# Fix: Github Clone Failed, Username not found

---

GitHub recently switched to an https scheme as the default for cloning repos.
As a side effect you may suddenly be prompted for a 'Username' and 'Password' when you push.
Where, previously, you were able to do so without typing in credentials.
The solution is to cause git to cache https credentials which is easy, since git uses curl under the covers.

In your `home` directory, create a file called: `.netrc`, for example: `/home/zafar/.netrc`.
In here put these:

```
machine github.com
login YOUR_GITHUB_EMAIL/YOUR_GITHUB_USERNAME
password YOUR_GITHUB_PASSWORD
```

fixed
