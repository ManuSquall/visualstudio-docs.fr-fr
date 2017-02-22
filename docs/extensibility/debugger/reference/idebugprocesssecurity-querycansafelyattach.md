---
title: "IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::QueryCanSafelyAttach"
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode permet au fournisseur de port pour afficher un avertissement lorsque l'utilisateur se s'attache à un processus potentiellement dangereux.  
  
## Syntaxe  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```c#  
int QueryCanSafelyAttach();  
```  
  
## Valeur de retour  
 Les valeurs de retour sont les suivantes :  
  
-   `S_OK`: Attacher le traitement est sécurisé et aucune boîte de dialogue d'avertissement n'est affichée.  
  
-   `S_FALSE`: Attachement peut être un problème de sécurité et une boîte de dialogue avec un avertissement est affichée.  
  
-   `FAILURE`: Attachement pour traiter échoue.  
  
## Voir aussi  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)