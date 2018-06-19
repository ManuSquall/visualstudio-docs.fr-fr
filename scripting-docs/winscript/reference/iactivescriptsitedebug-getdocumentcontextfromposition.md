---
title: IActiveScriptSiteDebug::GetDocumentContextFromPosition | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetDocumentContextFromPosition
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25ce03a124f246443afd0f5a8540a93e7d474f9a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724769"
---
# <a name="iactivescriptsitedebuggetdocumentcontextfromposition"></a>IActiveScriptSiteDebug::GetDocumentContextFromPosition
Utilisé par le moteur de langage pour déléguer `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwSourceContext`  
 [in] Le contenu de la source à `ParseScriptText` ou `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Un décalage relatif au début du bloc de script ou scriptlet de caractères.  
  
 `uNumChars`  
 [in] Nombre de caractères dans ce contexte.  
  
 `ppsc`  
 [out] Le contexte de document correspondant à cette étendue de la position de caractère.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Moteurs de langue permet de déléguer `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)