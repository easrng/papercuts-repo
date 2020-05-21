# Papercuts Repo
The default repo for Papercuts

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
