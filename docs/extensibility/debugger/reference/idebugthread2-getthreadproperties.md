---
title: "IDebugThread2::GetThreadProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::GetThreadProperties"
helpviewer_keywords: 
  - "IDebugThread2::GetThreadProperties"
ms.assetid: 304403fd-f4f8-4096-ac2c-bd3b59663aad
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugThread2::GetThreadProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient les propriétés décrivant ce thread.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetThreadProperties (   
   THREADPROPERTY_FIELDS dwFields,  
   THREADPROPERTIES*     ptp  
);  
```  
  
```c#  
int GetThreadProperties (   
   enum_THREADPROPERTY_FIELDS dwFields,  
   THREADPROPERTIES[]         ptp  
);  
```  
  
#### Paramètres  
 `dwFields`  
 \[in\]  Une combinaison des indicateurs d'énumération de [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) qui détermine les champs d' `ptp` doivent être effectués.  
  
 `ptp`  
 \[in, out\]  Une structure de [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) qui est rempli avec les propriétés du thread.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Les informations retournées de cette méthode sont généralement affichées dans la fenêtre de débogage de **Threads** .  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CProgram` qui implémente l'interface d' [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .  
  
```cpp#  
HRESULT CProgram::GetThreadProperties(THREADPROPERTY_FIELDS dwFields,  
                                      THREADPROPERTIES *ptp)  
{  
    HRESULT hr = E_FAIL;    
  
    // Check for valid argument.    
   if (ptp)    
    {    
      // Create an array of buffers at ptp the size of the  
      // THREADPROPERTIES structure and set all of the  
      // buffers at ptp to 0.    
      memset(ptp, 0, sizeof (THREADPROPERTIES));    
  
      // Check if there is a valid THREADPROPERTY_FIELDS and the TPF_ID flag is set.    
      if (dwFields & TPF_ID)    
      {    
         // Check for successful assignment of the current thread ID to  
         //  the dwThreadId of the passed THREADPROPERTIES.    
         if (GetThreadId(&(ptp->dwThreadId)) == S_OK)    
         {    
            // Set the TPF_ID flag in the THREADPROPERTY_FIELDS enumerator    
            // of the passed THREADPROPERTIES.    
            ptp->dwFields |= TPF_ID;    
         }    
      }    
  
      hr = S_OK;    
    }    
    else    
        hr = E_INVALIDARG;    
  
    return hr;    
}    
```  
  
## Voir aussi  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [THREADPROPERTY\_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)