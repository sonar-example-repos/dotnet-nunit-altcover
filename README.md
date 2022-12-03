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
https://stackoverflow.com/questions/45482507/how-do-i-install-nunit-3-console-on-windows-and-run-tests
go update https://community.sonarsource.com/t/coverage-test-data-generate-reports-for-c-vb-net/9871


```text
> dotnet add package altcover --version 8.5.841
> BEGIN
> dotnet build
> nunit3-console.exe --result=NUnitResults.xml "PrimeService.Tests\bin\Debug\netcoreapp3.1\PrimeService.Tests.dll"
> dotnet test /p:AltCover=true
> END
```
