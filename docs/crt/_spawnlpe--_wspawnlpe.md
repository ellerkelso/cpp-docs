---
title: "_spawnlpe, _wspawnlpe"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
apiname: 
  - "_spawnlpe"
  - "_wspawnlpe"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-process-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "spawnlpe"
  - "_wspawnlpe"
  - "_spawnlpe"
  - "wspawnlpe"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wspawnlpe function"
  - "wspawnlpe function"
  - "processes, creating"
  - "spawnlpe function"
  - "_spawnlpe function"
  - "processes, executing new"
  - "process creation"
ms.assetid: e171ebfa-70e7-4c44-8331-2a291fc17bd6
caps.latest.revision: 18
ms.author: "corob"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# _spawnlpe, _wspawnlpe
Creates and executes a new process.  
  
> [!IMPORTANT]
>  This API cannot be used in applications that execute in the [!INCLUDE[wrt](../atl/includes/wrt_md.md)]. For more information, see [CRT functions not supported with /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Syntax  
  
```  
intptr_t _spawnlpe(  
   int mode,  
   const char *cmdname,  
   const char *arg0,  
   const char *arg1,  
   ... const char *argn,  
   NULL,  
   const char *const *envp   
);  
intptr_t _wspawnlpe(  
   int mode,  
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   const wchar_t *arg1,  
   ... const wchar_t *argn,  
   NULL,  
   const wchar_t *const *envp   
);  
```  
  
#### Parameters  
 `mode`  
 Execution mode for the calling process.  
  
 `cmdname`  
 Path of the file to be executed.  
  
 `arg0, arg1, ... argn`  
 List of pointers to arguments. The `arg0` argument is typically a pointer to `cmdname`. The arguments `arg1` through `argn` are pointers to the character strings that form the new argument list. Following `argn`, there must be a `NULL` pointer to mark the end of the argument list.  
  
 `envp`  
 Array of pointers to environment settings.  
  
## Return Value  
 The return value from a synchronous `_spawnlpe` or `_wspawnlpe` (`_P_WAIT` specified for `mode`) is the exit status of the new process. The return value from an asynchronous `_spawnlpe` or `_wspawnlpe` (`_P_NOWAIT` or `_P_NOWAITO` specified for `mode`) is the process handle. The exit status is 0 if the process terminated normally. You can set the exit status to a nonzero value if the spawned process specifically uses a nonzero argument to call the `exit` routine. If the new process did not explicitly set a positive exit status, a positive exit status indicates an abnormal exit caused by an abort or an interrupt. A return value of –1 indicates an error (the new process is not started). In this case, `errno` is set to one of the following values.  
  
 `E2BIG`  
 Argument list exceeds 1024 bytes.  
  
 `EINVAL`  
 `mode` argument is invalid.  
  
 `ENOENT`  
 File or path is not found.  
  
 `ENOEXEC`  
 Specified file is not executable or has an invalid executable-file format.  
  
 `ENOMEM`  
 Not enough memory is available to execute the new process.  
  
 For more information about these and other return codes, see [errno, _doserrno, _sys_errlist, and _sys_nerr](../crt/errno--_doserrno--_sys_errlist--and-_sys_nerr.md).  
  
## Remarks  
 Each of these functions creates and executes a new process, passes each command-line argument as a separate parameter, and passes an array of pointers to environment settings. These functions use the `PATH` environment variable to find the file to execute.  
  
 These functions validate their parameters. If either `cmdname` or `arg0` is an empty string or a null pointer, the invalid parameter handler is invoked, as described in [Parameter Validation](../crt/parameter-validation.md). If execution is allowed to continue, these functions set `errno` to `EINVAL`, and return -1. No new process is spawned.  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`_spawnlpe`|\<process.h>|  
|`_wspawnlpe`|\<stdio.h> or \<wchar.h>|  
  
 For more compatibility information, see [Compatibility](../crt/compatibility.md).  
  
## Example  
 See the example in [_spawn, _wspawn Functions](../crt/_spawn--_wspawn-functions.md).  
  
## .NET Framework Equivalent  
  
-   [System::Diagnostics::Process Class](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [System::Diagnostics::ProcessStartInfo Class](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## See Also  
 [Process and Environment Control](../crt/process-and-environment-control.md)   
 [_spawn, _wspawn Functions](../crt/_spawn--_wspawn-functions.md)   
 [abort](../crt/abort.md)   
 [atexit](../crt/atexit.md)   
 [_exec, _wexec Functions](../crt/_exec--_wexec-functions.md)   
 [exit, _Exit, _exit](../crt/exit--_exit--_exit.md)   
 [_flushall](../crt/_flushall.md)   
 [_getmbcp](../crt/_getmbcp.md)   
 [_onexit, _onexit_m](../crt/_onexit--_onexit_m.md)   
 [_setmbcp](../crt/_setmbcp.md)   
 [system, _wsystem](../crt/system--_wsystem.md)