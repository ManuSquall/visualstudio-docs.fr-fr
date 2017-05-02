---
title: "IScriptEntry::SetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetSignature"
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetSignature
Définit les informations de type d'un objet de fonction d' `IScriptEntry` .  
  
## Syntaxe  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### Paramètres  
 `pti`  
 \[in\]  les informations de type.  
  
 `iMethod`  
 \[in\]  L'index de méthode dans l'objet d' `ITypeInfo` .  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Vous définissez les informations de type à l'aide de `IScriptEntry::SetSignature` ou d' [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md).  Les informations de type peuvent également être générées par l'entrée sur la représentation interne de fonction.  
  
## Voir aussi  
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)