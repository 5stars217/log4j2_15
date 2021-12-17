# Log4j2 Dos Env


## example one, pattern layout config in log4j.xml

`log4j2.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Configuration status="warn" name="MyApp" packages="">
    <appenders>
        <console name="STDOUT" target="SYSTEM_OUT">
            <PatternLayout pattern="%msg{lookups}%n"/>
        </console>
    </appenders>
    <Loggers>
        <Root level="info">
            <AppenderRef ref="STDOUT"/>
        </Root>
    </Loggers>
</Configuration>
```

poc：`localhost:8080/test?message=payload`

##  example 2- different pattern config.

`log4j2.xml`
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Configuration status="warn" name="MyApp" packages="">
    <appenders>
        <console name="STDOUT" target="SYSTEM_OUT">
            <PatternLayout>
                <pattern>%d %p %c{1.} [%t] $${ctx:loginId} %m%n</pattern>
            </PatternLayout>
        </console>
    </appenders>
    <Loggers>
        <Root level="info">
            <AppenderRef ref="STDOUT"/>
        </Root>
    </Loggers>
</Configuration>
```

poc：`localhost:8080/cve?userId=payload`
