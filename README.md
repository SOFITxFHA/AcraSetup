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
                //required. Https recommended
                uri = "http://172.105.78.169:8080/report"
                //optional. Enables http basic auth
                basicAuthLogin = "xxxxxxxx" //TODO Update this with your app integration
                //required if above set
                basicAuthPassword = "xxxxxxxxxx" //TODO Update this with your app integration
            }
            
## 4 - Update basicAuthLogin and basicAuthPassword with the acra integration that will be shared with you for your app (Example Code is given below):
            initAcra {
	            reportFormat = StringFormat.JSON
	            httpSender {
		            uri = "/report" /*best guess, you may need to adjust this*/
		            basicAuthLogin = "your-app-auth-login-will-be-here" //You'll copy this to your Application file
		            basicAuthPassword = "your-app-password-will-be here" //You'll copy this to your Application file
		            httpMethod = HttpSender.Method.POST
	            }
            }
