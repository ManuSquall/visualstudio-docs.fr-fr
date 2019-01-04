---
title: IDebugComPlusSymbolProvider::GetSymAttribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetSymAttribute
- GetSymAttribute
ms.assetid: 6cbaac92-a60b-4165-a7f5-c34407770f3c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26b9ccab159e95d1248de7efa620a6fccecc7164
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921391"
---
# <a name="idebugcomplussymbolprovidergetsymattribute"></a>IDebugComPlusSymbolProvider::GetSymAttribute
Récupère les symboles de débogage avec l’attribut parent donné pour le module spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSymAttribute (  
   ULONG32  ulAppDomainID,  
   GUID     guidModule,  
   _mdToken tokParent,  
   LPOLESTR pstrName,  
   ULONG32  cBuffer,  
   ULONG32* pcBuffer,  
   BYTE*    buffer  
);  
```  
  
```csharp  
int GetSymAttribute (  
   uint      ulAppDomainID,  
   Guid      guidModule,  
   int       tokParent,  
   string    pstrName,  
   uint      cBuffer,  
   out uint  pcBuffer,  
   out int[] buffer  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ulAppDomainID`  
 [in] Identificateur du domaine d’application.  
  
 `guidModule`  
 [in] Identificateur unique du module.  
  
 `tokParent`  
 [in] Jeton pour l’attribut parent.  
  
 `pstrName`  
 [in] Nom du module.  
  
 `cBuffer`  
 [in] Nombre d’octets requis pour la sortie `buffer`.  
  
 `pcBuffer`  
 [out] Longueur de la sortie `buffer`.  
  
 `buffer`  
 [out] Tableau qui contient les symboles.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter cette méthode pour un **CDebugSymbolProvider** objet qui expose le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) interface.  
  
```cpp  
HRESULT CDebugSymbolProvider::GetSymAttribute(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    _mdToken tokParent,  
    __in_z LPOLESTR pstrName,  
    ULONG32 cBuffer,  
    ULONG32 *pcBuffer,  
    BYTE buffer[])  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetSymAttribute );  
  
    IfFailGo( GetModule( idModule, &pModule) );  
  
    IfFailGo( pModule->GetSymAttribute( tokParent, pstrName, cBuffer, pcBuffer, buffer ) );  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetSymAttribute, hr);  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)