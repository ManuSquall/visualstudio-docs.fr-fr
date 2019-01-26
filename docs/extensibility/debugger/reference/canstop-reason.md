---
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba5f493303fd3b667e51bcd1f71a02d35c8fbc6f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963058"
---
# <a name="canstopreason"></a>CANSTOP_REASON
Utilisé pour déterminer si un programme peut arrêter l’exécution après avoir atteint un point particulier dans l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
typedef DWORD CANSTOP_REASON;  
```  
  
```csharp  
public enum enum_CANSTOP_REASON {   
   CANSTOP_ENTRYPOINT = 0x0000,  
   CANSTOP_STEPIN     = 0x0001  
};  
```  
  
## <a name="members"></a>Membres  
 CANSTOP_ENTRYPOINT  
 Spécifie le point d’entrée du programme donné.  
  
 CANSTOP_STEPIN  
 Spécifie le pas à pas détaillé dans une fonction.  
  
## <a name="remarks"></a>Notes  
 Passé en tant qu’argument à la [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) méthode pour vérifier avec le Gestionnaire de Session de débogage (SDM) s’il s’agit OK arrêter après avoir atteint le point d’entrée du programme ou après l’exécution pas à pas dans une fonction ou méthode.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)