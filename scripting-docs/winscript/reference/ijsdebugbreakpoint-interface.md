---
title: Interface IJsDebugBreakPoint | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 791c8488-21e7-46be-b1b4-fe74117cf200
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c43d23d0ba89e6b85a3dd4da688fa89fed4dd99
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093845"
---
# <a name="ijsdebugbreakpoint-interface"></a>IJsDebugBreakPoint, interface
Représente un point d’arrêt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
IJsDebugBreakPoint : public IUnknown;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[Méthode IJsDebugBreakPoint::Delete](../../winscript/reference/ijsdebugbreakpoint-delete-method.md)|Supprime le point d'arrêt.|  
|[Méthode IJsDebugBreakPoint::Disable](../../winscript/reference/ijsdebugbreakpoint-disable-method.md)|Désactive le point d’arrêt.|  
|[Méthode IJsDebugBreakPoint::Enable](../../winscript/reference/ijsdebugbreakpoint-enable-method.md)|Active le point d’arrêt.|  
|[Méthode IJsDebugBreakPoint::GetDocumentPosition](../../winscript/reference/ijsdebugbreakpoint-getdocumentposition-method.md)|Retourne la position de l’instruction où le point d’arrêt a été lié.|  
|[Méthode IJsDebugBreakPoint::IsEnabled](../../winscript/reference/ijsdebugbreakpoint-isenabled-method.md)|Détermine si le point d’arrêt est activé.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** jscript9diag.h  
  
## <a name="see-also"></a>Voir aussi  
 [Référence d’interfaces de script Windows](../../winscript/reference/windows-script-interfaces-reference.md)