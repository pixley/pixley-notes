[Github Repository](https://github.com/pixley/rpgs-community-patch)

[Unity Mod Development](https://wiki.nexusmods.com/index.php/Category:Unity_Mod_Manager)
# Context
I had originally intended on building an [[RPG Sounds Replacement]] from the ground up, but it occurred to me that it would make more sense to mod RPG Sounds instead with the fixes I wanted.  And, once those fixes are made, I could then develop future mods to implement entirely new functionality like direct VBAN output.
# Distributed Development Enabling
C# compilation relies on directly referencing linked libraries.  This poses an issue for mod development, as distributing RPG Sounds' DLLs, despite it being free-to-download, could potentially be a legal issue, and I don't want to deal with that.  And they shouldn't have to be in the repo anydangways.

The preferred method of referencing third-party libraries in the .NET world is NuGet.  However, this doesn't actually get around the proprietary library redistribution issue.

C# does, however, have the concept of "reference assemblies", which are basically hollow libraries where the API is intact, but all implementation is stripped away.  Reference assemblies are generally created by the creator of the library, but JetBrains offers the free utility [Refasmer](https://github.com/JetBrains/Refasmer), which takes an existing C# library and makes a reference assembly out of it.  Then there's no issue redistributing those!