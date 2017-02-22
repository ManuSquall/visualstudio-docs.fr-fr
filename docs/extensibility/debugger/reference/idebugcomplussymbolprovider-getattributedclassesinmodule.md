---
title: "IDebugComPlusSymbolProvider::GetAttributedClassesinModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider::GetAttributedClassesinModule"
  - "GetAttributedClassesinModule"
ms.assetid: d8b087f3-1d32-4570-9eb0-7e0f7b051bc8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugComPlusSymbolProvider::GetAttributedClassesinModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère les classes avec l'attribut spécifié dans un module donné.  
  
## Syntaxe  
  
```  
[C++]  
HRESULT GetAttributedClassesinModule (  
   ULONG32            ulAppDomainID,  
   GUID               guidModule,  
   LPOLESTR           pstrAttribute,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```  
[C#]  
int GetAttributedClassesinModule (  
   uint                 ulAppDomainID,  
   Guid                 guidModule,  
   string               pstrAttribute,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Paramètres  
 `ulAppDomainID`  
 \[in\]  identificateur du domaine d'application.  
  
 `guidModule`  
 \[in\]  identificateur unique du module.  
  
 `pstrAttribute`  
 \[in\]  la chaîne d'attribut.  
  
 `ppEnum`  
 \[out\]  Retourne une énumération de classes réaffectées.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet **de CDebugSymbolProvider** qui expose l'interface d' [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetAttributedClassesinModule(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    __in_z LPOLESTR pstrAttribute,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    CComPtr<IMetaDataImport> pMetaData;  
    Module_ID idModule(ulAppDomainID, guidModule);  
    const void* pUnused;  
    ULONG cbUnused;  
    HCORENUM hEnum = 0;  
    ULONG cTypeDefs = 0;  
    ULONG cEnum;  
    DWORD iTypeDef = 0;  
    mdTypeDef* rgTypeDefs = NULL;  
    IDebugField** rgFields = NULL;  
    DWORD ctField = 0;  
    CEnumDebugFields* pEnumFields = NULL;  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetAttributedClassesinModule );  
  
    IfFalseGo( pstrAttribute && ppEnum , E_INVALIDARG );  
    IfFailGo( GetModule( idModule, &pModule ) );  
    pModule->GetMetaData( &pMetaData );  
  
    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                       NULL,  
                                       0,  
                                       &cTypeDefs ) );  
  
    IfFailGo( pMetaData->CountEnum( hEnum, &cEnum ) );  
    pMetaData->CloseEnum(hEnum);  
    hEnum = NULL;  
  
    IfNullGo( rgTypeDefs = new mdTypeDef[cEnum], E_OUTOFMEMORY );  
    IfNullGo( rgFields = new IDebugField * [cEnum], E_OUTOFMEMORY );  
  
    IfFailGo( pMetaData->EnumTypeDefs( &hEnum,  
                                       rgTypeDefs,  
                                       cEnum,  
                                       &cTypeDefs ) );  
  
    for ( iTypeDef = 0; iTypeDef < cTypeDefs; iTypeDef++)  
    {  
  
        if (pMetaData->GetCustomAttributeByName( rgTypeDefs[iTypeDef],  
                pstrAttribute,  
                &pUnused,  
                &cbUnused ) == S_OK)  
        {  
            if (CreateClassType( idModule, rgTypeDefs[iTypeDef], rgFields + ctField) == S_OK)  
            {  
                ctField++;  
            }  
            else  
            {  
                ASSERT(!"Failed to Create Attributed Class");  
            }  
        }  
    }  
  
    IfNullGo( pEnumFields = new CEnumDebugFields, E_OUTOFMEMORY );  
    IfFailGo( pEnumFields->Initialize(rgFields, ctField) );  
    IfFailGo( pEnumFields->QueryInterface( __uuidof(IEnumDebugFields),  
                                           (void**) ppEnum ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetAttributedClassesinModule, hr );  
  
    DELETERG( rgTypeDefs );  
  
    for ( iTypeDef = 0; iTypeDef < ctField; iTypeDef++)  
    {  
        RELEASE( rgFields[iTypeDef] );  
    }  
  
    DELETERG( rgFields );  
    RELEASE( pEnumFields );  
  
    return hr;  
}  
```  
  
## Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)