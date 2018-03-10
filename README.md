# ssh-knownhost

Tool that combines `ssh-keyscan` with `ssh-keygen` to echo to stdout the required
string for your .ssh/known_hosts file if the fingerprint of the remote ssh-server
matches the provided fingerprint.

This allows you to easily add fingerprint verified entries to the `.ssh/known_hosts` 
file without the run-around.

## Examples

Check the remote ssh-server has the provided SHA256 fingerprint and echo the 
known_hosts entry to stdout
```
$
$ ssh-knownhost git-codecommit.us-east-2.amazonaws.com 3lBlW2g5xn/NA2Ck6dyeJIrQOWvn7n8UEs56fG6ZIzQ
|1|rc1EFpa3dGvQocfQVp5n77zvlFY=|ca6xmx4sxubSrqX9eqtcn/Dj9hg= ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCNbmnXfe621xtVMkrwOqf6QNIlnOKkQ01KoM6gKC4nv5T08hbGcGp6iYplGLKMLlki+auO1J3JTA3qAKDobZR1wDqtW9LC2k46GHV4YigUpd6D+YdranJqbxpGOuNd6c1EP50vQnlW9MxZYExyrZKT0UfOJAydQLoWPuSioyHk3zAltSIrCxczP3jxAhuoq++eUrdC5uF6UMNJC10eBA9XglAe2oRLzApoStyCAiKVnoBndU2NpJWqNw0K5qfEUx2vyQFfHNRAwNNRDFtkdE9ho255YECTO07Zg37QCZ+hV5VAoFRu5CHSXqVZc5YN1YXkZ8SVHyBX7krO80QaaDor
$
```

Check the remote ssh-server has the provided MD5 fingerprint and echo to stdout
```
$
$ ssh-knownhost git-codecommit.us-east-2.amazonaws.com a9:6d:03:ed:08:42:21:be:06:e1:e0:2a:d1:75:31:5e
|1|rc1EFpa3dGvQocfQVp5n77zvlFY=|ca6xmx4sxubSrqX9eqtcn/Dj9hg= ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCNbmnXfe621xtVMkrwOqf6QNIlnOKkQ01KoM6gKC4nv5T08hbGcGp6iYplGLKMLlki+auO1J3JTA3qAKDobZR1wDqtW9LC2k46GHV4YigUpd6D+YdranJqbxpGOuNd6c1EP50vQnlW9MxZYExyrZKT0UfOJAydQLoWPuSioyHk3zAltSIrCxczP3jxAhuoq++eUrdC5uF6UMNJC10eBA9XglAe2oRLzApoStyCAiKVnoBndU2NpJWqNw0K5qfEUx2vyQFfHNRAwNNRDFtkdE9ho255YECTO07Zg37QCZ+hV5VAoFRu5CHSXqVZc5YN1YXkZ8SVHyBX7krO80QaaDor
$
```

Check the remote ssh-server has the provided SHA256 fingerprint and append the 
output to ~/.ssh/known_hosts
```
$
$ ssh-knownhost git-codecommit.us-east-2.amazonaws.com 3lBlW2g5xn/NA2Ck6dyeJIrQOWvn7n8UEs56fG6ZIzQ >> ~/.ssh/known_hosts
$ 
```

Deliberatly using a bad fingerprint value
```
$
$ ssh-knownhost git-codecommit.us-east-2.amazonaws.com bad-fingerprint-value
No matching fingerprint
$
```

## Some AWS CodeCommit known SSH server fingerprints
* https://docs.aws.amazon.com/codecommit/latest/userguide/regions.html#regions-fingerprints

