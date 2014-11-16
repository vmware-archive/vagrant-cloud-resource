# Vagrant Cloud Resource

Automates creation of box versions in [Vagrant Cloud](https://vagrantcloud.com).


## Source Configuration

* `access_token`: *Required.* The access token.

* `username`: *Required.* The user that owns the box.

* `box`: *Required.* The name of the box.

* `provider`: *Required.* The provider of the box.


## Behavior

### `check`: Check for new versions of the box's provider.

Queries the Vagrant Cloud API for new versions of the box. If no version is
given, the current version is returned. Otherwise, all versions after the
given version are returned.


### `in`: Fetches the box.

Downloads the .box file for the box's provider and version. If no version,
the current version is fetched.

Returns the box version as the resource's version.

Places the following files in the destination:

* `version`: The version number of the box.

* `url`: The URL of the .box. (Be sure to follow redirects.)

* `box`: The downloaded .box file, if `download` is enabled.

#### Parameters

* `download`: *Optional.* Download the .box file.


### `out`: Publish a version of the box.

Creates a version of the box's provider. At least one of `url` or `release`
must be provided.

#### Parameters

* `number`: *Required.* Path to a file containing the version number.

* `description`: *Optional.* Path to a file containing the description of the
  version.

* `url`: *Optional.* Path to a file containing the URL to the .box.

* `release`: *Optional. Default `false`.* Release the version.
