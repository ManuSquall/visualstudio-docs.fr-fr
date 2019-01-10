---
title: IDebugDocumentHelper::GetScriptBlockInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: fd12aff51c661c2ba5af9ef909bfa481d22101d6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095288"
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