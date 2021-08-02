# Acra Setup

This guide will help the developers into integrating Acra into their projects. 

## 1 - Add Acra dependency into your app build.gradle file:
    implementation("ch.acra:acra-http:$acraVersion")
    implementation("ch.acra:acra-mail:$acraVersion")
    implementation("ch.acra:acra-core:$acraVersion")
    implementation("ch.acra:acra-dialog:$acraVersion")
    implementation("ch.acra:acra-notification:$acraVersion")
    implementation("ch.acra:acra-toast:$acraVersion")
    
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
                // defaults to POST
                httpMethod = HttpSender.Method.POST
                //defaults to 5000ms
                connectionTimeout = 5000
                //defaults to 20000ms
                socketTimeout = 20000
                // defaults to false
                dropReportsOnTimeout = false
                //defaults to false. Recommended if your backend supports it
                compress = false
                //defaults to all
                tlsProtocols = arrayOf(TLS.V1_3, TLS.V1_2, TLS.V1_1, TLS.V1)
            }
            
## 4 - Update basicAuthLogin and basicAuthPassword with the acra integration for your app (Example Code is give below):
            initAcra {
	            reportFormat = StringFormat.JSON
	            httpSender {
		            uri = "/report" /*best guess, you may need to adjust this*/
		            basicAuthLogin = "your-app-auth-login-will-be-here" //You'll copy this to your Application file
		            basicAuthPassword = "your-app-password-will-be here" //You'll copy this to your Application file
		            httpMethod = HttpSender.Method.POST
	            }
            }
