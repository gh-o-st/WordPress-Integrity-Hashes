# WordPress Integrity Hashes
## Introduction
The WordPress Integrity Hashes library is an ongoing effort aimed at offering an up-to-date set of file hashes for each WordPress version release. This repository serves as a centralized and reliable source for verifying the integrity of your WordPress installations.

## Key Features
1. Up-to-Date Coverage: This library stays current with each new WordPress release, ensuring that you have access to the most recent file hashes.
2. Flexible Data Consumption: Files are organized to allow you to choose the level of granularity you need—whether that’s a specific version (e.g., 1.0-platinum) or a group of versions (e.g., all 1.0.x releases).
3. Minimized Collision Risk: I used SHA-256 for hashing to minimize the risk of hash collisions, given the sheer number of files being hashed.

> _**A Note on Archive Hashes**_
> _Please note that the .zip archive hashes available in this library will not align with those on the WordPress release archive page. We use SHA-256 hashes specifically to minimize the risk of hash collisions due to the large volume of files._

## Version Grouping
Each version is conveniently organized into folders and subfolders. This allows for easy access to specific sets of data:

* Top-Level Group: Aggregates based on the first digit (e.g., all 1.x versions).
* Second-Tier Group: Further grouping based on the second digit (e.g., 1.0.x, 1.2.x).
* Version-Specific Group: Focused data for a specific release (e.g., 1.0-platinum, 2.0-gold).

## How to Use
Navigate to the directory corresponding to the version or versions of interest. The JSON files contain the file hashes required for integrity verification, allowing you to consume the data as needed for your specific requirements.

### Example in PHP
```php
$json = file_get_contents('path/to/hashes.json');
$hashes = json_decode($json, true);

// Access a specific version's hash
$hash = $hashes['1.0-platinum']['some_file.php'] ?? null;
```
### Example in Python
```python
import json

with open('path/to/hashes.json', 'r') as f:
    hashes = json.load(f)

# Access a specific version's hash
hash_value = hashes.get('1.0-platinum', {}).get('some_file.php', None)
```
### Example in Node.js
```js
const fs = require('fs');

const jsonData = fs.readFileSync('path/to/hashes.json', 'utf-8');
const hashes = JSON.parse(jsonData);

// Access a specific version's hash
const hash = hashes['1.0-platinum']?.['some_file.php'] || null;
```
### Example in Go
```Go
package main

import (
	"encoding/json"
	"io/ioutil"
	"log"
)

func main() {
	data, err := ioutil.ReadFile("path/to/hashes.json")
	if err != nil {
		log.Fatal(err)
	}
	
	var hashes map[string]map[string]string
	json.Unmarshal(data, &hashes)

	// Access a specific version's hash
	hash, ok := hashes["1.0-platinum"]["some_file.php"]
	if ok {
		// Do something with hash
	}
}
```
Feel free to tailor this to better suit the specifics of your project!
