---
title: IDebugExpressionContext ::P arseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573151"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Crée une expression de débogage pour le texte spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrCode`  
 dans Fournit le texte de l’expression ou des instructions.  
  
 `nRadix`  
 dans Base à utiliser.  
  
 `pstrDelimiter`  
 dans Délimiteur de bloc de fin de script. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, tel que deux guillemets simples (' '), pour détecter la fin du bloc de script. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script de fournir un prétraitement de primitive conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur de script utilise ces informations dépend du moteur de script. Définissez ce paramètre sur `NULL` si l’hôte n’a pas utilisé de délimiteur pour marquer la fin du bloc de script.  
  
 `dwFlags`  
 dans Combinaison des indicateurs de texte de débogage suivants :  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Indique que le texte est une expression par opposition à une instruction. Cet indicateur peut affecter la façon dont le texte est analysé par certaines langues.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Si une valeur de retour est disponible, elle est utilisée par l’appelant.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|N’autorisez pas les effets secondaires. Si cet indicateur est défini, l’évaluation de l’expression ne doit pas modifier l’état d’exécution.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Autorise les points d’arrêt pendant l’évaluation du texte. Si cet indicateur n’est pas défini, les points d’arrêt sont ignorés pendant l’évaluation du texte.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Autorise les rapports d’erreurs pendant l’évaluation du texte. Si cet indicateur n’est pas défini, les erreurs ne sont pas signalées à l’hôte pendant l’évaluation.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indique que l’expression doit être évaluée dans un contexte de code plutôt que d’exécuter l’expression elle-même|  
  
 `ppe`  
 à Retourne l’expression de débogage pour le texte spécifié.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée une expression de débogage pour le texte spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)