# Vendoring dependencies

```bash
# Run this from project root directory
go mod vendor -v

# Download the dependencies that are not available in Debian, are unlikely to
# ever be in Debian as independent separate packages, and thus need to be
# vendored in this package
MODULES=(
  "github.com/gohxs/readline"
  "github.com/jeandeaual/go-locale"
  "github.com/kenshaw/colors"
  "github.com/kenshaw/rasterm"
  "github.com/yookoala/realpath"
)

# Loop through each module
for MODULE in "${MODULES[@]}"
do
  mkdir -p debian/vendor/"$MODULE"
  cp --archive --update --verbose vendor/"$MODULE"/* debian/vendor/"$MODULE"/
done

# Remove extra binary files not needed for building
rm -f debian/vendor/github.com/kenshaw/rasterm/screenshot.png
```
