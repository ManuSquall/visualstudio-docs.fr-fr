---
title: DebugStackFrameDescriptor, structure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576549"
---
# <a name="debugstackframedescriptor-structure"></a>Structure DebugStackFrameDescriptor
Énumère les frames de pile et fusionne les résultats de plusieurs énumérateurs sur le même thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 Objet de frame de pile.  
  
 `dwMin`  
 Représentation dépendante de l’ordinateur de la plage d’adresses physiques inférieure associée à ce frame de pile.  
  
 `dwLim`  
 Représentation dépendante de l’ordinateur de la plage supérieure des adresses physiques associées à ce frame de pile.  
  
 `fFinal`  
 Indicateur qui signale que le frame est en cours de traitement.  
  
 `punkFinal`  
 Si ce paramètre n’est pas `NULL`, la fusion de l’énumérateur actuel doit s’arrêter et un nouveau doit être démarré. L’objet indique comment démarrer la nouvelle énumération.  
  
## <a name="remarks"></a>Notes  
 Le gestionnaire de débogage de processus utilise cette structure pour trier les frames de pile à partir de plusieurs moteurs de script. Par Convention, les piles augmentent. Par conséquent, sur les architectures où les piles s’étendent, les adresses doivent être complétées par des à la fois.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)