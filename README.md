# TvDbSharper
TvDbSharper is a fully featured modern REST client for TheTVDB API v4

## Fork & Modernization (Version 4.0.11)

This repository is a modernized fork of the original `TvDbSharper` library. The client has been updated to support the latest .NET standards and includes fixes and new endpoints from the current TVDB API.

### Changes include:
* **Framework Update:** The library now targets `.NET Standard 2.0` (from 1.1) and the test projects run on `.NET 8` (from .NET 6).
* **API Client Refresh:** The client generator was fixed and re-run to pull in the latest TVDB API v4 specification.
* **New Endpoints Added:** Includes new API calls that were missing from the 2022 version, such as:
    * `AllEpisodes`
    * `AllPeople`
    * `ListBySlug`
    * `MovieBySlug`
    * `SeriesBySlug`
    * `SeriesNextAired`
    * `SearchByRemoteId`
    * `UserInfo` and `UserInfoById`
* **Bug Fixes:**
    * Resolved runtime JSON deserialization errors where the live API sends fields not in the official documentation (e.g., `absoluteNumber`, `remoteIds`, `tags`, `primary_type`, `company_type`).
    * Fixed 401 Unauthorized error handling to parse the modern error response from the API.

## How to install

This fork is not published to the public nuget.org. To use it, you can:

1.  **Pack Locally:** Run `dotnet pack` on the `.csproj` file to create a `.nupkg` and add it to a local NuGet feed in Visual Studio.
2.  **Use GitHub Packages:** Set up a GitHub Action to publish the package to your own GitHub Packages feed.
3.  **Use a Project Reference:** Add a direct `<ProjectReference>` to the `TvDbSharper.csproj` file from your other solutions.

## The client

There is one client you need to know about:

```C#
var client = new TvDbClient();