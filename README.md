# gradleExtractZip

**Problem:**

I'm trying to extract a zip-file, which includes files with a german umlaut in its filename.
After unpacking the zip-file, all umlaute are replaced with cryptic characters.

| Filenames inside the Zip-Archive | Filenames after extracting the Zip-Archive|
| ------------------------------------ | ------------------------------------ |  
|  Umlaute-ÄÖÜ.txt | Umlaute-Ž™š.txt|  
|  Ä.txt | Ž.txt |  
|  Ö.txt | ™.txt |  
|  Ü.txt | š.txt |  

**My Gradle Task**

```groovy
task extractZip(dependsOn: clean){
    doLast{
        copy {
            FileTree updateZip = zipTree(file("$projectDir/UmlauteInside.zip"))
            from updateZip
            into file("$buildDir/extractedZipfile")
        }
    }
}
```

**Usage on commandline:**

`.\gradlew extractZip`

**Output:**

`build\extractedZipfile`
