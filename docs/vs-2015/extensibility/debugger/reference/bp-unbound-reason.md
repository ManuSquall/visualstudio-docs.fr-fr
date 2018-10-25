---
title: BP_UNBOUND_REASON | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5f98c13b2f87492d9aea1ea6d3cc03fd7bf4a1d3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834522"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Donne la raison pour laquelle qu'un point d’arrêt a été dissocié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
typedef DWORD BP_UNBOUND_REASON;  
```  
  
```csharp  
public enum enum_BP_UNBOUND_REASON {   
   BPUR_UNKNOWN           = 0x0000,  
   BPUR_CODE_UNLOADED     = 0x0002,  
   BPUR_BREAKPOINT_REBIND = 0x0003,  
   BPUR_BREAKPOINT_ERROR  = 0x0004  
};  
```  
  
## <a name="members"></a>Membres  
 BPUR_UNKNOWN  
 La raison est inconnue.  
  
 BPUR_CODE_UNLOADED  
 Le code qui contient le point d’arrêt a été déchargé.  
  
 BPUR_BREAKPOINT_REBIND  
 Le point d’arrêt a été reliée à un autre emplacement. Cela peut se produire après modification et continuer les opérations lorsque le point d’arrêt se déplace, ou lorsque le point d’arrêt est lié à un fichier avec un chemin d’accès qui n’est plus valide.  
  
 BPUR_ BREAKPOINT_ERROR  
 Le point d’arrêt est déterminé comme étant erreur après que qu’il est lié. Cela se produit pour les points d’arrêt managés dont les conditions ne sont plus valides.  
  
## <a name="remarks"></a>Notes  
 Retourné par la [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) (méthode).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)

