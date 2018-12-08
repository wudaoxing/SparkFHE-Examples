# SparkFHE-Examples

Note, there are two pom files which you can use to compile or package:
```bash
pom-devel.xml                   # will use the existing shared lib within ./libSparkFHE/lib
pom.xml                         # will download and refresh the C++ shared lib from our repo
```

Compile for the first time (so that, maven will download the shared lib)
```bash
./mvn clean compile
```


Run JUnit5 tests
```bash
./mvn test
```


Package into .jar
```bash
./mvn -U -DskipTests clean package
```


Run examples

Step 1: Generate necessary key pair and example ciphertexts (only needed to run once)
```bash
./mvn exec:java -Dexec.mainClass="spiritlab.sparkfhe.example.basic.KeyGenExample"       # this will generate the example key pair
./mvn exec:java -Dexec.mainClass="spiritlab.sparkfhe.example.basic.EncDecExample"       # this will generate some ciphertexts
```

Step 2: Test different FHE operations on example ciphertexts and vectors of ciphertexts
```bash
./mvn exec:java -Dexec.mainClass="spiritlab.sparkfhe.example.basic.BasicOPsExample"     # this will perform some basic FHE operations
./mvn exec:java -Dexec.mainClass="spiritlab.sparkfhe.example.basic.DotProductExample"   # this will perform dot product calculation on vectors of encrypted numbers 
```




For developer, you can update the shared libraries manually and recompile as below.
```bash
./mvn -f pom-devel.xml compile
```

