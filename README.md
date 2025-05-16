# QT Docker

This repository was inspired by [state-of-the-art/qt6-docker](https://github.com/state-of-the-art/qt6-docker). I found that, at time of writing,
I could not easily modify the Dockerfiles within that repository because `docker build` commands
against them are breaking. It appears that the outside world, in various ways, has moved on
from the expectations required by those dockerfiles, but the archived images are still useful in
building and deploying QT projects as appimages.

I also felt some modifications were in order. Namely...

- state-of-the-art's repository makes efforts to remove the aqtinstall package from the container.
  I think that was stupid so I've added it back in. It seems quite obvious to me that a QT developer
  would be interested in having access to aqt within their container since it was, personally, the
  first utility I attempted to reach for to pull in missing QT modules my project needed.
- It also does not pre-install any additional, and quite useful, QT modules. Since these containers
  are development containers I thought that was a bit odd not to do that.

The directory structure of this repository mirrors that of the state-of-the-art's, and the versioning
scheme of the underlying containers is `<QT-version>-<My Version>`. Archived images for these releases
are available from DockerHub.

"My Version", in the above statement, refers to the additional modifications I make, and follows a scheme
of `major-release.feature.fix`. The "feature" and "fix" fields will be updated if I add any new QT modules
to the container or fix a bug.

Full support for all versions of QT is not planned at this time. If, like me, you found state-of-the-art's
repository and were shocked to find the containers therein included no QT modules or the very convenient
program, aqtinstall, used for their installation, then you should be able to look at the Dockerfiles under
these subdirectories and easily modify them for your needs.

Also, despite my criticisms of state-of-the-art's implementation, I thank him for creating what he did.
It was a useful starting point.
