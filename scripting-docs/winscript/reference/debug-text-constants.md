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
ms.openlocfilehash: facbdc1258b3fca72a239d9d5cc41772cf577f13
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577369"
---
# <a name="debug_text-constants"></a>DEBUG_TEXT, constantes
Utilisé pendant [IDebugExpressionContext ::P arselanguagetext](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>Constantes  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|Indique que le texte est une expression par opposition à une instruction. Cet indicateur peut affecter la façon dont le texte est analysé par certaines langues.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Si une valeur de retour est disponible, elle est utilisée par l’appelant.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|N’autorisez pas les effets secondaires. Si cet indicateur est défini, l’évaluation de l’expression ne doit pas modifier l’état d’exécution.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Autorisez les points d’arrêt pendant l’évaluation du texte. Si cet indicateur n’est pas défini, les points d’arrêt sont ignorés pendant l’évaluation du texte.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Autorisez les rapports d’erreurs pendant l’évaluation du texte. Si cet indicateur n’est pas défini, les erreurs ne sont pas signalées à l’hôte pendant l’évaluation.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indique que l’expression doit être évaluée dans un contexte de code plutôt que d’exécuter l’expression elle-même.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de débogueur de script actif, énumérations et structures](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)