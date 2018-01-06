---
title: IEnumDebugPrograms2::GetCount | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPrograms2::GetCount
helpviewer_keywords: IEnumDebugPrograms2::GetCount
ms.assetid: 84832982-fa68-4090-a5b7-b233817876b7
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c74e14ee32d58a638cc4c60f98aca1ca26e4c075
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugprograms2getcount"></a>IEnumDebugPrograms2::GetCount
Retourne le nombre d’éléments dans l’énumération.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcelt`  
 [out] Retourne le nombre d’éléments dans l’énumération.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode n’est pas partie de l’interface d’énumération COM habituel qui spécifie que seules les `Next`, `Clone`, `Skip`, et `Reset` les méthodes doivent être implémentées.  
  
## <a name="see-also"></a>Voir aussi  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)