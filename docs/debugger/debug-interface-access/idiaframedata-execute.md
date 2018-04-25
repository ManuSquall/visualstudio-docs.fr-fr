---
title: IDiaFrameData::execute | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0645d2364712769a6b4f18ef14fbbcb503a51888
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Effectue le déroulement de pile et retourne les résultats dans une interface de frame de parcours de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `frame`  
 [in] Un [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objet qui contient l’état des registres de frame.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant montre les valeurs de retournés possibles pour cette méthode.  
  
|Value|Description|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Impossible d’exécuter un frame de pile dans le code de prologue.|  
|E_DIA_SYNTAX|Analyser l’erreur s’est produite dans le programme de frame.|  
|E_DIA_FRAME_ACCESS|Impossible de registres de l’accès ou de la mémoire.|  
|E_DIA_VALUE|Erreur dans le calcul d’une valeur (par exemple, une division par zéro).|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée pendant le débogage pour dérouler la pile. Le [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objet est implémenté par l’application cliente pour recevoir des mises à jour aux registres et fournir les méthodes utilisées par le `execute` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)