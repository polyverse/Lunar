# DEPRECATION NOTICE

Please note that this repository has been deprecated and is no longer actively maintained by Polyverse Corporation.  It may be removed in the future, but for now remains public for the benefit of any users.

Importantly, as the repository has not been maintained, it may contain unpatched security issues and other critical issues.  Use at your own risk, or better yet, please refer to the original repository: https://github.com/Dewera/Lunar

For any other issues, please feel free to contact info@polyverse.com

---
## Lunar

![](https://github.com/Dewera/Lunar/workflows/Continuous%20Integration/badge.svg)

A lightweight native DLL mapping library that supports mapping directly from memory

----

### Features

- WOW64 and x64 support
- Imports and delay imports are resolved
- Relocations are performed
- Sections are mapped with correct memory protection
- Headers are mapped with correct memory protection
- TLS callbacks are called with ProcessAttach and ProcessDetach
- Exception handling is setup for both SEH and C++ exceptions
- Security cookie is initialised

----

### Installation

- Install the latest version of Lunar using [NuGet](https://www.nuget.org/packages/Lunar)

----

### Getting started

The example below demonstrates a basic implementation of the library

```csharp

var libraryMapper = new LibraryMapper(process, dllBytes);

// Map the DLL into the process

libraryMapper.MapLibrary();

// Unmap the DLL from the process

libraryMapper.UnmapLibrary();

```

----

### Constructors

```csharp
LibraryMapper(Process, Memory<byte>)
```
Provides the functionality to map a DLL from memory into a remote process


```csharp
LibraryMapper(Process, string)
```

Provides the functionality to map a DLL from disk into a remote process

----

### Properties

```csharp
DllBaseAddress
```

The base address of the DLL in the remote process after it has been mapped

----

### Methods

```csharp
MapLibrary()
```

Maps the DLL into the remote process

```csharp
UnmapLibrary()
```

Unmaps the DLL from the remote process

----

### Caveats

- Attempting to inject into a system level process will require your program to be run in administrator mode
- Mapping requires the presence of a PDB for ntdll.dll, and, so, will automatically download the latest version of this PDB from the Microsoft symbol server and cache it in `%temp%/Lunar/PDB`

----

### Contributing

Pull requests are welcome

For large changes, please open an issue first to discuss what you would like to add
