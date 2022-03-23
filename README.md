# beam-wordcount-go
Example from https://github.com/apache/beam/blob/master/sdks/go/examples/wordcount/wordcount.go

## Read More

- [Apache Beam Go SDK Quickstart](https://beam.apache.org/get-started/quickstart-go/)

## Windows Tools

- PowerShell (cross-platform)
- Git
- Chocolatey (Windows Package Manager)

## Install Go and Verify

```PowerShell
go version
```

Review the installed files at C:\Program Files\Go.

## Initialize Project Module

```PowerShell
go mod init github.com/denisecase/beam-pagerank-go
```

Review go.mod.

## Get Beam Go SDK

When building, read error messages. 
If a package is needed, a command to add will be provided. 
Run the necessary commands. 

The command `go get` will download the package to the local module cache, 
and add it to the go.mod file. The `-u` flag indicates update. 

```PowerShell
go get -u github.com/apache/beam/sdks/v2/go/pkg/beam
go get -u github.com/apache/beam/sdks/v2/go/pkg/beam/transforms/create
go get -u github.com/apache/beam/sdks/v2/go/pkg/beam/sideInput
go get github.com/apache/beam/sdks/v2/go/pkg/beam/io/filesystem/gcs@v2.37.0
```

This allows us to use beam packages. Review go.mod. 

## Build to Executable

```PowerShell
go build pagerank.go
```

Review go.sum. 
Read any error messages and run recommended commands as needed.
Verify the new .exe executable file is created.

## Run Executable

```PowerShell
.\pagerank.exe --input <PATH_TO_INPUT_FILE> --output out.csv
```

Examples: 

```PowerShell
.\pagerank.exe --output denise.csv
.\pagerank.exe 
```

Review the local dependencies at C:\Users\<username>\AppData\Local\go-build.

## About Go

- go get - updates dependencies/versions listed in go.mod and updates local cache
- go install - used to build and install the provided source file in $GOPATH$
- go build - compiles and builds executable locally

## About Beam Pipelines

From https://beam.apache.org/documentation/programming-guide/

A typical Beam driver program works as follows:

1. Create a Pipeline object and set the pipeline execution options, including the Pipeline Runner.

2. Create an initial PCollection for pipeline data, either using the IOs to read data from an external storage system, or using a Create transform to build a PCollection from in-memory data.

3. Apply PTransforms to each PCollection. Transforms can change, filter, group, analyze, or otherwise process the elements in a PCollection. A transform creates a new output PCollection without modifying the input collection. A typical pipeline applies subsequent transforms to each new output PCollection in turn until processing is complete. However, note that a pipeline does not have to be a single straight line of transforms applied one after another: think of PCollections as variables and PTransforms as functions applied to these variables: the shape of the pipeline can be an arbitrarily complex processing graph.

4. Use IOs to write the final, transformed PCollection(s) to an external source.

5. Run the pipeline using the designated Pipeline Runner.

## Mapping Done by ParDo

A ParDo transform considers each element in the input PCollection, performs some processing function (your user code) on that element, and emits zero or more elements to an output PCollection.

The emit func(...) is useful when the number of output elements differ to the number of input elements. If its a 1:1 mapping a return makes the function easier to read. 

From <https://blog.gopheracademy.com/advent-2018/apache-beam/>

## Pushing to GitHub

1. Create an empty repo (same folder name) in GitHub
2. In your local folder, `git init`
3. `git remote add origin https://github.com/denisecase/beam-pagerank-go.git`
4. `git add .`
5. `git commit -m "initial commit"`
6. `git push -u origin main`