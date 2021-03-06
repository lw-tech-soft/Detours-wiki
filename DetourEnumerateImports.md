DetourEnumerateImports
======================

Enumerate imports from a module.

Definition
----------

>     BOOL DetourEnumerateImports(
>         _In_opt_ HMODULE hModule,
>         _In_opt_ PVOID pContext,
>         _In_opt_ PF_DETOUR_IMPORT_FILE_CALLBACK pfImportFile,
>         _In_opt_ PF_DETOUR_IMPORT_FUNC_CALLBACK pfImportFunc
>         );

Parameters
----------

*hModule*
:   The handle to the module whose imports are to be enumerated.

*pContext*
:   Program specific context that will be passed to *pfImportFile* and
    *pfImportFunc*.

*pfImportFile*
:   Callback function to be called once per file imported by module.

*pfImportFunc*
:   Callback function to be called once per function imported by module.

Return value
------------

`TRUE` if module imports are enumerated; otherwise `FALSE`.

Error codes
-----------

The function sets one of the following error codes, as appropriate. The
error code may be retrived after the function has returned by calling
`GetLastError`.

**ERROR\_BAD\_EXE\_FORMAT**
:   The MZ header of specified module is invalid.

**ERROR\_EXE\_MARKED\_INVALID**
:   The NT COFF header of the specified module is invalid.

**ERROR\_INVALID\_EXE\_SIGNATURE**
:   The NT COFF header of the specified module has an invalid signature.

Remarks
-------

If you need a pointer into the Import Address Table ("IAT"), you should
use the [DetourEnumerateImportsEx](DetourEnumerateImportsEx).

Related Samples
---------------

[Tracebld](SampleTracebld).
