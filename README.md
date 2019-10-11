# ant-code-snipphets

# target

```ant
<target name="targetName">
    ...
<target/>
```

# Make zip file

```ant
<target name="package">
    <mkdir dir="output" />
    <zip destfile="output/filename.zip" >
        <fileset dir=".">
            <include name="bin/**"/>
            <include name="classes/**"/>
            <include name="input/*"/>
            <exclude name="input/*.*"/>
            <include name="*.properties"/>
        </fileset>
        <fileset dir=".">
            <include name="dirname/3rdpartylib/**"/>
            <include name="dirname/batch/**"/>
        </fileset>
    </zip>
</target>
  ```