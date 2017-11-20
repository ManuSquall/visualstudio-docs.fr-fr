---
title: IDebugExpressionContext::ParseLanguageText | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpressionContext.ParseLanguageText
apilocation: jscript.dll
helpviewer_keywords: IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e455768b7d38096c64ab61f2b36aeba871ddf0bc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
Crée une expression de débogage pour le texte spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Fournit le texte de l’expression ou une instruction (s).  
  
 `nRadix`  
 [in] Base à utiliser.  
  
 `pstrDelimiter`  
 [in] Le délimiteur de fin du bloc de script. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, telles que les guillemets («), pour détecter la fin du bloc de script. Ce paramètre spécifie le délimiteur de l’hôte utilisé, ce qui permet au moteur de script pour fournir certains prétraitement primitifs conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur script utilise ces informations varient selon le moteur de script. Définissez ce paramètre sur `NULL` si l’ordinateur hôte n’utilisez pas un délimiteur pour marquer la fin du bloc de script.  
  
 `dwFlags`  
 [in] Combinaison des indicateurs de texte de débogage suivants :  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|Indique que le texte est une expression, par opposition à une instruction. Cet indicateur peut affecter la façon dans lequel le texte est analysé par certains langages.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|Si une valeur de retour est disponible, il sera utilisé par l’appelant.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|N’autorisez pas les effets secondaires. Si cet indicateur est défini, l’évaluation de l’expression ne doit modifier aucun état d’exécution.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|Permet des points d’arrêt lors de l’évaluation du texte. Si cet indicateur n’est pas défini les points d’arrêt sont ignorés lors de l’évaluation du texte.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|Permet de rapports d’erreurs lors de l’évaluation du texte. Si cet indicateur n’est pas défini puis erreurs ne sont pas signalées à l’hôte lors de l’évaluation.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|Indique l’expression doit être évaluée à un contexte de code au lieu d’exécuter l’expression elle-même|  
  
 `ppe`  
 [out] Retourne l’expression de débogage pour le texte spécifié.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode crée une expression de débogage pour le texte spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugExpressionContext](../../winscript/reference/idebugexpressioncontext-interface.md)