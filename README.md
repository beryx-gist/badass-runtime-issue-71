## Badass Runtime Plugin - [issue 71](https://github.com/beryx/badass-runtime-plugin/issues/71#issuecomment-707833927) ##

This 'Hello world' project shows how to change the value of the `Culture` parameter of light.exe, as discussed in the issue [JDK-8232621](https://bugs.openjdk.java.net/browse/JDK-8232621?focusedCommentId=14361347&page=com.atlassian.jira.plugin.system.issuetabpanels%3Acomment-tabpanel#comment-14361347).

The application is built using Gradle 6.7, which doesn't support Java 16.
However, you need a recent Java 16 version of jpackage.
Therefore, your JAVA_HOME should point to a JDK installation <= 15, while the environment variable BADASS_RUNTIME_JPACKAGE_HOME should point to a JDK 16 installation (build 16-ea+21-1209 or newer).

We set the `Culture` parameter to `zh-CN` by putting [the file a.wxl](https://github.com/beryx-gist/badass-runtime-issue-71/blob/master/src/main/resources/a.wxl) in the `src/main/resources` directory and by providing this directory to the `--resource-dir` option:
```
jpackage {
    installerOptions += ['--resource-dir', "src/main/resources"]
    ...
}
```
