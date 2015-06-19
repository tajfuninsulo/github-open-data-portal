*This article is translated from http://manzanamecanica.org/2013/04/como_publicar_open_data_con_github_una_guia_paso_a_paso.html**

Many organizations have little resources for "extra" activities, such as create their own Open Data portals. For example, small municipalities and towns do not have the time, personel or budget to expose datasets that could be useful and relevant for the community. In order to alleviate this situation, I present a simple method to publish Open Data using Github.

##What is GitHub?

Github is a company that offers hosting for software projects, based on the [GIT](http://en.wikipedia.org/wiki/Git_(software)) version control system. The service is free for Open Source projects. In general, there is no problem for projects smaller than 1GB in size, which is more than enough to host a large amount of datasets.

##If it is for software, why using it for data?

For the sake of this example, data and software are the same :-) GIT provides a versioning system for files that makes it easy to add and keep track of changes in datasets. Also, GitHub provides a feature called _forks_, where other users can replicate an existing repository. This copy can be modified and it is independent of the original version. Eventually, it is possible to apply the changes to the original repository (e.g., a patch fixing a bug). Github makes this proces easy, by providing _pull requests_, i.e., it is possible to ask the owner of the original repository to accept and adopt the changes made in the fork. Since GIT is a versioning control system, any change will be recorded and can be seen in the historical logs. All of the above makes GIT a nice system to publish and keep track of Open Data.

##Ok, you convinced me, what's next?

First, it is necessary to got to http://github.com and create an account if you don't have one already. Second, it is highly recommended to download the Github client (only for Mac and Windows), which provides a nice GUI.

![Download github client](https://raw.github.com/alangrafu/github-open-data-portal/images/images/od_github1.png)

##Create a repository

In the client, we can create a new repository. For this example I will call it `github-open-data-portal`:

![Create new repository 1](https://raw.github.com/alangrafu/github-open-data-portal/images/images/od_github2.png)

![Create new repository 2](https://raw.github.com/alangrafu/github-open-data-portal/images/images/od_github3.png)

Inside the repository I'll create a new folder called `data`:

![Create directory data](https://raw.github.com/alangrafu/github-open-data-portal/images/images/od_github4.png)

##Add datasets

For this example, I simply took some datasets from http://datos.gob.cl: Datasets 3877 (http://datos.gob.cl/datasets/ver/3877) and Dataset 3870 (http://datos.gob.cl/datasets/ver/3870). I took these files and put them in the `data` directory I just created.

In the GitHub client, we can see that the files have been detected

![Adding datasets](https://raw.github.com/alangrafu/github-open-data-portal/images/images/od_github5.png)

In order to upload them, we need to do a `commit`, that is, we store the current state of the repository: The new files are selected by default and we only need to describe these new additions to the repository:

![Doing commit](https://raw.github.com/alangrafu/github-open-data-portal/images/images/od_github6.png)

Finally, we press on `commit & sync`, and the client will upload the changes to GitHub

![Doing commit 2](https://raw.github.com/alangrafu/github-open-data-portal/images/images/od_github7.png)

##Modifying datasets

In the case of the file `Transporte.csv`, the last 3 lines are garbage and we want to remove them. We open this file with a text editor and remove the last 3 lines.

![Editing dataset](https://raw.github.com/alangrafu/github-open-data-portal/images/images/od_github8.png)

After saving the file, we can go again to the GitHub cliente and find that it detected the changes made to `Transporte.csv`. The lines in red indicate that they have been removed. Green lines may indicate lines that has been added.

![Saving cambios](https://raw.github.com/alangrafu/github-open-data-portal/images/images/od_github9.png)

We create a new commit, this time indicating that we have remove some lines from a dataset

Everytime we add or modify datasets, we need to create a new commit and sync with the github repository, to upload the changes. GitHub will keep the whole log of changes, files added/removed, who made each change, etc.

##License

It is important to make *very* clear under which legal conditions are we publishing data. A simple and reasonable way of doing that is to maintain a `LICENSE` file in the root of the repository, that describe in which terms this data can be used. In our example, the datasets used were taken from [Datos.gob.cl](http://datos.gob.cl), so we will use their same license [CC-3.0-BY](http://creativecommons.org/licenses/by/3.0/cl/).

# How can we access the data?

People can now access our data by going to our github repository (in this example https://github.com/alangrafu/github-open-data-portal). From there, it is possible to download each dataset, as well as download the whole collection of datasets as a [.zip archive](https://github.com/alangrafu/github-open-data-portal/archive/master.zip) that is generated by github automatically. Finally, it is also possible for others to [clone](https://help.github.com/articles/fork-a-repo) the repository, thus obtaining all the datasets including older versions.

#Demo

In order to simplify the process of showing the content of a repository in other sites (e.g., the official page of an organization), I wrote a small application that uses the Github's API to list all the datasets available in folder `data` of a repository. To make this app work, you need to copy and adapt the following code:

```
<div id="datasets"></div>
  <script src="https://raw.github.com/alangrafu/github-open-data-portal/master/app/js/jquery.min.js"></script>
  <script src='https://raw.github.com/alangrafu/github-open-data-portal/master/app/js/main.js'></script>
  <script>
  GDP.config.userName = 'alangrafu'; //User name
  GDP.config.projectName = 'github-open-data-portal'; //Repository name
  GDP.render("#datasets");
</script>
```

An example of the app can be seen at [http://graves.cl/example-github-opendata](http://graves.cl/example-github-opendata)

##Conclusion

It is easy to publish data on the Web. Using the method described above is it even simpler to publish datasets in 10 minutes or less. You just need to follow these steps:


* Create an account in github (if you don't have one) and download the github cliente
* Create a repository (or fork the one in the example)
* Add all the datasets you want in the `data` folder
* Add de right license in the `LICENSE` file
* Eventually you can use the script shown in the demo to list all the datasets available in other webpages
