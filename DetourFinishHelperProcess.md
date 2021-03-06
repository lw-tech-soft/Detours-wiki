DetourFinishHelperProcess
=========================

Finishes updating a target process from the helper process.

Definition
----------

>     VOID CALLBACK DetourFinishHelperProcess(
>         _In_ HWND,
>         _In_ HINSTANCE,
>         _In_ LPSTR,
>         _In_ INT);

Remarks
-------

When creating a 32-bit target process from a 64-bit parent process or
creating a 64-bit target process from a 32-bit parent process, the
[`DetourCreateProcessWithDllEx`](DetourCreateProcessWithDllEx)
API must create a temporary helper process. It loads a copy of the
user-supplied DLL into the helper process using the `rundll32.exe`
mechanism. `Rundll32.exe` will call DLL's Ordinal 1 export function. The
`DetourFinishHelperProcess` API must be set as the DLL's Ordinal 1
export function.

Within its `DllMain` function, a user-supplied DLL can determine if the
process is a helper process or a target process by calling the
[DetourIsHelperProcess](DetourIsHelperProcess) API.

For more information, see [Detouring 32-bit and 64-bit
Processes](OverviewHelpers).

Related Samples
---------------

[Simple](SampleFindFunc), [Simple](SampleSimple),
[Slept](SampleSlept), [Traceapi](SampleTraceapi),
[Tracebld](SampleTracebld), [Tracelnk](SampleTracelnk),
[Tracemem](SampleTracemem), [Tracereg](SampleTracereg),
[Traceser](SampleTraceser), [Tracetcp](SampleTracetcp),
[Tryman](SampleTryman).
