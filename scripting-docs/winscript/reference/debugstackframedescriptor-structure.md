---
title: Structure DebugStackFrameDescriptor | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c50c717cad626f4caf634c6a83b2af7213b78f83
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088476"
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