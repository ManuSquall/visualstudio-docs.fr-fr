---
title: IDebugDocumentHost::GetScriptTextAttributes | Microsoft Docs
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
ms.openlocfilehash: 016073d2ce22ab814716efc204ce573ea17cd510
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092714"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Retourne les attributs de texte pour un bloc de texte du document.  
  
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
 [in] Le texte de bloc de script. Cette chaîne n’est pas obligé de se terminer par null.  
  
 `uNumCodeChars`  
 [in] Le nombre de caractères dans le texte de bloc de script.  
  
 `pstrDelimiter`  
 [in] Adresse du délimiteur de fin du bloc de script. Lorsque `pstrCode` est analysé à partir d’un flux de texte, l’hôte utilise généralement un délimiteur, telles que les deux guillemets («), pour détecter la fin du bloc de script. Ce paramètre spécifie le délimiteur utilisé par l’hôte, ce qui permet au moteur de script fournir un prétraitement primitif conditionnel (par exemple, en remplaçant un guillemet simple ['] par deux guillemets simples à utiliser comme délimiteur). Exactement comment (et si) le moteur script utilise ces informations varient selon le moteur de script. Définissez ce paramètre avec la valeur NULL si l’hôte n’utilisez pas un séparateur pour marquer la fin du bloc de script.  
  
 `dwFlags`  
 [in] Indicateurs associés au bloc de script. Peut être une combinaison des valeurs suivantes :  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Indique que les identificateurs et les opérateurs point doivent être identifiés avec les indicateurs SOURCETEXT_ATTR_IDENTIFIER et SOURCETEXT_ATTR_MEMBERLOOKUP, respectivement.|  
|GETATTRFLAG_THIS|0x0100|Indique que l’identificateur pour l’objet actif doit être identifié avec l’indicateur SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Indique que le texte de commentaire et de contenu de chaîne doit être identifié avec l’indicateur SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Mémoire tampon pour contenir les attributs retournés.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
|`E_NOTIMPL`|L’hôte utilise uniquement les attributs par défaut.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne les attributs de texte pour un bloc de texte du document arbitraire. Il est acceptable pour les ordinateurs hôtes à retourner `E_NOTIMPL`, auquel cas les attributs par défaut sont utilisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [Énumération SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)