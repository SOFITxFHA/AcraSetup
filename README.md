# Acra Setup

This guide will help the developers into integrating Acra into their projects. 

## 1 - Add Acra dependency into your app build.gradle file:
    implementation("ch.acra:acra-http:$acraVersion")
    implementation("ch.acra:acra-core:$acraVersion")   
    
## 2 - Add Acra version ext to your project level build.gradle file
    ext.acraVersion = "5.8.2"

## 3 - Add the following code to your Application class:
    CrashReporter.initialize(this, path)
        initAcra {
            reportFormat = StringFormat.JSON
            httpSender {
                uri = "http://172.105.78.169:8080/report"
                basicAuthLogin = "xxxxxxxx" //TODO Update this with your app integration
                basicAuthPassword = "xxxxxxxxxx" //TODO Update this with your app integration
		    httpMethod = HttpSender.Method.POST
            }
	    }
	    
## 4 - Remove the TODO tags once your update your "basicAuthLogin" and "basicAuthPassword"
And just like that, your Acra integration is done!
