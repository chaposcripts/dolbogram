# dolbogram
Dolbogram is a simle lua telegram bot api library

## Installation
1. download latest version from releases
2. put `dolbogram` folder to `package.path` path

## Usage example
```lua
local Degrogram = require('degrogram');
local Bot = Degrogram:new('YOUR-TOKEN');

Bot:onMessage(function(ctx)
    print(('[New message] From: %s (@%s), chat: %d, message: %s'):format(ctx.chat.first_name or 'N/A', ctx.chat.username, ctx.chat.id, ctx.text));
    if (ctx.chat.type == 'private') then
        if (ctx.text == '/start') then
            Bot:sendMessage({
                chat_id = ctx.chat.id,
                text = 'Hello, i\'m alive!';
            });
        elseif (ctx.text:match('/echo (.+)')) then
            Bot:sendMessage({
                chat_id = ctx.chat.id,
                text = ctx.text:match('/echo (.+)');
            });
        end
    end
end);

Bot:startPolling();
```
