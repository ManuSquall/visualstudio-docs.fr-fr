---
title: 'IDebugComPlusSymbolProvider :: UpdateSymbols | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- UpdateSymbols
- IDebugComPlusSymbolProvider::UpdateSymbols
ms.assetid: d530f6f1-4af2-454b-bab0-02478a8fe81e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b208cadc8264bf3ddbd30d9316b9f0d5a7050b50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176748"
---
# <a name="idebugcomplussymbolproviderupdatesymbols"></a>IDebugComPlusSymbolProvider::UpdateSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Met à jour les symboles de débogage dans la mémoire avec ceux du flux de données spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT UpdateSymbols (  
   ULONG32  ulAppDomainID,  
   GUID     guidModule,  
   IStream* pUpdateStream  
);  
```  
  
```csharp  
int UpdateSymbols (  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   IStream pUpdateStream  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ulAppDomainID`  
 dans Identificateur du domaine d’application.  
  
 `guidModule`  
 dans Identificateur unique du module.  
  
 `pUpdateStream`  
 dans Flux de données qui contient les symboles de débogage mis à jour.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un objet **CDebugSymbolProvider** qui expose l’interface [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::UpdateSymbols(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IStream* pUpdateStream  
)  
{  
    ASSERT(!"Use UpdateSymbols2 on IDebugENCSymbolProvider2");  
    return E_NOTIMPL;  
}  
  
HRESULT CDebugSymbolProvider::UpdateSymbols2(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IStream* pUpdateStream,  
    LINEDELTA* pDeltaLines,  
    ULONG cDeltaLines  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::UpdateSymbols );  
  
    IfFailGo( GetModule( idModule, &pModule ) );  
    IfFailGo( pModule->UpdateSymbols( pUpdateStream, pDeltaLines, cDeltaLines ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::UpdateSymbols, hr );  
  
    return hr;  
}  
```  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
