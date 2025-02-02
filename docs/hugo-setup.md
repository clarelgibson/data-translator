# Steps to set up my Hugo site

1. Create new repository in Github
2. Clone repository to local directory

    `git clone git@github.com:clarelgibson/data-translator.git`

3. Create a new Hugo site in the cloned directory (using yaml format for config files and front matter intead of the default toml format)

    `hugo new site . --force --format yaml`