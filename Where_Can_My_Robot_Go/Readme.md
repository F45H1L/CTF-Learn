# Where Can My Robot Go?

## 1. Check robots.txt

The hint says:

What does disallow tell a robot?

This indicates that we should inspect the website's robots.txt file.

Visit:

https://ctflearn.com/robots.txt

## 2. Inspect the Disallow Entry

The page contains:
```
User-agent: *
Disallow: /70r3hnanldfspufdsoifnlds.html
```
The Disallow directive tells web crawlers not to access the specified path.

## 3. Visit the Disallowed Path

Append the path to the main website:

https://ctflearn.com/70r3hnanldfspufdsoifnlds.html

## 4. Retrieve the Flag

The page reveals:
Flag
```
CTFlearn{r0b0ts_4r3_th3_futur3}
```
Key Takeaway

robots.txt is commonly used to provide crawling instructions to search-engine bots. During web reconnaissance, it can sometimes reveal interesting or sensitive-looking paths that are worth manually investigating.

Note: robots.txt is not an access-control mechanism. A Disallow entry does not prevent users from accessing the path.