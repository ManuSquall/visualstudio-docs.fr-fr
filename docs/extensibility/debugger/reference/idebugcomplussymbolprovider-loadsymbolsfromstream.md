---
title: IDebugComPlusSymbolProvider::LoadSymbolsFromStream | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider::LoadSymbolsFromStream
- LoadSymbolsFromStream
ms.assetid: 1de272f0-24f4-4548-8b70-a205cddd4727
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8daf00c4463610e1b55bc4580a4ffa50962041f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcomplussymbolproviderloadsymbolsfromstream"></a>IDebugComPlusSymbolProvider::LoadSymbolsFromStream
Étant donnés le flux de données de symboles de débogage de charge.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadSymbolsFromStream(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   IStream*  pStream  
);  
```  
  
```csharp  
int LoadSymbolsFromStream(  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   ulong   baseAddress,  
   object  pUnkMetadataImport,  
   IStream pStream  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ulAppDomainID`  
 [in] Identificateur du domaine d’application.  
  
 `guidModule`  
 [in] Identificateur unique du module.  
  
 `baseAddress`  
 [in] Adresse mémoire de base.  
  
 `pUnkMetadataImport`  
 [in] Objet qui contient les métadonnées du symbole.  
  
 `pStream`  
 [in] Flux de données qui contient les symboles.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose la [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface. La méthode appelle la [LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md) (méthode).  
  
```cpp  
HRESULT CDebugSymbolProvider::LoadSymbolsFromStream(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* pUnkMetadataImport,  
    IStream* pStream  
)  
{  
    return LoadSymbolsFromStreamWithCorModule (ulAppDomainID, guidModule, baseOffset, pUnkMetadataImport, NULL, pStream);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)