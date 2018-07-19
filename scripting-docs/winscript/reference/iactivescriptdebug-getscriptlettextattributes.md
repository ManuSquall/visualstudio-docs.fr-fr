---
title: IActiveScriptDebug::GetScriptletTextAttributes | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 909879030e5c6d26353d2003279d5c1ca7bacb74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724429"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Retourne les attributs de texte pour un scriptlet arbitraire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrCode`  
 [in] Le texte du scriptlet. Cette chaîne ne doit pas être null terminé.  
  
 `uNumCodeChars`  
 [in] Le nombre de caractères dans le texte du scriptlet.  
  
 `pstrDelimiter`  
 [in] Adresse de fin-de-scriptlet délimiteur. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, telles que les guillemets («), pour détecter la fin du scriptlet. Ce paramètre spécifie le délimiteur de l’hôte utilisé, ce qui permet au moteur de script pour fournir certains prétraitement primitifs conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur script utilise ces informations varient selon le moteur de script. Définissez ce paramètre avec la valeur NULL si l’hôte n’utilisez pas un délimiteur pour marquer la fin du scriptlet.  
  
 `dwFlags`  
 [in] Indicateurs associés le scriptlet. Peut être une combinaison des valeurs suivantes :  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Indique que les opérateurs de point et les identificateurs doivent être identifiés avec les indicateurs SOURCETEXT_ATTR_IDENTIFIER et SOURCETEXT_ATTR_MEMBERLOOKUP, respectivement.|  
|GETATTRFLAG_THIS|0 x 0100|Indique que l’identificateur de l’objet en cours doit être identifié avec l’indicateur SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Indique que le texte de commentaire et de contenu de chaîne doit être identifié avec l’indicateur SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [dans, out] Mémoire tampon devant contenir les attributs retournés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Un hôte actif qui implémente `IDebugDocumentText` interface cette méthode permet de déléguer les appels à la `IDebugDocumentText::GetText` (méthode).  
  
 Cet appel est fourni, car les scriptlets ont tendance à être des expressions et peut avoir une syntaxe différente d’un bloc de script. Si elles ont la même syntaxe, l’implémentation de cette méthode est identique à l’implémentation de la `GetScriptTextAttributes` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptDebug (Interface)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText (Interface)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)