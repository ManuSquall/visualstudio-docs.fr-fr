---
title: IDebugDocumentHelper::GetScriptBlockInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetScriptBlockInfo
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1984cdc19beb883dd7ee82f58497b11a8d781b0
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144431"
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
Récupère la plage de caractères et le moteur de script correspondant à un bloc de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwSourceContext`  
 [in] Le contexte de la source pour le bloc de script.  
  
 `ppasd`  
 [out] Le moteur de script pour ce bloc de script.  
  
 `piCharPos`  
 [out] Emplacement du début du bloc de script.  
  
 `cChars`  
 [out] Nombre de caractères dans le bloc de script.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne `HRESULT`. Les valeurs possibles sont notamment celles figurant dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode récupère la plage de caractères et le moteur de script correspondant à un bloc de script.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)