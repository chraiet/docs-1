---
title: "ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: 
  - "ICLRAssemblyIdentityManager.GetBindingIdentityFromStream"
apilocation: 
  - "mscoree.dll"
apitype: "COM"
f1_keywords: 
  - "ICLRAssemblyIdentityManager::GetBindingIdentityFromStream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBindingIdentityFromStream method [.NET Framework hosting]"
  - "ICLRAssemblyIdentityManager::GetBindingIdentityFromStream method [.NET Framework hosting]"
ms.assetid: 40123b30-a589-46b3-95d3-af7b2b0baa05
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# ICLRAssemblyIdentityManager::GetBindingIdentityFromStream Method
Gets the canonical assembly identity data for the assembly in the specified stream.  
  
## Syntax  
  
```  
HRESULT GetBindingIdentityFromStream (  
    [in] IStream    *pStream,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### Parameters  
 `pStream`  
 [in] The assembly stream to be evaluated.  
  
 `dwFlags`  
 [in] Provided for future extensibility. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.  
  
 `pwzBuffer`  
 [out] A buffer containing the opaque assembly identity data.  
  
 `pcchBufferSize`  
 [in, out] The size of `pwzBuffer`.  
  
## Return Value  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|The method returned successfully.|  
|E_INVALIDARG|The supplied `pStream` is null.|  
|ERROR_INSUFFICIENT_BUFFER|The size of `pwzBuffer` is too small.|  
|HOST_E_CLRNOTAVAILABLE|The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.|  
|HOST_E_TIMEOUT|The call timed out.|  
|HOST_E_NOT_OWNER|The caller does not own the lock.|  
|HOST_E_ABANDONED|An event was canceled while a blocked thread or fiber was waiting on it.|  
|E_FAIL|An unknown catastrophic failure occurred. If a method returns E_FAIL, the CLR is no longer usable within the process. Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.|  
  
## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** MSCorEE.h  
  
 **Library:** Included as a resource in MSCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## See Also  
 [ICLRAssemblyIdentityManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)   
 [ICLRAssemblyReferenceList Interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)