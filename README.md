# mkdocs-docker

MkDoks (docker image)
======================

This image will provide you all the funcionality of mkdocs from [mkdocs](www.mkdocs.org).
Some examples of its usage are the follows:

Create a new project
---------------------

This is the command for creating a new project in a local folder.

	docker run -it --rm -v /absolute/path/to/local/folder:/docs marsala/mkdocs new myProject

The flag `--rm` is necessary just for autoremoving the container when execution completes. You have to remove `/absolute/path/to/local/folder`
with the real absolute path to the local folder obviously. A new folder for `myProject` will be created in the path you will provide.

Build the docs
--------------

Let's assume we have just created the new project of the previous command. To build `myProject` project you must move in the project folder
with:

	cd myProject

and use the following command:

	docker run -it --rm -v /absolute/path/to/local/folder:/docs marsala/mkdocs build

this will generate a folder `site` in `/absolute/path/to/local/folder`. If you want generate the site in another folder you can use `/docs/site`
as volume. This is the command for duing it:

	docker run -it --rm -v /absolute/path/to/local/folder:/docs -v /absolute/local/folder/site:/docs/site  marsala/mkdocs build 

Serve a project
----------------

To serve `myProject` project you must move in the project folder with:

	cd myProject

and use the following command:

	docker run -d -v /absolute/path/to/local/folder/myProject:/docs -p 8000:8000 marsala/mkdocs mkdocs serve

You have to remove `/absolute/path/to/local/folder/myProject` with the real absolute path to the local folder of your project. 
If you are using Docker whithin a Virtual Machine, like in __Mac OS X__, __Windows__ or like __boot2docker__ and similar, you have to use this command:

	docker run -d -v /absolute/path/to/local/folder/myProject:/docs -p 8000:8000 marsala/mkdocs mkdocs serve -a 0.0.0.0:8000

  
