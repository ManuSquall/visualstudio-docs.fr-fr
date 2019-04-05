---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6d615a24e9c6608713699904724a62d14569ee4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938288"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode obtient les utilitaires machine pour un serveur.  
  
> [!NOTE]
>  Cette méthode est obsolète : n’utilisez pas ([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] retourne toujours `E_NOTIMPL` si cette méthode est appelée). Elle est conservée pour des raisons historiques.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Retourne toujours `E_NOTIMPL` si cette méthode est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
