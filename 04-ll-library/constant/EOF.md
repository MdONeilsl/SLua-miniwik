# `EOF`

This value is provided by both ll.GetNotecardLine (when triggered through the dataserver event) and ll.GetNotecardLineSync if the line index requested is beyond the notecard's boundary. It always equates to three consecutive newline characters ("\n\n\n").

**Type:** `string`

**Value:** `\n\n\n`