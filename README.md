# µMail (MicroMail)
A lightweight, scalable SMTP client for sending email in MicroPython.


## Usage:

A bare minimal approach

```py
import umail
smtp = umail.SMTP('smtp.gmail.com', 587, email='my@gmail.com', password='mypassword')
smtp.to('someones@gmail.com')
smtp.send("This is an example.")
smtp.quit()
```


## API docs:

* **`umail.SMTP(host, port, [ssl, email, password])`**
  * **host** - smtp server
  * **port** - server's port number
  * **ssl** - set `True` when SSL is required by the server
  * **email** - my email/username to the server
  * **password** - my password

* **`SMTP.login(email, password)`**
  If you did not login when intializing the server, do it here!

* **`SMTP.to(addrs)`**
  * **addrs** - Recipient's email address. If multiple recipents, use a list, eg. `['aaa@mail.com', 'bbb@mail.com']`

* **`SMTP.write(content)`**
  To send a long email or an email that contains large attachments, you will most likely exceed the memory limit of your MCU.\
  Use this function to break up your email into smaller chunks.\
  Each call to `write()` will cause the current `content` to be sent to the server so you can load the next chunk.

* **`SMTP.send([content])`**
  Finish writing the email.\
  Make the SMTP server to actually send your email to the recipent address.

* **`SMTP.quit()`**
  Close the connection to the server


## Other

For more details, pleasse refer to sample code under `examples\`
