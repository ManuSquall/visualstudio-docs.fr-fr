---
title: IDebugSymbolProviderDirect::GetCurrentModulesState | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- GetCurrentModulesState
- IDebugSymbolProviderDirect::GetCurrentModulesState
ms.assetid: a0c85318-5686-4eed-b213-21f2b9e681e6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc16ce17ed9499036d4eaf29a39d1616eed54c7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857157"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesstate"></a>IDebugSymbolProviderDirect::GetCurrentModulesState
Récupère des informations sur le groupe de symboles dont le fournisseur de symboles est un membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentModulesState(  
    DWORD*          pState,  
    unsigned long * count  
);  
```  
  
```csharp  
int GetCurrentModulesState(  
    out uint pState,  
    out uint count  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pState`  
 [out] L’état du groupe de fournisseur de symboles.  
  
 `count`  
 [out] Nombre de modules dans le groupe.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 L’état est modifié chaque fois qu’un module est ajouté ou supprimé, le groupe de symboles. Par conséquent, cette méthode peut être utilisée pour détecter si un groupe de symboles a été modifié.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)