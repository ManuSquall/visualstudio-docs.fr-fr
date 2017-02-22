---
title: "IDebugPortSupplier2::CanAddPort | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

vérifie qu'un fournisseur de port peut ajouter de nouveaux ports.  
  
## Syntaxe  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```c#  
int CanAddPort();  
```  
  
## Valeur de retour  
 Si le port peut être ajouté, retourne `S_OK`; sinon, retourne `S_FALSE` pour n'indique pas de port peuvent être ajoutés à ce fournisseur de port.  
  
## Notes  
 Appelez cette méthode avant d'appeler la méthode d' [Ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) depuis la dernière méthode crée le port ainsi que l'ajout, qui peut être une opération qui prend du temps.  
  
## Voir aussi  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [Ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)