# Getting the Source Code

## Install repo

[repo](https://code.google.com/archive/p/git-repo/) is a tool from Google that
works with Gerrit and allows us to manage the multiple git repos that make up
the CORD code base.

If you don't already have `repo` installed, this may be possible with your
system package manager, or using the [instructions on the android source
site](https://source.android.com/source/downloading#installing-repo), or by
using the following commands which download/verify/install it:

```sh
curl -o /tmp/repo https://storage.googleapis.com/git-repo-downloads/repo
echo 'e147f0392686c40cfd7d5e6f332c6ee74c4eab4d24e2694b3b0a0c037bf51dc5  /tmp/repo' | sha256sum -c -
sudo mv /tmp/repo /usr/local/bin/repo
sudo chmod a+x /usr/local/bin/repo
```

## Download CORD repositories

The `cord` repositories are usually checked out to `~/cord` in most of our
examples and deployments:

<pre><code>
mkdir ~/cord && \
cd ~/cord && \
repo init -u https://gerrit.opencord.org/manifest -b {{ book.branch }} && \
repo sync
</code></pre>

> NOTE: `-b` specifies the branch name. Development work goes on in `master,
> and there are also specific stable branches such as `cord-4.0` that can be
> used.

When this is complete, a listing (`ls`) inside this directory should yield
output similar to:

```sh
$ ls
build		component	incubator	onos-apps	orchestration	test
```

## Download patchsets

Once you've downloaded a CORD source tree, you can download patchsets from
Gerrit with the following command:

```
repo download orchestration/xos 1234/3
```

Which downloads a patch for the `xos` git repo, patchset number `1234` and
version `3`.

Also see [Configuring your Development Environment:cord-bootstrap.sh script
](install.md#cord-bootstrap.sh-script) for instructions on downloading
patchsets during a build using the `cord-bootstrap.sh` script.

## Contributing code to CORD

We use [Gerrit](https://gerrit.opencord.org) to manage the CORD code base. For
more information see [Working with
Gerrit](https://wiki.opencord.org/display/CORD/Working+with+Gerrit).

For a general introduction to ways you can participate and contribute to the
project, see [Contributing to
CORD](https://wiki.opencord.org/display/CORD/Contributing+to+CORD).

