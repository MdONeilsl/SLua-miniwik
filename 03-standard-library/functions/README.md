# functions

This folder contains documentation for core Lua functions and built-in utilities available in SLua.

| Path | Contents |
|---|---|
| [assert](assert.md) | Asserting a condition with optional message |
| [collectgarbage](collectgarbage.md) | Manually triggers Lua garbage collection cycle |
| [dangerouslyexecuterequiredmodule](dangerouslyexecuterequiredmodule.md) | Executes external modules unsafely and directly |
| [error](error.md) | Raising errors with custom messages or objects |
| [gcinfo](gcinfo.md) | Reports current garbage collector memory usage |
| [getfenv](getfenv.md) | Retrieves local execution environment scope |
| [getmetatable](getmetatable.md) | Accessing an object's associated metatable |
| [graphheap](graphheap.md) | Dumps graph-allocated memory structure to file |
| [graphuserheap](graphuserheap.md) | Dumps user-allocated memory structure to file |
| [ipairs](ipairs.md) | Iterating over array-like sequence keys |
| [loadstring](loadstring.md) | Compiling string source code into executable function |
| [newproxy](newproxy.md) | Creating generic, type-agnostic proxy objects |
| [next](next.md) | Iterating through table pairs sequentially |
| [pairs](pairs.md) | Iterating over all table keys and values |
| [pcall](pcall.md) | Protected call handling potential runtime errors |
| [print](print.md) | Outputting multiple arguments to standard output |
| [rawequal](rawequal.md) | Strict comparison of values and types |
| [rawget](rawget.md) | Direct table access ignoring index methods |
| [rawlen](rawlen.md) | Getting raw length of tables or strings |
| [rawset](rawset.md) | Setting table fields ignoring newindex methods |
| [require](require.md) | Loading and executing external modules by name |
| [select](select.md) | Selecting specific range of passed arguments |
| [setfenv](setfenv.md) | Setting local execution environment scope |
| [setmetatable](setmetatable.md) | Modifying a table's associated metatable |
| [tonumber](tonumber.md) | Converting string to number with specified base |
| [toquaternion](toquaternion.md) | String conversion into a quaternion type |
| [torotation](torotation.md) | String conversion into a rotation quaternion |
| [tostring](tostring.md) | Converting any object instance to string |
| [touuid](touuid.md) | Generating UUID from various inputs |
| [tovector](tovector.md) | String conversion into a vector type |
| [type](type.md) | Determining the basic data type name |
| [typeof](typeof.md) | Detailed type checking including user data |
| [unpack](unpack.md) | Extracting multiple values from array indices |
| [xpcall](xpcall.md) | Protected call handling potential runtime errors |
