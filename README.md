# unix_passwordCracking

=============================================
```Python

# worked under UNIX

import crypt

def testPass(cryptPass):
    salt = cryptPass[0:2] #salt为前2位
    dictFile = open("dictionary.txt","r") #只读方式读取字典
    for word in dictFile.readlines():
        word = word.strip("\n")
        cryptWord = crypt.crypt(word,salt)
        if (cryptWord == cryptPass):
            print("[+] Found Password: " + word + "\n")
            return
        print("[-] Password Not Found. \n")
        return

def main():
    passFile = open("password.txt","r")
    for line in passFile.readlines():
        if ":" in line:
            user = line.split(":")[0] #root: egg
            cryptPass = line.split(":")[1].strip(" ")
            print("[*] Cracking Password For : " + user)
            testPass(cryptPass)

if __name__ == '__main__':
    main()

```

```
 if you got a Error:`ModuleNotFoundError: No module named '_crypt'
 you should know:`you need to run it under UNIX,crypt() is a unix crypt for password
```
