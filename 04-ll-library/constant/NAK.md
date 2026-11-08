# `NAK`

When ll.GetNotecardLineSync or ll.FindNotecardTextSync executes and the corresponding notecard is absent from the region's cache, this value is returned as a single-entry list. This specific string represents an ASCII NAK signal bracketed by newline characters (using codes 10, 21, and 10).

**Type:** `string`

**Value:** `\n\x15\n`