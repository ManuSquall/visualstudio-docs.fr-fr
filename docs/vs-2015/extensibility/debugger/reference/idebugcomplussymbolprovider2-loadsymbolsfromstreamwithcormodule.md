---
title: IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
- LoadSymbolsFromStreamWithCorModule
ms.assetid: f79b894f-52c4-43c2-9a68-c71536451f6c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: edb3ab54ae7ce87b4d23f54c21627ce4ca791e4c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951261"
---
# <a name="idebugcomplussymbolprovider2loadsymbolsfromstreamwithcormodule"></a>IDebugComPlusSymbolProvider2::LoadSymbolsFromStreamWithCorModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Charger des symboles de débogage à partir d’un flux de données étant donné la **ICorDebugModule** objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT LoadSymbolsFromStreamWithCorModule(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONGLONG baseAddress,  
   IUnknown* pUnkMetadataImport,  
   IUnknown* pUnkCorDebugModule,  
   IStream*  pStream  
);  
```  
  
```csharp  
int LoadSymbolsFromStreamWithCorModule(  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   ulong   baseAddress,  
   object  pUnkMetadataImport,  
   object  pUnkCorDebugModule,  
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
 [in] Objet qui contient les métadonnées de symbole.  
  
 `pUnkCorDebugModule`  
 [in] Objet qui implémente le [ICorDebugModule (Interface)](/dotnet/framework/unmanaged-api/debugging/icordebugmodule-interface).  
  
 `pStream`  
 [in] Flux de données qui contient les symboles de débogage à charger.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose le [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) interface.  
  
```cpp#  
HRESULT CDebugSymbolProvider::LoadSymbolsFromStreamWithCorModule(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    ULONGLONG baseOffset,  
    IUnknown* pUnkMetadataImport,  
    IUnknown* pUnkCorDebugModule,  
    IStream* pStream  
)  
{  
    CAutoLock Lock(this);  
  
    HRESULT hr = S_OK;  
    CComPtr<IMetaDataImport> pMetadata;  
    CComPtr<ICorDebugModule> pCorModule;  
  
    CModule* pmodule = NULL;  
    CModule* pmoduleNew = NULL;  
    bool fAlreadyLoaded = false;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    DWORD dwCurrentState = 0;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pUnkMetadataImport, IUnknown));  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbolsFromStream );  
  
    IfFalseGo( pUnkMetadataImport, E_INVALIDARG );  
    IfFalseGo( pUnkCorDebugModule, E_INVALIDARG );  
  
    IfFailGo( pUnkMetadataImport->QueryInterface( IID_IMetaDataImport,  
              (void**)&pMetadata) );  
  
    IfFailGo( pUnkCorDebugModule->QueryInterface( IID_ICorDebugModule,  
              (void**)&pCorModule) );  
  
    ASSERT(guidModule != GUID_NULL);  
  
    fAlreadyLoaded = GetModule( idModule, &pmodule ) == S_OK;  
  
    IfNullGo( pmoduleNew = new CModule, E_OUTOFMEMORY );  
  
    dwCurrentState = m_pSymProvGroup ? m_pSymProvGroup->GetCurrentState() : 0;  
  
    IfFailGo( pmoduleNew->Create( idModule,  
                                  dwCurrentState,  
                                  pMetadata,  
                                  pCorModule,  
                                  pStream,  
                                  baseOffset ) );  
  
    if (fAlreadyLoaded)  
    {  
        IfFailGo(pmoduleNew->AddEquivalentModulesFrom(pmodule));  
        RemoveModule(pmodule);  
    }  
  
    IfFailGo( AddModule( pmoduleNew ) );  
  
Error:  
  
    RELEASE (pmodule);  
    RELEASE (pmoduleNew);  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbolsFromStream, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)

