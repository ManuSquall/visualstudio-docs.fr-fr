---
title: 'IDebugCodeContext :: GetDocumentContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.GetDocumentContext
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::GetDocumentContext
ms.assetid: 9fe17b65-3a8c-4d21-9b66-0e4ff303af72
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dc1cda6164375f3434ee562b540e85268fe4c68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573228"
---
# <a name="idebugcodecontextgetdocumentcontext"></a>IDebugCodeContext::GetDocumentContext
Retourne le contexte de document associé à ce contexte de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppsc`  
 à Contexte de document associé à ce contexte de code.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|valeur|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Pour les documents texte, la plage de la position des caractères doit inclure le texte de l’instruction entière. Cela permet à l’IDE du débogueur de mettre en surbrillance l’instruction source actuelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugCodeContext](../../winscript/reference/idebugcodecontext-interface.md)