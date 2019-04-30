---
title: Structure DebugStackFrameDescriptor | Microsoft Docs
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
ms.openlocfilehash: fddae48178ec6c56ce647f5c4f3a1bff3d81a980
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955192"
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
 L’objet de frame de pile.  
  
 `dwMin`  
 Représentation sous forme de dépendantes de l’ordinateur de la plage inférieure des adresses physiques associées à ce frame de pile.  
  
 `dwLim`  
 Représentation sous forme de dépendantes de l’ordinateur de la plage supérieure des adresses physiques associées à ce frame de pile.  
  
 `fFinal`  
 Indicateur qui indique que le frame est en cours de traitement.  
  
 `punkFinal`  
 Si ce paramètre n’est pas `NULL`, l’énumérateur en cours la fusion doit s’arrêter et démarrer un nouveau. L’objet indique comment démarrer la nouvelle énumération.  
  
## <a name="remarks"></a>Notes  
 Le Gestionnaire de débogage de processus utilise cette structure pour trier les frames de pile à partir de plusieurs moteurs de script. Par convention, les piles évoluent vers le bas. Par conséquent, sur les architectures où les piles évoluent, les adresses doivent être complétées à par deux.  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)