---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 977c7157ade60afe57b3564934319a34d140d81c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027657"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Cette méthode obtient les utilitaires machine pour un serveur.  
  
> [!NOTE]
>  Cette méthode est obsolète : n’utilisez pas ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] retourne toujours `E_NOTIMPL` si cette méthode est appelée). Elle est conservée pour des raisons historiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppUtil`  
 [out] Retourne un `IDebugMDMUtil2_V7` interface qui représente les informations sur les utilitaires des machine.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne toujours `E_NOTIMPL`, indiquant que la méthode n’est pas implémentée.  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Retourne toujours `E_NOTIMPL` si cette méthode est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)