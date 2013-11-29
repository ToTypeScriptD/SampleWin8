#Sample Windows 8 WinJS TypeScript project

This project's intent is to allow you to understand some steps used to convert a `WinJS` application to use [TypeScript](http://typescriptlang.org).

This readme will basically describe in detail what each commit in this repository's history is doing.

### Prerequisites

1. Visual Studio
2. [TypeScript plugin](http://www.typescriptlang.org) for Visual Studio


### 1. File->New Windows 8.0 Navigation app.

Nothing fancy here. Using a regular template from Visual Studio we created a basic Navigation app.

### 2. Update project file to start supporting TypeScript

You should be able to find the details of this step on the [TypeScript CodePlex Documentation](https://typescript.codeplex.com/wikipage?title=Compile-on-save&referringTitle=Documentation) page. We're basically giving the project a pointer

### 3. Update .gitignore

We don't want to track the generated `*.js` files once we've converted over to TypeScript so let's update our git repositories `.gitignore` file to not track these js files.

### 4. Convert *.js files to *.ts

1. Rename the project `*.js` files to `*.ts` files.
2. We're updating the project file to get the nested dependency feel so that the generated `.js` file is nested under `.ts` files.
3. Note: we still reference the `*.js` files in our `*.html`.

### 5. Stub winjs type definitions

Adding a placeholder for the `WinJS` type. You can consider another source for this such as [DefinitelyTyped WinJS](https://github.com/borisyankov/DefinitelyTyped/blob/master/winjs/winjs.d.ts) or the one in the TypeScript repositories source. But we're just taking a minimal step for this sample.

### 6. Use ToTypeScriptD to generated winrt.d.ts type definitions

1. First go get [ToTypeScriptD installed](https://github.com/ToTypeScriptD/ToTypeScriptD).
2. You can then use the command below in PowerShell to generate the type definitions.

Below is the PowerShell command:

    ToTypeScriptD winmd --specialTypes `
        C:\Windows\System32\WinMetadata\Windows.ApplicationModel.winmd `
        C:\Windows\System32\WinMetadata\Windows.Data.winmd `
        C:\Windows\System32\WinMetadata\Windows.Devices.winmd `
        C:\Windows\System32\WinMetadata\Windows.Foundation.winmd `
        C:\Windows\System32\WinMetadata\Windows.Globalization.winmd `
        C:\Windows\System32\WinMetadata\Windows.Graphics.winmd `
        C:\Windows\System32\WinMetadata\Windows.Management.winmd `
        C:\Windows\System32\WinMetadata\Windows.Media.winmd `
        C:\Windows\System32\WinMetadata\Windows.Networking.winmd `
        C:\Windows\System32\WinMetadata\Windows.Security.winmd `
        C:\Windows\System32\WinMetadata\Windows.Storage.winmd `
        C:\Windows\System32\WinMetadata\Windows.System.winmd `
        C:\Windows\System32\WinMetadata\Windows.UI.winmd `
        C:\Windows\System32\WinMetadata\Windows.Web.winmd `
        | Out-File -FilePath SampleWin8\Scripts\typings\winrt.d.ts -Encoding ASCII

Same command as above without the newlines:

    ToTypeScriptD winmd --specialTypes C:\Windows\System32\WinMetadata\Windows.ApplicationModel.winmd C:\Windows\System32\WinMetadata\Windows.Data.winmd C:\Windows\System32\WinMetadata\Windows.Devices.winmd C:\Windows\System32\WinMetadata\Windows.Foundation.winmd C:\Windows\System32\WinMetadata\Windows.Globalization.winmd C:\Windows\System32\WinMetadata\Windows.Graphics.winmd C:\Windows\System32\WinMetadata\Windows.Management.winmd C:\Windows\System32\WinMetadata\Windows.Media.winmd C:\Windows\System32\WinMetadata\Windows.Networking.winmd C:\Windows\System32\WinMetadata\Windows.Security.winmd C:\Windows\System32\WinMetadata\Windows.Storage.winmd C:\Windows\System32\WinMetadata\Windows.System.winmd C:\Windows\System32\WinMetadata\Windows.UI.winmd C:\Windows\System32\WinMetadata\Windows.Web.winmd | Out-File -FilePath SampleWin8\Scripts\typings\winrt.d.ts -Encoding ASCII


### 7. Appease the TypeScript compiler

This is just a step to appease the TypeScript compiler until we start to use TypeScript modules instead of WinJS namespaces.

### 8. Use TypeScript module instead of WinJS Module

If you use WinJS Namespaces you will loose many of the benefits of TypeScript and surrounding TypeScript tooling provides. So we probalby want to consider using TypeScript modules in place of WinJS Namespaces.

### 9. Added a readme

Added this readme file :) I hope it was useful.

# Contribute to this guide?

I am interested in suggestions or pull requests for this guide . To keep it useful to users, I may squish commits to keep the git commit log in line with this readme. If you submit a pull request, please update the below section with your name so I can give you proper accolades.

* ![staxmanade avatar](https://gravatar.com/avatar/b92a22c70f03a3218b358cfeeb566ac4?s=20)  [Jason Jarrett](github.com/staxmanade/)
