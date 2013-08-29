* Set compiler ```export CC=<path-to>/ccc-analyzer```
* Generate makefiles ```cmake -H<source-dir> -B<build-dir>```
* Run the scan-build ```scan-build --use-analyzer=<path-to>/clang make```
* Analyze the build ```scan-view <output-file>```