# All services and methods

[!KEYREF objstorage-name] The HTTP API provides the following services:

| Service | Description |
| ------- | --------- |
| [Bucket](bucket.md) | Performs bucket management. |
| [Object](object.md) | Performs object management. |
| [Multipart upload](multipart.md) | Controls uploading of large objects. |

## Supported methods {#operations-list}

### Bucket service

| Method | Description |
| ----- | ----- |
| [create](bucket/create.md) | Creates a bucket. |
| [getMeta](bucket/getmeta.md) | Checks the existence of a bucket and access to it. |
| [listObjects](bucket/listobjects.md) | Returns a list of bucket objects. |
| [listBuckets](bucket/list.md) | Returns a list of buckets. |
| [deleteBucket](bucket/delete.md) | Deletes a bucket. |

### Object service

| Method | Description |
| ----- | ----- |
| [upload](object/upload.md) | Uploads an object to [!KEYREF objstorage-name]. |
| [get](object/get.md) | Retrieves an object from [!KEYREF objstorage-name]. |
| [getObjectMeta](object/getobjectmeta.md) | Retrieves object metadata. |
| [delete](object/delete.md) | Deletes an object. |
| [deleteMultipleObjecs](object/deletemultipleobjects.md) | Deletes objects based on a list. |

### Multipart Upload service

| Method | Description |
| ----- | ----- |
| [startUpload](multipart/startupload.md) | Starts multipart upload. |
| [uploadPart](multipart/uploadpart.md) | Uploads a part of an object. |
| [listParts](multipart/listparts.md) | Displays a list of uploaded parts. |
| [abortUpload](multipart/abortupload.md) | Aborts multipart upload. |
| [completeUpload](multipart/completeupload.md) | Completes multipart upload. |
| [listUploads](multipart/listuploads.md) | Returns a list of incomplete uploads. |

### Static Website Hosting service

| Method | Description |
| ----- | ----- |
| [upload](hosting/upload.md) | Uploads a bucket's configuration for static website hosting to [!KEYREF objstorage-name]. |
| [get](hosting/get.md) | Returns a bucket's configuration for static website hosting from [!KEYREF objstorage-name]. |
| [delete](hosting/delete.md) | Deletes a bucket's configuration for static website hosting. |

## See also

- [[!TITLE]](../../s3/index.md)
- [[!TITLE]](../../instruments/index.md)

