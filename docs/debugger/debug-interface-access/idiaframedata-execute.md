---
title: IDiaFrameData::execute | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29b284e466ce751e86f488203b4b22c0c18c6573
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
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
  
|Valeur|Description|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Impossible d’exécuter un frame de pile dans le code de prologue.|  
|E_DIA_SYNTAX|Analyser l’erreur s’est produite dans le programme de frame.|  
|E_DIA_FRAME_ACCESS|Impossible de registres de l’accès ou de la mémoire.|  
|E_DIA_VALUE|Erreur dans le calcul d’une valeur (par exemple, une division par zéro).|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est appelée pendant le débogage pour dérouler la pile. Le [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objet est implémenté par l’application cliente pour recevoir des mises à jour aux registres et fournir les méthodes utilisées par le `execute` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)