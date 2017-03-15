---
title: "IDebugProperty3::CreateObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::CreateObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::CreateObjectID"
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un identificateur unique pour que cette propriété garantit qu'elle est unique parmi les autres propriétés.  
  
## Syntaxe  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```c#  
int CreateObjectID();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode est appelée lorsque le gestionnaire de débogage de session souhaite vous assurer que cette propriété est identifiée parmi les autres propriétés.  Les installations \(DE\) de moteur de débogage cette méthode à moins que les propriétés qui sont traitées déjà sont identifiés.  Si le De ne prend pas en charge cette méthode, il retourne `E_NOTIMPL`.  
  
 Tout identificateur unique créé avec `CreateObjectID` est détruit lorsque la méthode d' [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) est appelée ; cela indique également la fin de le besoin d'identifier cette propriété.  
  
> [!NOTE]
>  Il n'existe aucune méthode pour récupérer cet identificateur unique, le De peut faire ce qu'il souhaite pour les identificateurs uniques lorsque la méthode d' `CreateObjectID` est appelée.  
  
## Voir aussi  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)