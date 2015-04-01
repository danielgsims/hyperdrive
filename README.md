# Hyperdrive - A Hypermedia Specification

### Current Version 0.1

Any input is appreciated. You can file an issue, make a pull request or reach out on Twitter

## Introduction

Hyperdrive is a hypermedia specification for representing entities.
Hyperdrive is intended to be generic specification that extends existing JSON hypermedia specifications,
making them even more awesome, kind of like painting flames on a space ship. Hyperdrive adds a detailed
quote to each entity based on the HTTP Status Code that accurately describes the status. The existing
HTTP specification does an okay job describing status codes, but with Hyperdrive quotes, the process is
much more streamlined and awesome.

## Rules

  * A Hyperdrive response MUST be valid JSON
  * A Hyperdrive response MUST have a key called hyperquote which uses the Quote from the table below based on
    the HTTP Status Code
  * A Hyperdrive response SHOULD use the media type application/vnd.hyperdrive+json

## Example

On a GET request to /prisoners when you are not authorized, you might get the following HAL response:

```
    {
       "hyperquote": "Aren't you a little short for a stormtrooper?"
       "_links": {
            "self": { "href": "/prisoners" },
       }
    }
```

When trying to POST to /locations/mos-eisley-cantina and you use a wrong media type:

```
    {
       "hyperquote": "Hey! We don't serve their kind here.",
       "_links": {
            "self": { "href": "/locations/mos-eisley-cantina" },
       }
    }
```

When requesting an accept for processing, but the processing isn't wrapped up yet, you can send a 202 like this:

```
    {
        "hyperquote": "I want to learn the ways of the Force and become a Jedi like my father.",
        "foo": "bar",
        "_links": {
            "self": { "href": "/foo" }
        }
    }
```

## Messages

Status Code                         | Quote
------------------------------------|-----------------------------------------------------------------------
100	Continue                    | Continue with the operation; you may fire when ready.
101	Switching Protocols         | You've only begun to discover your power! Join me, and I will complete your training! With our combined strength, we can bring order to the galaxy.
102	Processing                  | It'll take a few moments to get the coordinates from the navi-computer.
200 OK                              |
201 Created                         | Oh, I'm afraid the deflector shield will be quite operational when your friends arrive.
202 Accepted                        | I want to learn the ways of the Force and become a Jedi like my father.
203 Non-Authoritative Information   | I have placed information vital to the survival of the Rebellion into the memory systems of this R2 unit.
204 No Content                      | -
205 Reset Content                   | Clear your mind of questions.
206 Partial Content                 | Is there more to this recording?
300 Multiple Choices                | I'm taking Captain Solo and his friends. You can either profit by this or be destroyed. It's your choice, but I warn you not to underestimate my power.
301 Moved Permanently               | Move the ship out of the asteroid field so that we can send a clear transmission.
302 Found                           | Sir, rebel ships are coming into our sector.
303 See Other                       | Move along. Move along.
304 Not Modified                    |
305 Use Proxy                       | I am a member of the Imperial Senate on a diplomatic mission to Alderaan.
307 Temporary Redirect              | Set your course for Alderaan.
400 Bad Request                     | I'm terribly sorry about all this. After all, he's only a Wookiee.
401 Unauthorized                    | Aren't you a little short for a stormtrooper?
402 Payment Required                | I expect to be well paid. I'm in it for the money.
403 Forbidden                       | No, I don't think he likes you at all. No, I don't like you either.
404 Not Found                       | These aren't the droids you're looking for.
405 Method Not Allowed              | Surrender is a perfectly acceptable alternative in extreme circumstances!
406 Not Acceptable                  | Hey! We don't serve their kind here.
407 Proxy Authentication Required   | Hey, you're not permitted in there. It's restricted.
408 Request Timeout                 | Han will have that shield down. We've got to give him more time!
409 Conflict                        | Your thoughts betray you, Father. I feel the good in you, the conflict.
410 Gone                            | Thats what I'm trying to tell you, kid. It ain't there. It's been totally blown away.
411 Length Required                 | How far away is Yoda? Will it take us long to get there?
412 Precondition Failed             | Try not. Do... or do not. There is no try.
413 Request Entity Too Large        | That's no moon. It's a space station.
414 Request-URI Too Long            | I can't. It's too big.
415 Unsupported Media Type          | Sir, I don't know where your ship learned to communicate, but it has the most peculiar dialect.
416 Request Range Not Satisfiable   | At that close range we won't last long against those Star Destroyers!
417 Expectation Failed              | Our cruisers can't repel firepower of that magnitude!
500 Internal Server Error           | Uh, we had a slight weapons malfunction, but uh... everything's perfectly all right now. We're fine. We're all fine here now, thank you. How are you?
501 Not Implemented                 | If only you'd attached my legs, I wouldn't be in this ridiculous position.
502 Bad Gateway                     | You said you wanted to be around when I made a mistake, well, this could be it, sweetheart.
503 Service Unavailable             | If I may say so, sir, I noticed earlier the hyperdrive motivator has been damaged. It's impossible to go to lightspeed.
504 Gateway Timeout                 | Sorry sweetheart. I haven't got time for anything else.
505 HTTP Version Not Support        | Don't blame me. I'm an interpreter. I'm not supposed to know a power socket from a computer terminal.
