---
title: Constantes DEBUG_TEXT | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2342555c4ee92b403aa01cc0ca15bb805f2b002e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152796"
---
# <a name="debugtext-constants"></a>DEBUG_TEXT, constantes
Utilisé pendant [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Indique que le texte est une expression, par opposition à une instruction. Cet indicateur peut-être affecter le mode dans lequel le texte est analysé par certains langages.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Si une valeur de retour est disponible, il sera utilisé par l’appelant.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|Ne pas autoriser les effets secondaires. Si cet indicateur est défini, l’évaluation de l’expression ne doit changer aucun état d’exécution.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Autoriser les points d’arrêt lors de l’évaluation du texte. Si cet indicateur n’est pas défini, les points d’arrêt seront ignorés lors de l’évaluation du texte.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Autoriser les rapports d’erreurs lors de l’évaluation du texte. Si cet indicateur n’est pas défini, puis erreurs ne seront pas signalées à l’hôte lors de l’évaluation.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indique que l’expression doit être évaluée à un contexte de code au lieu de l’expression elle-même en cours d’exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)