---
title: "Énumération ERRORRESUMEACTION | Documents Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 914c1d7aa4d2935ea94322ebd257f4135d79e9c0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="errorresumeaction-enumeration"></a>Énumération ERRORRESUMEACTION
Explique comment poursuivre à partir d'une erreur d'exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Permet de gérer l’erreur le moteur de langage.|  
|ERRORRESUMEACTION_SkipErrorStatement|Reprend l’exécution dans le code qui suit l’instruction qui a généré l’erreur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)