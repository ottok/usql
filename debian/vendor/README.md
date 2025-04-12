# Vendoring dependencies

```bash
# Run this from project root directory
go mod vendor

# Download only the dependencies that are not yet available in Debian
MODULES=(
  "github.com/go-git/go-billy/v5"
  "github.com/gohxs/readline"
  "github.com/google/goexpect"
  "github.com/google/goterm"
  "github.com/jeandeaual/go-locale"
  "github.com/kenshaw/colors"
  "github.com/kenshaw/rasterm"
  "github.com/mattn/go-sixel"
  "github.com/nathan-fiscaletti/consolesize-go"
  "github.com/soniakeys/quant"
  "github.com/xo/dburl"
  "github.com/xo/tblfmt"
  "github.com/yookoala/realpath"
)

# Loop through each module
for MODULE in "${MODULES[@]}"
do
  mkdir -p debian/vendor/"$MODULE"
  cp --archive --update --verbose vendor/"$MODULE"/* debian/vendor/"$MODULE"/
done
```
