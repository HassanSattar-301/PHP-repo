
# FileWrapper

Wraps file with mime-type and filename to be sent as part of an HTTP request.

## Methods

| Name | Type | Description |
|  --- | --- | --- |
| `getFilename()` | `?string` | Get name of the file to be used in the upload data. |
| `getMimeType()` | `?string` | Get the mime-type to be sent with the file. |

## Usage Example

```php
// creating a file wrapper instance
$file = FileWrapper::createFromPath('path/to/file.txt', 'w+', 'my_file');

// send file in API request
$client->getExampleController()->sendFile($file);

// getting file from API response
$file = $client->getExampleController()->getFile();

// printing file information
echo $file;

// printing file content
echo ApiHelper::serialize($file);
```

