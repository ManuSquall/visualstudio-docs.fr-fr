---
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4042cf58ee34b5f49df601b94e1110f03e0b6f5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197549"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Effectue le déroulement de la pile et retourne les résultats dans une interface de frame de parcours de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `frame`  
 dans Objet [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) qui contient l’état des registres de frame.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Le tableau suivant indique les valeurs de retour possibles pour cette méthode.  
  
|Valeur|Description|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Impossible d’exécuter un frame de pile dans le code de prologue.|  
|E_DIA_SYNTAX|Erreur d’analyse rencontrée dans le programme Frame.|  
|E_DIA_FRAME_ACCESS|Impossible d’accéder aux registres ou à la mémoire.|  
|E_DIA_VALUE|Erreur dans le calcul d’une valeur (par exemple, Division par zéro).|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée pendant le débogage pour dérouler la pile. L’objet [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) est implémenté par l’application cliente pour recevoir des mises à jour des registres et pour fournir les méthodes utilisées par la `execute` méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
