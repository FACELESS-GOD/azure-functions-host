### Release notes

<!-- Please add your release notes in the following format:
- My change description (#PR)
-->
- Update Python Worker Version to [4.18.0](https://github.com/Azure/azure-functions-python-worker/releases/tag/4.18.0)
- Update Java Worker Version to [2.13.0](https://github.com/Azure/azure-functions-java-worker/releases/tag/2.13.0)
- Update WebJobsScriptHostService to remove hardcoded sleep during application shut down (#9520)
- Update PowerShell 7.2 Worker Version to [4.0.2974](https://github.com/Azure/azure-functions-powershell-worker/releases/tag/v4.0.2974)
- Update PowerShell 7.0 Worker Version to [4.0.2973](https://github.com/Azure/azure-functions-powershell-worker/releases/tag/v4.0.2973)
- Add support for standalone executable (ie: `dotnet build --standalone`) for out-of-proc workers in Linux Consumption. (#9550)
- Bug fix: Do not restart worker channels or JobHost when an API request is made to get or update the function metadata (unless the config was changed) (#9510)
  - This fixes a bug where requests to 'admin/functions' lead to a "Did not find initialized workers" error when
    worker indexing is enabled.
- Bug fix: If there are no channels created and the host is running, restart the JobHost instead of shutting down worker channels (#9510)
  - This fixes a bug with worker indexing where we are shutting down worker channels and creating a new channel that never
    gets properly initialized as the invocation buffers are not created - this leads to a "Did not find initialized workers" error.
- Check if a blob container or table exists before trying to create it (#9555)
- Limit dotnet-isolated specialization to 64 bit host process (#9548)
- Sending command line arguments to language workers with `functions-` prefix to prevent conflicts (#9514)