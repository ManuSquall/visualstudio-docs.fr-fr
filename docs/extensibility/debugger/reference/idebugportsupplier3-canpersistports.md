---
title: "IDebugPortSupplier3::CanPersistPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode détermine si le fournisseur de port peut conserver des ports \(en les entrant sur le disque\) entre les appels du débogueur.  
  
## Syntaxe  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```c#  
int CanPersistPorts();  
```  
  
#### Paramètres  
 Aucun  
  
## Valeur de retour  
 `S_OK` si les ports peuvent être persistants, ou `S_FALSE` pour indiquer que les ports ne peuvent pas être persistants.  
  
## Notes  
 Si le fournisseur de port peut conserver des ports, elle doit le faire par lorsqu'il est détruit et les recharger ensuite lorsqu'il est instancié à nouveau.  
  
## Voir aussi  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)