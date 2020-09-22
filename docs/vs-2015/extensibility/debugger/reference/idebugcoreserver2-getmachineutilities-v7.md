---
title: 'IDebugCoreServer2 :: GetMachineUtilities_V7 | Microsoft Docs'
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
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840154"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode obtient les utilitaires d’ordinateur pour un serveur.  
  
> [!NOTE]
> Cette méthode est obsolète : n’utilisez pas ( [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] retourne toujours `E_NOTIMPL` la valeur si cette méthode est appelée). Elle est conservée pour des raisons historiques.  
  
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
 à Retourne une `IDebugMDMUtil2_V7` interface qui représente les informations sur les utilitaires de l’ordinateur.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne toujours `E_NOTIMPL` , indiquant que la méthode n’est pas implémentée.  
  
## <a name="remarks"></a>Remarques  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] retourne toujours `E_NOTIMPL` la valeur si cette méthode est appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
