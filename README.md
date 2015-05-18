android-template
================

A barebones android project template. Useful if you want a quick
android project without any dependencies or source files.

I use it with the following zsh alias:

```bash
android-project () {
  name=$1
  application_id=$2

  if [ -z "$name" ]; then
    echo "Usage: android-project <folder_name> <application_id>"
    return
  fi

  if [ -z "$application_id" ]; then
    echo "Usage: android-project <folder_name> <application_id>"
    return
  fi

  echo "Cloning template into $name"
  git clone https://github.com/madisp/android-template.git $name
  pushd $name

  echo "Cleaning git artifacts"
  rm -rf .git
  rm **/.gitkeep
  rm LICENSE
  rm README.md

  echo "Replacing package name with $application_id"
  # gor is goreplace, you can use sed or something else here
  gor 'com.madisp.template' -r "$application_id"

  echo "All done"
  popd
}
```
