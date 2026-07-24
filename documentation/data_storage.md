(data-storage)=
# Data Storage

The Fornax Science Console offers both private and shared data storage options.
Users are also welcome to "bring your own storage".
Basic specifications and usage tips are described below.

## Private Storage

To cover a range of use cases, Fornax offers three options for private storage.
They are summarized in the table below, with more detail in the sections that follow.

```{list-table} Overview of private storage options
:header-rows: 1

* - Storage Type
  - Max Size
  - Duration
  - Filesystem
  - Typical Use Case
* - [Home directory](#home-directory)
  - 200 GB
  - any
  - POSIX (standard Unix)
  - most daily needs
* - [S3 bucket](#private-s3)
  - limited only by user's credits
  - any
  - mounted AWS S3 bucket
  - long-term storage, especially for large data
* - [Scratch space](#temporary-storage)
  - 3 TB
  - up to 90 days
  - POSIX (standard Unix)
  - short-term working space for large data
```

For the cost (in credits) of each option, see [](change-controlled-documents/user-resource-allotments-and-costs.md).

(home-directory)=
### Home Directory

The user's home directory (`~/`) is private and intended for most data storage use cases, including notebook, code, and data files.
It uses a standard Unix filesystem (POSIX).

By default, the home directory has a 200 GB limit.
To request an increase, please contact the [](#helpdesk).

It is backed up daily at midnight EST, and the backups are retained for 1 day.

```{tip}
All users will see the following directories in their home directory: `fornax-notebooks`, `s3-storage`, and `shared-storage`.
Those do not actually live in the home directory (they are mounted or symlinked in), and a user intending to save data to their home directory should **not** save it inside any of those directories.
```

(private-s3)=
### S3 Bucket

All users have access to a private {term}`AWS S3<s3>` bucket, which is mounted into the home directory at `~/s3-storage`.
It is best suited for infrequently accessed data, such as archival storage of pipeline outputs (catalogs, spectra, images, etc.) needed for reproducibility.

There is no limit on the amount of data a user can store here, other than their own credit allotment.

Data stored here are not backed up, but AWS guarantees very high reliability (>>99%).
Users can expect that data stored here will be available.
But once the user deletes the data, it is non-recoverable.

Please be aware that `~/s3-storage` doesn't behave exactly like a traditional filesystem.
In particular, it is inefficient for repeated access of many small files.
When storing multiple files, consider using `tar` to collect them into a single file before saving to `~/s3-storage`.

(temporary-storage)=
### Temporary Scratch Space

The directory `/scratch` is private and uses a standard Unix filesystem (POSIX).
It's intended as a working area for large data in cases where your [S3 storage](#private-s3) isn't performant enough, and your [home directory](#home-directory) is too small.
For example, if your analysis writes many files and you find that writing to S3 is too slow, write to `/scratch` and then move the data you want to keep long-term over to S3 after your analysis is complete.

This storage is not backed up.
The storage system is highly reliable and should not lose data due to system error, but cannot protect against user error.
Lost data are not recoverable.

By default, `/scratch` exists but is limited to 1 GB.
You can expand it up to 3 TB for a maximum of 90 days at a time.
To manage this space, go to the [](#forsc-Dashboard) and click `Storage → Scratch`.
Details are in the drop-down below.

````{note} How to manage scratch storage space
:class: dropdown

On the [](#forsc-Dashboard), click `Storage → Scratch` to get to the Scratch Storage management page.

```{figure} ../_static/forsc_dashboard_scratch_default.png
:alt: Scratch Storage management page on the Fornax Dashboard, showing the default configuration (user has not created scratch space) and a Request Storage button.

Scratch Storage Dashboard page with a button to request storage
```

Create scratch space (expand beyond the default 1 GB)
: Go to the Scratch Storage Dashboard page and complete the following steps.
  The only limit on how many times you can do this is the number of credits you have available.

  1. Click `Request Storage`.
  2. Choose a size between 500 GB and 3 TB.
     (You will be able to increase this later.)
  3. Choose an expiration date of up to 60 days in the future.
     (You will be able to increase or decrease this later.)
  4. The total charge in credits will be displayed, along with the number of credits you currently have.
     Be sure to leave yourself enough credits to run servers and anything else you want to do.
  5. Click `Submit Request`.
     If you have enough credits to cover the total, your scratch space will be expanded.
     This can take a few minutes.
     When it's complete, you'll receive a message via the [Forum](#intro-forum), and your Dashboard page will look similar to the screenshot below.

```{figure} ../_static/forsc_dashboard_scratch_created.png
:alt: Scratch Storage management page on the Fornax Dashboard, showing the configuration of the user's current scratch space (storage size, created date, expiration date, and days remaining) and buttons to modify or release the storage space.

Scratch Storage Dashboard page after space has been created
```

Access scratch space
: [Start a server session](#start-server-session) and navigate to the `/scratch` directory.
  Note that you won't be able to see `/scratch` in the UI because it doesn't show up in your home directory.
You can also access it by opening a {term}`terminal` and entering `ls /scratch`.

Change scratch size or expiration date
: Go to the Scratch Storage Dashboard page and click `Modify Allocation`.
  From there you will be able to:

  - Increase the storage size up to a maximum of 3 TB.
    (Can't decrease the size.)
  - Increase or decrease the expiration date.
    It can be increased to up to 90 days total from the date it was initially expanded.

Release (delete) scratch space
: Release the scratch space as soon as you're done with it so your credits stop being charged.
  First, [shut down your server](#shutdown-server).
  Then go to the Scratch Storage Dashboard page and click `Release Storage`.
  You will be asked to confirm.

  When the space is released, **all files** in `~/scratch` will be **permanently deleted** and the directory will be resized back to 1 GB.
  The process can take up to 20 minutes or more to complete.
  You will receive a message via the [Forum](#intro-forum) when it's done.

  If you don't manually release the space, it will be automatically released on the expiration date you chose when creating or updating the space.
````

```{danger} Warning: Data is permanently deleted when scratch is released or expires
**All files** in `~/scratch` will be **permanently deleted** when the expanded scratch space is manually released through the Dashboard or the expiration date is reached, whichever comes first.
The data are non-recoverable.

You will receive a message via the [Forum](#intro-forum) halfway between the creation and expiration dates, and again 3 days and 1 day before the expiration date.
The messages will include instructions for copying data out of `/scratch` to S3 or another permanent location.
```

## Shared Storage

The directory `~/shared-storage` is a shared area that is visible to every Fornax user.
It uses a standard Unix filesystem (POSIX).

Users wishing to share data or code with collaborators should make a new directory called `~/shared-storage/users/$USER` (where `$USER` is their username) and save the files there.

## Bring Your Own Storage

Users are also welcome to "bring your own storage".
This can be anything that is accessible through an API.
Examples include Google Drive, Box, AWS S3 buckets, and Google Cloud Storage buckets.
