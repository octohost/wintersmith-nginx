wintersmith-nginx
==================

You don't need to use node to serve a [Wintersmith](http://wintersmith.io/) site - you can just compile the files and use anything - `wintersmith build`

This is a container that has node and Wintersmith available, to compile and install the static site, that nginx serves.

You can use our container: `docker pull octohost/wintersmith-nginx`

Or you can build your own:

```
docker build -t your-name-here/wintersmith-nginx .
docker push your-name-here/wintersmith-nginx
```

After this - just add this Dockerfile to your Harp repo:

```
FROM octohost/wintersmith-nginx

WORKDIR /srv/www

ADD . /srv/www/
RUN wintersmith build

EXPOSE 80

CMD nginx
```

Push it to your docker server - and your server will use 4-6MB of RAM.

To see an example working repo, [take a look here](https://github.com/octohost/wintersmith).