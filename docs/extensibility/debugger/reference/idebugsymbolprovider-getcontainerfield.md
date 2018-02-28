---
title: IDebugSymbolProvider::GetContainerField | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugSymbolProvider::GetContainerField
helpviewer_keywords:
- IDebugSymbolProvider::GetContainerField method
ms.assetid: d6b56b4f-a96b-4fa7-87c1-bac4e58fa766
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9f6f3f662605953e5350db89a236c1861fc42ab4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolprovidergetcontainerfield"></a>IDebugSymbolProvider::GetContainerField
Cette méthode obtient le champ qui contient l’adresse de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContainerField(   
   IDebugAddress*         pAddress,  
   IDebugContainerField** ppContainerField  
);  
```  
  
```csharp  
int GetContainerField(  
   IDebugAddress            pAddress,   
   out IDebugContainerField ppContainerField  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pAddress`  
 [in] L’adresse telle que représentée par une [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
 `ppContainerField`  
 [out] Retourne un champ conteneur représenté par une [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interface.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)