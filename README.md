# WordPress Integrity Hashes
A library I hope to keep up to date with each new WordPress release, which compiles a json file of the file hashes for that particular version release. The `.zip` archive hashes won't match up to those on the WordPress release history archive page. This is because the file hashes I've used are sha256 instead of sha1 or md5. Because of the vast number of files that have to be hashed, the probability of collisions with the smaller memspace increased dramatically compared to a few hundred hashes for the total number of releases.

Each release is grouped such that you can consume as little or as much of the data as you want for each release. (ie. only 1.0-platinum, or all 1.0.x releases, etc)
