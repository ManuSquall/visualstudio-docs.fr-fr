---
title: IDebugProgramDestroyEvent2::GetExitCode | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramDestroyEvent2::GetExitCode
helpviewer_keywords: IDebugProgramDestroyEvent2::GetExitCode
ms.assetid: 7f540cf6-e2d1-42b0-913e-a26d654b7659
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d075ddafb81bf30423842986317d4724b6b42e7c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramdestroyevent2getexitcode"></a>IDebugProgramDestroyEvent2::GetExitCode
Obtient le code de sortie du programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExitCode(   
   DWORD* pdwExit  
);  
```  
  
```csharp  
int GetExitCode(   
   out uint pdwExit  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pdwExit`  
 [out] Retourne le code de sortie du programme.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)