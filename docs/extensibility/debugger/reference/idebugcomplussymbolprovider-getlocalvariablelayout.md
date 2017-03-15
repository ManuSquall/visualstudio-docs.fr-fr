---
title: "IDebugComPlusSymbolProvider::GetLocalVariablelayout | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetLocalVariablelayout"
  - "IDebugComPlusSymbolProvider::GetLocalVariablelayout"
ms.assetid: b7328d85-e5e9-4d9f-bcd1-e7711fd33878
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugComPlusSymbolProvider::GetLocalVariablelayout
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Extrait la disposition des variables locales pour un ensemble de méthodes.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetLocalVariablelayout(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONG32   cMethods,  
   _mdToken  rgMethodTokens[],  
   IStream** pStreamLayout  
);  
```  
  
```c#  
int GetLocalVariablelayout(  
   uint        ulAppDomainID,  
   Guid        guidModule,  
   uint        cMethods,  
   int[]       rgMethodTokens,  
   out IStream pStreamLayout  
);  
```  
  
#### Paramètres  
 `ulAppDomainID`  
 \[in\]  identificateur du domaine d'application.  
  
 `guidModule`  
 \[in\]  identificateur unique du module.  
  
 `cMethods`  
 \[in\]  Numéro de jetons de méthode dans le tableau d' `rgMethodTokens` .  
  
 `rgMethodTokens`  
 \[in\]  Tableau de jetons de méthode.  
  
 `pStreamLayout`  
 \[out\]  Un flux de texte qui contient la disposition variable.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **de CDebugSymbolProvider** qui expose l'interface d' [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetLocalVariablelayout(  
    ULONG32 ulAppDomainID,   
    GUID guidModule,   
    ULONG32 cMethods,   
    _mdToken rgMethodTokens[],   
    IStream** ppStreamLayout)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetLocalVariablelayout);  
  
    CComPtr<ISymUnmanagedReader> symReader;  
    IfFailRet(GetSymUnmanagedReader(ulAppDomainID, guidModule, (IUnknown **) &symReader));  
    CComPtr<IStream> stream;  
    IfFailRet(CreateStreamOnHGlobal(NULL, true, &stream));  
  
    for (ULONG32 iMethod = 0; iMethod < cMethods; iMethod += 1)  
    {  
        CComPtr<ISymUnmanagedMethod> method;  
        IfFailRet(symReader->GetMethod(rgMethodTokens[iMethod], &method));  
        CComPtr<ISymUnmanagedScope> rootScope;  
        IfFailRet(method->GetRootScope(&rootScope));  
  
        //  
        // Add the method's variables to the stream  
        //  
        IfFailRet(AddScopeToStream(rootScope, 0, stream));  
  
        // do end of method marker  
        ULONG32 depth = 0xFFFFFFFF;  
        ULONG cb = 0;  
        IfFailRet(stream->Write(&depth, sizeof(depth), &cb));  
    }  
  
    LARGE_INTEGER pos;  
    pos.QuadPart = 0;  
    IfFailRet(stream->Seek(pos, STREAM_SEEK_SET, 0));  
    *ppStreamLayout = stream.Detach();  
  
    METHOD_EXIT(CDebugSymbolProvider::GetLocalVariablelayout, hr);  
    return hr;  
}  
```  
  
## Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)