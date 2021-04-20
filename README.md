This project has been created to demonstrate the issue raised in the [NuGet and Snappy libraries impact on VCS (GIT)](https://developer.mongodb.com/community/forums/t/nuget-and-snappy-libraries-impact-on-vcs-git/10011) topic on the [mongoDB Developer Community Forum](https://developer.mongodb.com/community/forums/)

## Environment Used

* Windows 10 Pro Version 20H2 (OS build 19042.928)
* Microsoft Visual Studio Enterprise 2019 Version 16.8.4

## Steps to Reproduce

* Create a new C# Console App (.NET Framework) and target .NET Framework 4.7.2
* Right click the Solution and choose Manage NuGet Packages for Solution...
* Browse for the MongoDB.Driver and install version 2.12.2 (the latest stable version on 20-Apr-2021)
* Observe that the following new files are added to the solution and included in the VCS:
  * `Core/Compression/Snappy/lib/win/snappy32.dll`
  * `Core/Compression/Snappy/lib/win/snappy64.dll`
  * `Core/Compression/Zstandard/lib/win/libzstd.dll`
  * `libmongocrypt.dylib`
  * `libmongocrypt.so`
  * `mongocrypt.dll`

## Possible Workaround

One possible workaround proposed by [Wan Bachtiar](https://developer.mongodb.com/community/forums/u/wan) is to add the reference to the MongoDB Driver directly in the `csproj` file and not use NuGet:

    <ItemGroup>
      <PackageReference Include="MongoDB.Driver" Version="2.12.2" />
    </ItemGroup>
