(data-storage)=
# Data Storage

The Fornax Science Console offers both private and shared data storage options.
Users are also welcome to "bring your own storage".
Basic specifications and usage tips are described below.

## Private Home Directory

The user's home directory (`~/`) is intended for most data storage use cases, including notebook, code, and data files.
It uses a standard Unix filesystem (POSIX).

By default, the home directory has a 200 GB limit.
To request an increase, please contact the [](#helpdesk).

It is backed up daily at midnight EST, and the backups are retained for 1 day.

```{tip}
All users will see the following directories in their home directory: `fornax-notebooks`, `s3-storage`, and `shared-storage`.
Those do not actually live in the home directory (they are mounted or symlinked in), and a user intending to save data to their home directory should **not** save it inside any of those directories.
```

(private-s3)=
## Private S3 Bucket

All users have access to a private {term}`AWS S3<s3>` bucket, which is mounted in to the home directory at `~/s3-storage`.
It is best suited for infrequently accessed data, such as archival storage of pipeline outputs (catalogs, spectra, images, etc.) needed for reproducibility.

There is no limit on the amount of data a user can store here, other than their own credit allotment.

Data stored here are not backed up, but AWS guarantees very high reliability (>>99%).
Users can expect that data stored here will be available.
But once the user deletes the data, it is non-recoverable.

Please be aware that `~/s3-storage` doesn't behave exactly like a traditional filesystem.
In particular, it is inefficient for repeated access of many small files.
When storing multiple files, consider using `tar` to collect them into a single file before saving to `~/s3-storage`.

(temporary-storage)=
## Private Temporary Storage

The directory `/scratch` is intended for short-term storage of large volumes of data (TB scale).
For example, it's a good place to write large analysis outputs.
(Then move to [S3](#private-s3) for long-term storage.)
It uses a standard Unix filesystem (POSIX).

By default, the directory exists but is limited to 1 GB.
Users can contact the [](#helpdesk) to request additional space.

## Shared Storage

The directory `~/shared-storage` is a shared area that is visible to every Fornax user.
It uses a standard Unix filesystem (POSIX).

Users wishing to share data or code with collaborators should make a new directory called `~/shared-storage/users/$USER` (where `$USER` is their username) and save the files there.

## Bring Your Own Storage

Users are also welcome to "bring your own storage".
This can be anything that is accessible through an API.
Examples include Google Drive, Box, AWS S3 buckets, and Google Cloud Storage buckets.
