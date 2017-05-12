---
title: "IDispatchEx::GetNameSpaceParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNameSpaceParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNameSpaceParent (méthode)"
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNameSpaceParent
Récupère l'interface pour le parent de l'espace de noms d'un objet.  
  
## Syntaxe  
  
```  
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### Paramètres  
 `ppunk`  
 Adresse d'un pointeur d'interface de `IUnknown` qui accepte l'interface du parent de l'espace de noms.  
  
## Valeur de retour  
 Retourne `S_OK` si l'opération a réussi ou code d'erreur défini par OLE sinon.  
  
## Voir aussi  
 [IDispatchEx, interface](../../winscript/reference/idispatchex-interface.md)