---
title: "IDebugDocumentHelper::GetScriptBlockInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.GetScriptBlockInfo
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::GetScriptBlockInfo"
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::GetScriptBlockInfo
Extrait la cuisinière des caractères et le moteur de script correspondant à un bloc de script.  
  
## Syntaxe  
  
```  
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### Paramètres  
 `dwSourceContext`  
 \[in\]  le contexte de source pour le bloc de script.  
  
 `ppasd`  
 \[out\]  le moteur de script pour ce bloc de script.  
  
 `piCharPos`  
 \[out\]  emplacement du début du bloc de script.  
  
 `cChars`  
 \[out\]  Nombre de caractères dans le bloc de script.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode extrait la cuisinière des caractères et le moteur de script correspondant à un bloc de script.  
  
## Voir aussi  
 [IDebugDocumentHelper, interface](../../winscript/reference/idebugdocumenthelper-interface.md)