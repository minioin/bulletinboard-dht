BulletinBoard DHT
=================

BulletinBoard is a general-purpose Distributed-Hash-Table based on Kademlia [1].
The interface is provided as a D-Bus service via these commands:

    Service: org.manuel.BulletinBoard
      Object Path: /
      Interface:   org.manuel.BulletinBoard
      Commands:
       - Get(String app_id, Array of [Byte] key)
          -> (Array of [Array of [Byte]] values)
       - Put(String app_id, Array of [Byte] key, Array of [Byte] value)
          -> ()
       - Remove(String app_id, Array of [Byte] key, Array of [Byte] value)
          -> ()
       - RemoveKey(String app_id, Array of [Byte] key)
          -> ()

where `app_id` is an string specific to your application (e.g. `myfilesharingapp`).
The `key` is hashed together with `app_id` using SHA-1 and the `value` may not
exceed 2048 bytes.
Note that you cannot assume that a value returned by the `Get` command was
really published by an instance of your application.

[1] http://pdos.csail.mit.edu/~petar/papers/maymounkov-kademlia-lncs.pdf