# Module 1: Email Header Analysis

Look at the listening ports on the machine
```
sudo netstat -ltnp
```
see port 25 (SMTP)


```
ps -fax | grep [PID]
```

```
cd /var/mail
ls
```

```
sudo less hvale
```

```
sudo grep "PHP" *
```

```
sudo grep "X-Mailer:" *
```

```
sudo grep "X-Mailer:" * | sort | uniq -c | sort -n
```

```
sudo cat tavaline | grep "X-Mailer: PHPMailer" -B 20
```

```
sudo cat tavaline | grep "X-Mailer: PHPMailer" -A 20
```

