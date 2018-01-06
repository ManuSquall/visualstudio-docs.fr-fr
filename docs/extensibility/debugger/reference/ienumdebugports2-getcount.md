---
title: IEnumDebugPorts2::GetCount | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPorts2::GetCount
helpviewer_keywords: IEnumDebugPorts2::GetCount
ms.assetid: d714455c-e4fc-48dc-a6d4-7e8b5d7c1bce
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b13f262fcf77867439371081fa3eedbc26dd9780
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugports2getcount"></a>IEnumDebugPorts2::GetCount
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
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)