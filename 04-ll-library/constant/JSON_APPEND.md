# `JSON_APPEND`

This specifier passed to ll.JsonSetValue instructs that the provided value must be added to the array located at the designated nesting level. Should the intended location not contain an array, any current contents will be completely replaced by the newly created array.

**Type:** `number`

**Value:** `-1`

## Deprecated

- **reason:** Use 'lljson.decode' and 'table.insert' instead.
