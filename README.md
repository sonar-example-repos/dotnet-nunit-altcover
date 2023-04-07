# NUnit Unit Tests and AltCover coverage - A SonarQube Sonar Scanner for .NET Example

# Unit testing using NUnit sample

This sample is part of the [unit testing tutorial](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-nunit) for creating applications with unit tests included. See that topic for detailed steps on the code for this sample.

## Key features

This sample demonstrates creating a library and writing effective unit tests that validate the features in that library. The example provides a service that indicates whether a number is prime.

## Restore and test

To run the tests, navigate to the *PrimeService.Tests* directory and type the following commands:

```
dotnet restore
dotnet test
```

`dotnet restore` restores the packages of both projects.
`dotnet test` builds both projects and runs all of the configured tests.

<a name="dotnet-restore-note"></a>
**Note:** Starting with .NET Core 2.0 SDK, you don't have to run [`dotnet restore`](https://docs.microsoft.com/dotnet/core/tools/dotnet-restore) because it's run implicitly by all commands that require a restore to occur, such as `dotnet new`, `dotnet build` and `dotnet run`. It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.



TODO write up instructions on this repo
* https://stackoverflow.com/questions/45482507/how-do-i-install-nunit-3-console-on-windows-and-run-tests
* go update https://community.sonarsource.com/t/coverage-test-data-generate-reports-for-c-vb-net/9871


The key Sonar analysis parameter is **/d:"sonar.cs.opencover.reportsPaths=NUnitResults.xml"**.

```text
> (install NUnit via choco)
> (if altcover not added to csproj/vbproj yet) dotnet add package altcover --version 8.5.841
> dotnet sonarscanner begin /k:dotnet-nunit-altcover /d:sonar.login=<INSERT-TOKEN> /d:sonar.host.url=http://localhost:9900 /d:sonar.verbose=true /d:"sonar.cs.opencover.reportsPaths=NUnitResults.xml"
> dotnet build
> nunit3-console.exe --result=NUnitResults.xml "PrimeService.Tests\bin\Debug\netcoreapp3.1\PrimeService.Tests.dll"
> dotnet test /p:AltCover=true
> dotnet sonarscanner end /d:sonar.login=<INSERT-TOKEN>
```

Example sonar analysis log:
```text
04:35:30.776 INFO: Sensor C# Unit Test Results Import [csharp]
04:35:30.777 DEBUG: Pattern matcher extracted prefix/absolute path 'C:\Users\maevetesting\Downloads\Projects\dotnet-nunit-altcover\.\NUnitResults.xml' from the given pattern 'NUnitResults.xml'.
04:35:30.777 DEBUG: Pattern matcher returns a single file: 'C:\Users\maevetesting\Downloads\Projects\dotnet-nunit-altcover\.\NUnitResults.xml'.
04:35:30.778 DEBUG: The current user dir is 'C:\Users\maevetesting\Downloads\Projects\dotnet-nunit-altcover'.
04:35:30.778 INFO: Parsing the NUnit Test Results file 'C:\Users\maevetesting\Downloads\Projects\dotnet-nunit-altcover\.\NUnitResults.xml'.
04:35:30.916 DEBUG: Parsed NUnit test run - total: 4, totalSkipped: 0, failures: 0, errors: 0, execution time: 966.
04:35:30.935 INFO: Sensor C# Unit Test Results Import [csharp] (done) | time=159ms
```
