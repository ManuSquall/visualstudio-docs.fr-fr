---
title: "IScriptEntry::GetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetSignature"
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetSignature
Les informations de type de retour pour un objet de fonction d' `IScriptEntry` .  
  
## Syntaxe  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### Paramètres  
 `ppti`  
 \[out\]  Les informations de type associées à cet objet de fonction d' `IScriptEntry` .  
  
 `piMethod`  
 \[out\]  Index de méthode dans l'objet d' `ITypeInfo` .  
  
## Valeur de retour  
 Élément `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Vous définissez les informations de type à l'aide de [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) ou d' [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md).  Les informations de type peuvent également être générées par l'entrée sur la représentation interne de fonction.  
  
## Voir aussi  
 [IScriptEntry, interface](../../winscript/reference/iscriptentry-interface.md)