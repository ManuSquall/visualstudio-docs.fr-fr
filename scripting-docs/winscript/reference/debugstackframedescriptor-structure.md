---
title: Structure DebugStackFrameDescriptor | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 346f039ca96f2160d7ac28686e542b3d88a91dfb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="debugstackframedescriptor-structure"></a>Structure DebugStackFrameDescriptor
Énumère les frames de pile et fusionne les résultats de plusieurs énumérateurs sur le même thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Membres  
 `pdsf`  
 L’objet de frame de pile.  
  
 `dwMin`  
 Représentation sous forme de dépendantes de l’ordinateur de la plage inférieure des adresses physiques, associé à ce frame de pile.  
  
 `dwLim`  
 Représentation sous forme de dépendantes de l’ordinateur de la plage supérieure des adresses physiques, associé à ce frame de pile.  
  
 `fFinal`  
 Indicateur qui indique que l’image est en cours de traitement.  
  
 `punkFinal`  
 Si ce paramètre n’est pas `NULL`, l’énumérateur en cours la fusion doit s’arrêter et un nouveau doit être démarré. L’objet indique comment démarrer la nouvelle énumération.  
  
## <a name="remarks"></a>Remarques  
 Le Gestionnaire de processus de débogage utilise cette structure pour trier les frames de pile à partir de plusieurs moteurs de script. Par convention, les piles évoluent vers le bas. Par conséquent, sur les architectures où piles évoluent, les adresses doivent être complété en deux.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)