# External Libraries
This section covers how to add a third party library Java to your project.

## Remote Libraries
#### Adding the Repository
1. Open `<Project_Dir>/JBI/Android.UPL.xml` in your favorite text editor.
2. Find the `<baseBuildGradleAdditions>` tag.
3. Add the following code inside the tag:
```xml
<insert>	
	allprojects {
		repositories {
			// Example for google repository.
			google()
		
			// Maven Repository
			maven {
				url 'https://website.com/'
			}
		}
	}
</insert>
```

#### Adding the Dependency
1. Open `<Project_Dir>/JBI/Android.UPL.xml` in your favorite text editor.
2. Find the `<buildGradleAdditions>` tag.
3. Add the following code inside the tag:
```xml
<insert>
	dependencies {
		implementation fileTree(dir: 'libs', include: ['*.jar'])
		
		// Your libraries here. For example, here we add the Google Ads library:
		implementation 'com.google.android.gms:play-services-ads:20.2.0'
	}
</insert>
```

## Local Libraries
1. Open `<Project_Dir>/JBI/Android.UPL.xml` in your favorite text editor.
2. Find the `<buildGradleAdditions>` tag.
3. Add the following code inside the tag:
```xml
<insert>
	dependencies {
		implementation fileTree(dir: 'libs', include: ['*.jar'])
		
		// Your other remote librares...
		implementation 'com.google.android.gms:play-services-ads:20.2.0'
		// ...
		
		// Adds a local .jar file. $S(PluginDir) points to the `<Project_Dir>/JBI/` library.
		implementation files("</insert><insertValue value="$S(PluginDir)"/><insert>/path/to/lib/lib.jar")
		
		// Adds another .jar file. With an absolute path this time.
		implementation files("C:/Android/Libraries/path/to/lib/lib.jar")
	}
</insert>
```
