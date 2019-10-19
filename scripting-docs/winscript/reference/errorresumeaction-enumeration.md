---
title: Énumération ERRORRESUMEACTION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad9b8598cb027c96f6fb6fad6f3d343e6058cfdb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575864"
---
# <a name="errorresumeaction-enumeration"></a>Énumération ERRORRESUMEACTION
Explique comment poursuivre à partir d'une erreur d'exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Réexécute l’instruction qui a généré l’erreur.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Permet au moteur de langage de gérer l’erreur.|  
|ERRORRESUMEACTION_SkipErrorStatement|Reprend l’exécution dans le code qui suit l’instruction qui a généré l’erreur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)