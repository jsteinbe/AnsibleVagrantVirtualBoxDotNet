# Ansible/Vagrant DotNet VirtualBox


## What is this?

This is a Vagrant Box that uses Ansible to install ASP Core onto a Ubuntu Linux Virtual Machine. This is meant as
a self-hosting test box for a MVC5/ASP Core to see how well ASP Core works under this new environment and to allow
development.

The server will be setup to host a very simple MVC ASP Core application. The application has a simple Controller
and View. The simple application that is installed will need to be run as you develop (see Improvements below). To
start you can run the following:

## Why?

Historically ASP has been a proprietary software project that runs on Windows boxes exclusively. This has changed
recently and now Asp Core is fully open source and compatible with Linux/Mac Os. I am always interested in new
technology and wanted to see how it worked. I am excited for the challenge and intrigued at the possibilities.
I have always liked the idea of free open source software since any unused machine can be provisioned without
licensing restrictions.

## How do I use it?

You will want to download the Vagrant box via:

```shell
host$ vagrant up
```

That will download the ~440 MB box (which can take a while). You can then provision it with:

```shell
host$ vagrant provision
```

After that you are ready to run the application. Simply:

```shell
host$ vagrant ssh         # Login to Vagrant box
guest$ cd WebApplication  # Go into Web Application Directory
guest$ dotnet run         # Run!
```

To the host, the application will be available at http://localhost:8000 .

Note: If you change the dependencies in project.json you will need to run `dotnet restore`.

## Improvements

Instead of running dotnet run each time a third party program could be installed to make the process automatic.
Something along the lines of grunt would be perfect. Node is fairly large and the goal of this was to make a small
development box. Feel free to modify it to your needs!

## Program Specs

This project was tested with:

Vagrant 1.8.5
VirtualBox 5.1.2 r108956
ansible 2.1.1.0
