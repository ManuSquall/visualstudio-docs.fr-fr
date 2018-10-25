---
title: IDebugSymbolProvider::GetLanguage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4987074e63f26a91d890066b3b74240989745197
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947951"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Cette méthode obtient le langage ayant servi à compiler le code à l’adresse de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLanguage(   
   IDebugAddress* pAddress,  
   GUID*          pguidLanguage,  
   GUID*          pguidLanguageVendor  
);  
```  
  
```csharp  
int GetLanguage(  
   IDebugAddress pAddress,   
   out Guid      pguidLanguage,   
   out Guid      pguidLanguageVendor  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAddress`  
 [in] Un type d’objet représenté par un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
 `pguidLanguage`  
 [out] Retourne un `GUID` qui spécifie le langage.  
  
 `pguidLanguageVendor`  
 [out] Retourne un `GUID` qui spécifie le fournisseur de langage.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le moteur de débogage appelle cette méthode pour obtenir les informations nécessaires sélectionner l’évaluateur d’expression correcte.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)