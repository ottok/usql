# Vendoring dependencies

```bash
# Run this from project root directory
go mod vendor

# Download only the dependencies that are not yet available in Debian
MODULES=(
  "github.com/gohxs/readline"
  "github.com/jeandeaual/go-locale"
  "github.com/kenshaw/colors"
  "github.com/kenshaw/rasterm"
  "github.com/xo/dburl"
  "github.com/yookoala/realpath"
)

# Loop through each module
for MODULE in "${MODULES[@]}"
do
  mkdir -p debian/vendor/"$MODULE"
  cp --archive --update --verbose vendor/"$MODULE"/* debian/vendor/"$MODULE"/
done
```
