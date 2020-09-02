---
title: CANSTOP_REASON | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CANSTOP_REASON
helpviewer_keywords:
- CANSTOP_REASON enumeration
ms.assetid: 6da944eb-36cd-4a8c-8d71-544c775cfcc1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 277164ea3dfcdabbe24622bb5148ebd75d54f8c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561847"
---
# <a name="canstop_reason"></a>CANSTOP_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Utilisé pour déterminer si un programme peut arrêter l’exécution après avoir atteint un point particulier dans l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 Passé en tant qu’argument à la méthode [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) pour confirmer auprès du gestionnaire de débogage de session (SDM) s’il est possible de s’arrêter après avoir atteint le point d’entrée du programme ou après avoir effectué un pas à pas détaillé dans une fonction ou une méthode.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
