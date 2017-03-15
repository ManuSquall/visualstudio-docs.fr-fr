---
title: "IDebugProperty3::DestroyObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::DestroyObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::DestroyObjectID"
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Détruit l'identificateur unique associé à cette propriété, indiquant que l'appelant ne s'inquiète plus pour identifier cette propriété uniquement de toutes les autres propriétés.  
  
## Syntaxe  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```c#  
int DestroyObjectID();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Si le moteur de débogage n'a pas besoin de prendre en charge des identificateurs uniques pour une propriété \(parce qu'il les suit déjà uniquement en interne\), il peut simplement retourner `E_NOTIMPL` de cette méthode.  
  
 Les identificateurs uniques sont créés avec un appel à la méthode d' [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) lorsque l'appelant veut vous assurer que cette propriété est identifiée parmi les autres propriétés.  
  
## Voir aussi  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)