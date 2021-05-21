# Installation

First install [graphviz](http://graphviz.org/Download.php) for your OS, then

	go get github.com/delabroj/graphpkg

# Usage

To graph the dependencies of the net package:

	graphpkg net

# Filtering

graphpkg can also filter out packages that do not match the supplied regex, this may improve the readability of some graphs by excluding the std library:

	graphpkg -match 'launchpad.net' launchpad.net/goamz/s3

# Filtering Parents

Filter out packages whose parents do not match the supplied regex:

	graphpkg -parent-match 'goamz/s3' launchpad.net/goamz/s3

# Vendor

Look for packages in the indicated vendor folder first:

	graphpkg -vendor 'launchpad.net/goamz/s3/vendor' launchpad.net/goamz/s3

# Prefix-trim

Remove the given string from the beginning of package names before graphing.

	graphpkg -prefix-trim 'launchpad.net/goamz' launchpad.net/goamz/s3

# Output

By default graphpkg shows the graph in your browser, you can choose to print the resulting svg to standard output:

	graphpkg -stdout -match 'github.com' github.com/davecheney/graphpkg

# Examples

## Show all the direct, third-party dependencies of goamz/s3 and its imported subpackages

	graphpkg -match '\.' -parent-match 'goamz/s3' github.com/goamz/s3
