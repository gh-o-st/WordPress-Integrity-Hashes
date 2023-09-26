# WordPress Integrity Hashes
This library is an ongoing effort aimed at offering an up-to-date set of file hashes for each WordPress version release. This repository serves as a centralized and reliable source for verifying the integrity of your WordPress installations.

The hashes were all made programmatically, but verified _visually_ (eg. ensuring the file wasn't empty, etc) by me, as well as some random sample testing to ensure the process was working as expected. Each version was downloaded, the resulting archive hashed, then unzipped and the following rules were used to determine what to hash:

1. All PHP, JS, and CSS files within wp-admin
2. All PHP, JS, and CSS files within wp-includes
3. All PHP, JS, and css files contained in the root directory of the install, excluding wp-config-sample.php (as this file is never executed)

## Key Features
1. Up-to-Date Coverage: This library stays current with each new WordPress release, ensuring that you have access to the most recent file hashes.
2. Flexible Data Consumption: Files are organized to allow you to choose the level of granularity you need—whether that’s a specific version (e.g., 1.0-platinum) or a group of versions (e.g., all 1.0.x releases).
3. Minimized Collision Risk: I used SHA-256 for hashing to minimize the risk of hash collisions, given the sheer number of files being hashed.

Hmm, now that I think about it, that last point doesn't even matter. The volume is from the aggregation of versions. Each release would have miniscule chances of collisions using md5 or sha1 for its respective list of files.
<br><br><br>
_...Oh well, what's done is done._

---

> _**A Note on Archive Hashes**_
> 
> _Please note that the .zip archive hashes available in this library will not align with those on the WordPress release archive page, as those are md5 and sha1 hashes, not sha256._

---

## Version Grouping
Each version is conveniently organized into folders and subfolders. This allows for easy access to specific sets of data:

* Top-Level Group: Aggregates based on the first digit (e.g., all 1.x versions).
* Second-Tier Group: Further grouping based on the second digit (e.g., 1.0.x, 1.2.x).
* Version-Specific Group: Focused data for a specific release (e.g., 1.0-platinum, 2.0-gold).

```
WordPress Integrity Hashes
├── 1.x
│   ├── 1.0.x
│   │   └── 1.0-platinum
│   └── 1.2.x
│       └── 1.2
├── 2.x
│   ├── 2.0.x
│   │   └── 2.0
│   └── 2.1.x
│       └── 2.1
└── 3.x
    ├── 3.0.x
    │   └── 3.0
    └── 3.1.x
        └── 3.1
//...
```

## How to Use
Navigate to the directory corresponding to the version or versions of interest. The JSON files contain the file hashes required for integrity verification, allowing you to consume the data as needed for your specific requirements. Feel free to tailor this to better suit the specifics of your project!
<br><br><br>
_**Note**: These hashes are meant for integrity verification and are not a substitute for security measures like code audits._
