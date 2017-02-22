---
title: "IDebugProperty3::GetStringCharLength | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::GetStringCharLength"
helpviewer_keywords: 
  - "IDebugProperty3::GetStringCharLength"
ms.assetid: 89a8676b-6da9-4358-91c2-039bf33f99e4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty3::GetStringCharLength
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne le nombre de caractères dans la chaîne associée de la propriété.  
  
## Syntaxe  
  
```cpp  
HRESULT GetStringCharLength(  
   ULONG *pLen  
);  
```  
  
```c#  
int GetStringCharLength(  
   out uint pLen  
);  
```  
  
#### Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`pLen`|\[out\]  Retourne le nombre de caractères dans la chaîne de la propriété.|  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  
  
## Notes  
 En général, cette méthode est utilisée comme un prélude à allouer une mémoire tampon par un appel à la méthode d' [GetStringChars](../Topic/IDebugProperty3::GetStringChars.md) .  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **de CProperty** qui expose l'interface d' [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) .  
  
```cpp#  
STDMETHODIMP CProperty::GetStringCharLength(ULONG *pLen)  
{  
    HRESULT hr = E_INVALIDARG;  
  
    EVALFLAGS oldEVALFLAGS = m_EVALFLAGS;  
  
    m_EVALFLAGS &= ~EVAL_NOFUNCEVAL;  
  
    if (pLen)  
    {  
        DEBUG_PROPERTY_INFO dpInfo;  
        dpInfo.bstrValue = NULL;  
        ULONG ulen = 0;  
        hr = GetPropertyInfo(DEBUGPROP_INFO_VALUE,10,DEFAULT_TIMEOUT,NULL,0,&dpInfo);  
        if (hr == S_OK && dpInfo.bstrValue)  
        {  
            if (wcscmp(dpInfo.bstrValue,L"Nothing") == 0)  
            {  
                ulen = 0;   //VSWhidbey#64815  
            }  
            else  
            {  
                ulen = ::SysStringLen(dpInfo.bstrValue);  
                if( ulen > 2 &&  
                    dpInfo.bstrValue[0] == L'"' &&  
                    dpInfo.bstrValue[ulen-1] == L'"')  
                {                      
                    ulen = ulen > 2 ? ulen - 2 : ulen;  //remove two double quotes  
                }  
            }  
        }  
        ::SysFreeString(dpInfo.bstrValue);  
        *pLen = ulen;  
    }  
    m_EVALFLAGS = oldEVALFLAGS;  
    return hr;  
}  
```  
  
## Voir aussi  
 [GetStringChars](../Topic/IDebugProperty3::GetStringChars.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)