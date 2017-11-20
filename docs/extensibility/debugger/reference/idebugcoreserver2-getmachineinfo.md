---
title: IDebugCoreServer2::GetMachineInfo | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::GetInfo
helpviewer_keywords: IDebugCoreServer2::GetInfo
ms.assetid: 8fa1a1d3-9fcb-4fb3-bf4e-e7172ac08d77
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b434a33797fcd761a898234892e6a872b11d178
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver2getmachineinfo"></a>IDebugCoreServer2::GetMachineInfo
Récupère une description de l’ordinateur que le serveur de base est en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInfo(   
   MACHINE_INFO_FIELDS Fields,  
   MACHINE_INFO*       pMachineInfo  
);  
```  
  
```csharp  
int GetInfo(   
   enum_ MACHINE_INFO_FIELDS  Fields,  
   MACHINE_INFO[]             pMachineInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Fields`  
 [in] Une combinaison d’indicateurs à partir de la [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) énumération qui spécifient les champs de `pMachineInfo` doivent être remplis.  
  
 `pMachineInfo`  
 [dans, out] A [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) structure est remplie avec une description de l’ordinateur.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)