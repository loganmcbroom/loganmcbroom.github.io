---
layout: default
title: Eye Coordinate Finder
parent: Software
---

```python
-- Eye coordinate finder for all builds(hopefully)
-- To be run in the cheat engine lua script thingy
-- The script runs when you trigger one of the east/west messages and prints the coordinates
local results = AOBScan("5C 50 34 56", "", 0)
if results == nil then	
	print("Eye spawn address not found")
else
	local eye_spawn_address = tonumber(results[0], 16)-0xE
	results.destroy()

	print(string.format("Eye spawn address: %x", eye_spawn_address))
  	debug_setBreakpoint(eye_spawn_address, function()
    	local x = 0
    	local y = 0
    	if tonumber(tostring(ECX))>100000 then x = tostring(ECX) - 4294967295 else x = tostring(ECX) end
    	if tonumber(tostring(EDX))>100000 then y = tostring(EDX) - 4294967295 else y = tostring(EDX) end
    	print('X: '..x..' Y: '..y)
    	end)
end
```

A c++ version of this can be found [here](https://pastebin.com/rXNsPi47) (this code can stay in a link, it is long spaghetti).

