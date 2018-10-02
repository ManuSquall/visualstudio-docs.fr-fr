---
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e88ed8a93d77910d76cefefc0ee97c01f88de15b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506531"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugBinder3::GetAllAliases](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder3-getallaliases).  
  
Cette méthode récupère une liste d’alias à partir du programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `uRequest`  
 [in] Le nombre maximal d’alias à retourner (spécifie la longueur du tableau passé dans `ppAliases`).  
  
 `ppAliases`  
 [in, out] Tableau à remplir avec des alias (s’il s’agit d’une valeur null et `uRequest` est 0, le nombre d’alias qui peuvent être retournées est renvoyé par `puFetched`).  
  
 `puFetched`  
 [out] Retourne le nombre d’alias obtenu.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)

