---
title: IDebugDocumentHost::GetScriptTextAttributes | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 517b228bb46594d19ba6d2fdf41a68e22ac03c75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728529"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Retourne les attributs de texte d’un bloc de texte du document.  
  
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
 [in] Le texte de bloc de script. Cette chaîne n’a pas besoin de se terminer par null.  
  
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
|`E_NOTIMPL`|L’hôte utilise uniquement les attributs par défaut.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode retourne les attributs de texte pour un bloc arbitraire du texte du document. Il est acceptable pour les ordinateurs hôtes à retourner `E_NOTIMPL`, auquel cas les attributs par défaut sont utilisés.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocumentHost (Interface)](../../winscript/reference/idebugdocumenthost-interface.md)   
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)