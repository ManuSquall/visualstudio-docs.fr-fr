---
title: "IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::DefineScriptBlock"
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::DefineScriptBlock
Indique au programme d'assistance qu'une plage spécifique de caractères est un bloc de script qui est géré par le moteur de script donné.  
  
## Syntaxe  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### Paramètres  
 `ulCharOffset`  
 \[in\]  emplacement du début du bloc de script.  
  
 `cChars`  
 \[in\]  Nombre de caractères dans le bloc de script.  
  
 `pas`  
 \[in\]  le moteur de script pour ce bloc de script.  
  
 `fScriptlet`  
 \[in\]  Réduisez qui indique si le bloc de script est un scriptlet.  
  
 `pdwSourceContext`  
 \[out\]  le contexte de source pour le bloc de script.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Intelligent un hôte peut utiliser cette méthode lorsque ses documents contiennent des blocs de script incorporé.  Un moteur de langage peut utiliser cette méthode lorsque son code contient les scripts incorporés d'autres langages.  
  
 Le moteur de script est chargé de toutes les recherches de coloration de syntaxe et de contexte de code dans le bloc de script.  
  
 La méthode d' `DefineScriptBlock` doit être appelée après le texte a été ajouté \(par exemple, à l'aide de la méthode d' `IDebugDocumentHelper::AddDBCSText` \) mais avant que le bloc de script a été analysé \(par exemple, à l'aide de la méthode d' `IActiveScriptParse ::ParseScriptText` \).  
  
## Voir aussi  
 [IDebugDocumentHelper, interface](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)