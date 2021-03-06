# ontology-starter-kit

Initialize a GitHub repo for managing your ontology the OBO Library way!

For more details, see

 * [Creating an ontology project](https://douroucouli.wordpress.com/2015/12/16/creating-an-ontology-project-an-update/)
 * [OBO Workshop Slides](https://docs.google.com/presentation/d/1JPAaDl6Nitxet9NVqWI30eIygcerYAjdMIGmxbRtIn0/edit?usp=sharing)

# Requirements

Any Linux or OS X command line environment should work. You will minimally need the following installed:

 * perl
 * git
 * java8

The kit will also try to make an initial ontology release, unless you tell it not to. It will attempt to download the following dependencies:

 * robot
 * owltools

# Protocol

## Download this starter package

It's recommended you get a release version: https://github.com/INCATools/ontology-starter-kit/releases

## Initialize

First you must be in the root level of the starter kit

    cd ontology-starter-kit

The `seed-my-ontology-repo.pl` command does everything you need. For help:

    ./seed-my-ontology-repo.pl  -h

An example:

    ./seed-my-ontology-repo.pl   -d po ro pato -u cmungall -t "Triffid Behavior ontology" triffo

You can list any set of dependencies you like after "-d". However, these must be the official OBO ontology IDs. See http://obofoundry.org for details.

This will create your starter files in
`target/triffid-behavior-ontology`. It will also prepare an initial
release and initialize a local repository (not yet pushed to GitHub).

You can customize at this stage, or (recommended) after making an initial push to github

## Push to GitHub

The starter kit will automatically initialize a git project, add all files and commit.

You will need to create a project on GitHub.

 1. Go to: https://github.com/new
 2. The owner MUST be the org you selected with the `-u` option. The MUST be the one you set with `-t`.
 3. Do not initialize with a README (you already have one)
 4. Click Create
 5. See the section under "…or push an existing repository from the command line"

Follow the instructions there. E.g.

```
cd target/triffid-behavior-ontology
git remote add origin git@github.com:cmungall/triffid-behavior-ontology.git
git push -u origin master
```

Note: you can now mv `target/triffid-behavior-ontology` to anywhere you like in your home directory. Or you can do a fresh checkout from github

## Edit and release cycle

In your repo you will see a README-editors.md file that has been customized for your project. Follow these instructions.

Generally the cycle is to:

 - branch
 - the edit the edit.owl file
 - make test
 - git commit
 - git push

To make a release

`make prepare_release`

Note that any make step can be preceded by run.sh if you have Docker installed

## OBO Library metadata

The assumption here is that you are ahdering to OBO principles and
want to eventually submit to OBO. Your repo will contain stub metadata
files to help you do this.

You can create pull requests for your ontology on the OBO Foundry. See the `src/metadata` file for more details.

For more documentation, see http://obofoundry.org

## Additional

You will want to also:

 * enable travis
 * enable zenodo (optional)

See the README-editors.md file that has been generated for your project.

## Troubleshooting.

If you have issues, file them here: https://github.com/INCATools/ontology-starter-kit/issues

Some things to check:

 * if something goes wrong you can try again. You may want to remove the `target` dir, or use the `-c` option
 * make sure your ontid has no spaces
 * if your title has spaces, enclose it in quotes


## Customizing

You will likely want to customize the build process, and of course to edit the ontology.

The main thing you will want to do is to modify the seeds that are
used to build the imports. The ones that are there are just examples,
edit them as you like. See the ROBOT docs and the [OBO
Tutorial](https://github.com/jamesaoverton/obo-tutorial) for more
info.

## Adapting an existing ontology repo

The OSK is designed for creating a new repo for a new ontology. It can still be used to help figure out how to migrate an existing github repository to the OSK structure. There are different ways to do this.

 * Manually compare your ontology against the [template](https://github.com/INCATools/ontology-starter-kit/tree/master/template) folder and make necessary adjustments
 * Run osk as if creating a new repo. Manually compare this with your existing repo and use `git mv` to rearrange, and adding any missing files by copying them across and doing a `git add`
 * Create a new repo de novo and abandon your existing one, using github issue mover to move tickets across.
 
 Obviously the second method is not ideal as you lose your github history. Note even with `git mv` history tracking becomes harder

## More documentation

You will find additional documentation in the src/ontology/README-editors.md file in your repo
