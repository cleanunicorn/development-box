Add the box to your local installation of **vagrant**

```
vagrant box add hydrarulz/laravel-development hydrarulz-laravel-development.box
```

Then go into your Laravel installation directory and copy the sample **Vagrantfile**

```
cp Vagrantfile /into/your/laravel/folder/
```

Now you are set to start up your machine. This will create the machine based on the **Vagrantfile** you provided in the current directory and will share the current directory in the machine also.
Make sure this is the root directory of your Laravel app.

```
vagrant up
```

After all is setup you can connect to your machine.

```
vagrant ssh
```

Go to your shared folder in the virtual machine and start the Laravel application

```
cd /vagrant
./artisan serve --host=0.0.0.0
```

You should be able to see the result on your host machine by browsing to `http://localhost:8000`

When you started the vagrant machine with `vagrant up` it used the Vagrantfile from your current directory and it automatically shares your directory in the `/vagrant` directory in the virtual machine
