---
title: 'IActiveScriptDebug :: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57bd466965f6431a1418df1aa56cf6a7bbbc78cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576932"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Retourne les attributs de texte pour un bloc arbitraire de texte de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
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
 dans Texte du bloc de script. Il n’est pas nécessaire que cette chaîne se termine par null.  
  
 `uNumCodeChars`  
 dans Nombre de caractères dans le texte de bloc de script.  
  
 `pstrDelimiter`  
 dans Adresse du délimiteur de bloc de fin de script. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, tel que deux guillemets simples (' '), pour détecter la fin du bloc de script. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script de fournir un prétraitement de primitive conditionnelle (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur de script utilise ces informations dépend du moteur de script. Affectez la valeur NULL à ce paramètre si l’hôte n’a pas utilisé de délimiteur pour marquer la fin du bloc de script.  
  
 `dwFlags`  
 dans Indicateurs associés au bloc de script. Peut être une combinaison de ces valeurs :  
  
|Constante|valeur|Description|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Indique que les identificateurs et les opérateurs point doivent être identifiés avec les indicateurs SOURCETEXT_ATTR_IDENTIFIER et SOURCETEXT_ATTR_MEMBERLOOKUP, respectivement.|  
|GETATTRFLAG_THIS|0x0100|Indique que l’identificateur de l’objet actuel doit être identifié avec l’indicateur SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Indique que le contenu de chaîne et le texte de commentaire doivent être identifiés avec l’indicateur SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Mémoire tampon qui contient les attributs retournés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Un hôte actif qui implémente `IDebugDocumentText` interface peut utiliser cette méthode pour déléguer des appels à la méthode `IDebugDocumentText::GetText`.  
  
 Cette méthode pour les blocs de script ; la méthode `GetScriptletTextAttributes` concerne les scriptlets.  
  
## <a name="see-also"></a>Voir aussi  
 @No__t_1 de l' [interface IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)  
 [IActiveScriptDebug :: GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)    
 @No__t_1 de l' [interface IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)  
 [IDebugDocumentText :: GetText](../../winscript/reference/idebugdocumenttext-gettext.md)    
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)