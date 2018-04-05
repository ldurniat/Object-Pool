# Object-Pool
*Object-Pool* is simple module for Corona for reusing objects instead of creating new ones. It is inspired by [GBC Object Pool](https://marketplace.coronalabs.com/corona-plugins/gbc-object-pool) module by John Schumacher.

### Example

	local objectpool = require 'pl.ldurniat.objectpool.objectpool'

	local i = 0

	-- Create new Text Object 
	local function createObject()

		i = i + 1
		return display.newText( i, 0, 0, 40, 20, native.systemFont, 20 )

	end		

	-- Create pool with Text Objects
	local textPool = objectpool.init( createObject, 30 )

	local function putIntoPool( object )

		-- We don't need it now
	    textPool:put( object )

	end

	local function addTextObject()

		-- Get Text Object from pool
		local text = textPool:get()

		-- Check if we get object or nil
		if text then

			transition.to( text, 
				{ 	
					x=math.random( display.contentWidth ), 
					y=math.random( display.contentHeight ), 
					onComplete=putIntoPool
				}
			)

		end	

	end	

	timer.performWithDelay( 50, addTextObject, 0 )

Also see [Simple-Particle-System](https://github.com/ldurniat/Simple-Particle-System).

### Run

To run code you need install [Corona SDK](https://portal.coronalabs.com) 

### License

This project is licensed under the MIT License - see the [LICENSE.md](https://github.com/ldurniat/Object-Pool/blob/master/LICENSE) file for details.


