---
title: "IDebugObject2::IsUserData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsUserData"
helpviewer_keywords: 
  - "IDebugObject2::IsUserData (méthode)"
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::IsUserData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Détermine si l'objet représente les données de l'utilisateur.  
  
## Syntaxe  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```c#  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### Paramètres  
 `pfUser`  
 \[out\]  Retourne une valeur différente de zéro \(`TRUE`\) si l'objet représente des données utilisateur ; zéro \(`FALSE`\) dans le cas contraire.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Les données d'utilisateur est un objet qui fait partie d'un module indiqué comme JustMyCode \(une option utilisateur\-configurable qui marque un module comme le code utilisateur et par conséquent visible dans une trace de la pile\).  
  
## Voir aussi  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)