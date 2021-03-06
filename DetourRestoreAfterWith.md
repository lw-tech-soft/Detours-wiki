DetourRestoreAfterWith
======================

Restore the contents in memory import table after a process was started
with
[DetourCreateProcessWithDllEx](DetourCreateProcessWithDllEx) or
[DetourCreateProcessWithDlls](DetourCreateProcessWithDlls). .

Definition
----------

>     BOOL DetourRestoreAfterWith(VOID);

Return value
------------

Returns true if the necessary payload was found and the restore
succeeded.

Error codes
-----------

The function sets one of the following error codes if it was unable to
find the necessary payload or restore the import table. The error code
may be retrived after the function has returned by calling
`GetLastError`.

**ERROR\_MOD\_NOT\_FOUND**
:   Could not find the necessary payload.

Remarks
-------

The
[`DetourCreateProcessWithDllEx`](DetourCreateProcessWithDllEx)
API modifies the in-memory import table of the target PE binary program
in the new process it creates. For correct application compatibilty, the
changes to the import table should be removed before the application
runs. To remove these changes,
[`DetourCreateProcessWithDllEx`](DetourCreateProcessWithDllEx)
copies relevant reversal data into a payload in the target process using
the [`DetourCopyPayloadToProcess`](DetourCopyPayloadToProcess)
API. When called in the target process, `DetourRestoreAfterWith`
searches for the necessary payloaded and restores the contents of the
import table.

For correct results, `DetourRestoreAfterWith` should be called in the
PROCESS\_ATTACH portion of the DllMain function of the DLL loaded into
the target process.

Related Samples
---------------

[Simple](SampleFindFunc), [Simple](SampleSimple),
[Slept](SampleSlept), [Traceapi](SampleTraceapi),
[Tracebld](SampleTracebld), [Tracelnk](SampleTracelnk),
[Tracemem](SampleTracemem), [Tracereg](SampleTracereg),
[Traceser](SampleTraceser), [Tracetcp](SampleTracetcp),
[Tryman](SampleTryman).
