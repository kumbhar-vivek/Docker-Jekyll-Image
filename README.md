# Docker Jekyll Image


How to use the image

- Run the below command where you have your Dockerfile.

```
docker build -t 'your_docker_image' .
```

Example:
`docker build --rm -t kumbhar-vivek .`

- Run the command at the root of your website directory

```
docker run --rm -v $(pwd):/home/jekyll -p 80:80 'your_docker_image' jekyll new <site_name>
```
Example:
`docker run --rm -v $(pwd):/home/jekyll -p 80:80 kumbhar-vivek jekyll new blog`

- If you are using existing Jekyll site, you need to have Gemfile at the root with the following:

```
# ----- copy text as is -----

source "https://rubygems.org"

# This ensures the proper Jekyll version is running.
# If you want to use GitHub Pages, comment the line "gem "jekyll""
gem "jekyll", "3.5.2"

# You can add a Jekyll theme here.
# gem "minima", "~> 2.0"

# If you have any plugins, put them here!
group :jekyll_plugins do
   gem "jekyll-feed", "~> 0.6"
end

# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]

# ----- end of file -----
```

- To **start** jekyll docker site

```
docker run --rm -v $(pwd):/home/jekyll -p 80:80 'your_docker_image' jekyll serve
```

Example:
`docker run --rm -v $(pwd):/home/jekyll -p 80:80 kumbhar-vivek jekyll serve`

- To **clean** jekyll docker built site

```
docker run --rm -v $(pwd):/home/jekyll -p 80:80 'your_docker_image' jekyll clean
```

Example:
`docker run --rm -v $(pwd):/home/jekyll -p 80:80 kumbhar-vivek jekyll clean`

##### NOTE:

- You need to add the below mentioned text to your *_config.yml* file under the root of your Jekyll site.

```
host: 0.0.0.0
port: 80
```
