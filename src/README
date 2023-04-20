Logger for accumulating records in memory
=========================================

This strange logger can be used in modules for systems where there is no built-in PSR-3 logger or in API request
handlers, when along with the response to the request you need to give debugging information about the request
processing process.

A typical scheme of working with a logger:

````php
$logger = new ProcessLogger(...);

$logger->info(...);

..
$logger->info(...);

...

$logger->debug(...);

...

$logger->info(...);

...

if($logger instanceof ProcessLogger) $text = $logger->flush();

````

You can upload the accumulated records and save them to a file, for example, in the `__destruct` method of the main
class of your module. Or in the method of forming a response to an API request.

The only non-standard method of the logger is 'flush()', which merges all records into a string, using the line break
character to merge them, and produces text ready to be written to a file.
