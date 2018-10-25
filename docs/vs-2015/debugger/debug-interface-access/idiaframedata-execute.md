---
title: IDiaFrameData::execute | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 933b05bbd9e0ff93a9e132578a72fb44db8be945
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49859721"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Effectue le déroulement de pile et renvoie les résultats dans une interface de frame de parcours de pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
|E_DIA_INPROLOG|Impossible d’exécuter un frame de pile, tandis que dans le code de prologue.|  
|E_DIA_SYNTAX|Analyser l’erreur s’est produite dans le programme de frame.|  
|E_DIA_FRAME_ACCESS|Impossible de registres d’accès ou de la mémoire.|  
|E_DIA_VALUE|Erreur dans le calcul d’une valeur (par exemple, la division par zéro).|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée pendant le débogage pour dérouler la pile. Le [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objet est implémenté par l’application cliente pour recevoir des mises à jour aux registres et de fournir des méthodes utilisées par le `execute` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



