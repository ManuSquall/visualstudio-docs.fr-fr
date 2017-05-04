---
title: "Fonction Debug.msUpdateAsyncCallbackRelation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Fonction Debug.msUpdateAsyncCallbackRelation
Met à jour l'état de la relation entre un élément de travail synchrone et l'opération asynchrone associée.  
  
## Syntaxe  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### Paramètres  
 `relatedAsyncOperationId`  
 Requis.  ID associé à l'opération asynchrone.  
  
 `relationType`  
 Facultatif.  Valeur qui spécifie l'état de relation.  
  
## Notes  
 L'élément de travail synchrone est généralement la fonction de rappel pour l'opération asynchrone.  Cette fonction peut être appelée lorsqu'une opération asynchrone est abandonnée, qu'une opération de jointure est utilisée ou dans d'autres scénarios.  
  
 Les valeurs possibles pour `relationType` sont les suivantes :  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 Pour plus d'informations, consultez la rubrique sur les [constantes Debug](../../javascript/reference/debug-constants.md).  
  
> [!NOTE]
>  Certains outils de débogage n'affichent pas les informations envoyées au débogueur par cette fonction.  
  
## Configuration requise  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]