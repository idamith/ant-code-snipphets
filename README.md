# Ant code snipphets

# target

```ant
<target name="targetName">
    ...
<target/>
```

# Call one target from another

```ant
<target name="targetName" depends="targetOne, targetTwo">
    ...
    <antcall target="anotherTarget" />
    ...
<target/>
```

# Print something

```ant
<target name="targetName">
    ...
    <echo>Something</echo>
    ...
<target/>
```

# Use property files

```ant
<target name="setProperties">
    <property file="build.properties" />
    <property file="conf/another.properties" />
    <echo>${property.name}</echo>
</target>
```

# Make a zip file

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

# Compile Java code

```ant
<target name="compile" depends="setClasspath, createdirs">
    ...
    <javac srcdir="src" destdir="${classes.dir}" debug="on" deprecation="on" optimize="on" memoryMaximumSize="300m" fork="yes" target="1.8" source="1.8">
        <classpath refid="project.class.path" />
        <exclude name="**/some-dir/**" />
        <exclude name="META-INF/**" />
    </javac>
</target>
```

# Build path

```ant
<target name="setClasspath" depends="setProperties">
    <path id="project.class.path">
        <pathelement path="${classes.dir}" />
        <pathelement path="${config.app.dir}" />
        <fileset dir="${3rdparty.dir}">
        <include name="**/*.jar" />
        <exclude name="**/oracle/**"/>
        </fileset>
            <fileset dir="${ojdbc.dir}">
            <include name="**/*.jar" />
        </fileset>
    </path>
    <property name="class.path" refid="project.class.path"/>
    <echo>${class.path}</echo>
</target>
```

# Timestamp

```ant
<tstamp>
    <format property="timestamp" pattern="yyyyMMdd-HHmmss"/>
</tstamp>
```

# Make directory

```ant
<target name="createdirs">
    <mkdir dir="${classes.dir}" />
    <mkdir dir="${log.dir}" />
    <mkdir dir="${report.dir}" />
</target>
```
