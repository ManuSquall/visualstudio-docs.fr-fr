---
title: IDebugDocumentHelper::CreateDebugDocumentContext | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.CreateDebugDocumentContext
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::CreateDebugDocumentContext
ms.assetid: aa4ec691-9fb1-4da7-8085-b40d8a062467
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54d91c4df9d1e478d028e95e5cfc930d69355c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726409"
---
# <a name="idebugdocumenthelpercreatedebugdocumentcontext"></a>IDebugDocumentHelper::CreateDebugDocumentContext
Crée un nouveau contexte de document de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateDebugDocumentContext(  
   ULONG                    iCharPos,  
   ULONG                    cChars,  
   IDebugDocumentContext**  ppddc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `iCharPos`  
 [in] Emplacement du début du contenu du document de débogage.  
  
 `cChars`  
 [in] Nombre de caractères dans le contexte.  
  
 `ppddc`  
 [out] Le nouveau contexte de document de débogage.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Remarques  
 Cette méthode permet à l’hôte créer un nouveau contexte de document de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)