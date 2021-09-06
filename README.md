# Simple Hash Map for ip/dn mapping

## Entry data structure
```sh=
struct entry {
	char *key;
	void *data;
};
```
- please make sure both key and data is stored in heap instead of stack
	- key and data should be malloced
- all key should be a null-terminated string

## ip2dn Functions
```c=
int map_init(struct map *map);
/*
 * Initialize the map data structure
 * Return Value
 *	If success, 0 will be returned. If failed, 1 will be returned.
 * */

uint32_t hash(char *key, unsigned int cap); 
/*
 * Calculate the hash value according to the given key which is ip in these design
 * Return value
 * 	The hash value corresponding to the key.
 * */

entry *find(struct map *map, char *key);
/*
 * Find the empty slot or the slot of the key
 * Return Value
 * 	If there is a hit, the return pointer to the entry.
 * */

int insert(struct map *map, entry *entry);
/*
 * Insert the entry into the map
 * Return value
 * 	If success, 0 will be returned. If failed, 1 will be returned.
 * */

int expand(struct map *map);
/*
 * expand the bucket size of the map and rehashing
 * Return Value
 * 	If success, 0 will be returned. If failed, 1 will be returned.
 * */
```
