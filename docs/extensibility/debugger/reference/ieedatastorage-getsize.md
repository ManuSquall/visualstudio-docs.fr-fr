---
title: "IEEDataStorage::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEDataStorage::GetSize"
helpviewer_keywords: 
  - "IEEDataStorage::GetSize"
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEDataStorage::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne le nombre d'octets contenus dans cet objet.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetSize(  
   ULONG* size  
);  
```  
  
```c#  
int GetSize(  
   out uint size  
);  
```  
  
#### Paramètres  
 `size`  
 \[out\]  le nombre d'octets contenus dans cet objet.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Utilisez la méthode d' [GetData](../Topic/IEEDataStorage::GetData.md) pour récupérer les octets de données réels.  
  
## Voir aussi  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../Topic/IEEDataStorage::GetData.md)