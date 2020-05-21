# Papercuts Repo
The default repo for Papercuts


#### 2. Personalize

**Release File**

Edit `Release` file. Modify the items pointed by `<--`

    Origin: Reposi3  <--
    Label: Reposi3   <--
    Suite: stable
    Version: 1.0
    Codename: ios
    Architectures: iphoneos-arm
    Components: main
    Description: Reposi3 - a cydia repo template  <--

**Branding**

Open `index.html` and look at lines 18 and 19.
Change line 18 into your own **brand** and line 19 to have your own URL.
Line2 27-44 contains the list of featured packages.
You can edit those too or remove them totally.

Replace CydiaIcon.png.


**Page Footers**

This data are the links that appear at the bottom of every depication. The data is stored in `repo.xml` at the root folder of your repo.

```xml
<repo>
    <footerlinks>
        <link>
            <name>Follow me on Twitter</name>
            <url>https://twitter.com/reposi3</url>
            <iconclass>glyphicon glyphicon-user</iconclass>
        </link>
        <link>
            <name>I want this depiction template</name>
            <url>https://github.com/supermamon/Reposi3</url>
            <iconclass>glyphicon glyphicon-thumbs-up</iconclass>
        </link>
    </footerlinks>
</repo>
```


#### 3. Your repo is _almost_ ready.
At this point your repo is basically ready to be added into Cydia.
You can also visit your repo's homepage by going to `https://username.github.io/repo/`.
It will come with 2 sample packages, Old Package and New Package.
Each of the packages have a link on this page pointing to their depictions.
Next guide will show you how to assign and customize your depiction pages.

## Adding packages first package to your repo

#### 1. Adding a simple depiction page

Go to the depictions folder and duplicate the folder `com.supermamon.oldpackage`.
Rename the duplicate with the same name as your package name.
There are 2 files inside the folder - `info.xml` and `changelog.xml`.
Update the 2 files with information regading your package.
The tags are pretty much self-explanatory.
Contact [@reposi3](https://twitter.com/reposi3) or [@supermamon](https://twitter.com/supermamon) for questions.

`info.xml`.
```xml
<package>
    <id>com.supermamon.oldpackage</id>
    <name>Old Package</name>
    <version>1.0.0-1</version>
    <compatibility>
        <firmware>
            <miniOS>5.0</miniOS>
            <maxiOS>7.0</maxiOS>
            <otherVersions>unsupported</otherVersions>
            <!--
            for otherVersions, you can put either unsupported or unconfirmed
            -->
        </firmware>
    </compatibility>
    <dependencies></dependencies>
    <descriptionlist>
        <description>This is an old package. Requires iOS 7 and below..</description>
    </descriptionlist>
    <screenshots></screenshots>
    <changelog>
        <change>Initial release</change>
    </changelog>
    <links></links>
</package>
```

`changelog.xml`.
```xml
<changelog>
    <changes>
        <version>1.0.0-1</version>
        <change>Initial release</change>
    </changes>
</changelog>
```


#### 2. Link the depiction page your tweak's `control` file

You can add the depictions url at the end of your package's `control` file before compiling it.
The depiction line should look like this:

```text
Depiction: https://username.github.io/repo/depictions/?p=[idhere]
```

Replace `[idhere]` with your actual package name.

```text
Depiction: https://username.github.io/repo/depictions/?p=com.supermamon.oldpackage
```

#### 3. Rebuilding the `Packages` file

With your updated `control` file, build your tweak.
Store the resulting `.deb.` file into the `/debs/` folder of your repo.
Build your `Packages` file and compress with `bzip2`.

```sh
user:~/ $ cd repo
user:~/repo $ dpkg-scanpackages -m ./debs > Packages
user:~/repo $ bzip2 Packages
```

_Windows users, see [dpkg-scanpackages-py](https://github.com/supermamon/dpkg-scanpackages-py) or [scanpkg](https://github.com/mstg/scanpkg)._

#### 5. Cydia at last!

If you haven't done yet, go ahead and add your repo to Cydia.
You should now be able to install your tweak into your own repo.

### Cleanup

Just a cleanup step, remove the debs that came with this template and re-run the commands on step 3. You can keep the sample depictions for reference by they're not needed for your repo.
