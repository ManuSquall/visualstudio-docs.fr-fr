---
title: IActiveScriptDebug::GetScriptTextAttributes | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8e9cd76da3e754eabce836b386893043dcd0622
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Retourne les attributs de texte pour un bloc arbitraire de texte du script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pstrCode`  
 [in] Le texte de bloc de script. Cette chaîne ne doit pas être null terminé.  
  
 `uNumCodeChars`  
 [in] Le nombre de caractères dans le texte de bloc de script.  
  
 `pstrDelimiter`  
 [in] Adresse du délimiteur de fin du bloc de script. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, telles que les guillemets («), pour détecter la fin du bloc de script. Ce paramètre spécifie le délimiteur de l’hôte utilisé, ce qui permet au moteur de script pour fournir certains prétraitement primitifs conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur script utilise ces informations varient selon le moteur de script. Définissez ce paramètre avec la valeur NULL si l’hôte n’utilisez pas un délimiteur pour marquer la fin du bloc de script.  
  
 `dwFlags`  
 [in] Indicateurs associés au bloc de script. Peut être une combinaison des valeurs suivantes :  
  
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
  
 Cette méthode pour les blocs de script ; le `GetScriptletTextAttributes` méthode concerne les scriptlets.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptDebug (Interface)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [IDebugDocumentText (Interface)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)