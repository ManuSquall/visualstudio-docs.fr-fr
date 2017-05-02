---
title: "Propri&#233;t&#233;s d’erreurs sp&#233;ciales des m&#233;thodes asynchrones Windows Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45155584-06d8-4e7f-93a6-8564a93f643d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Propri&#233;t&#233;s d’erreurs sp&#233;ciales des m&#233;thodes asynchrones Windows Runtime
Déboguer les méthodes asynchrones Windows Runtime dans JavaScript peut se révéler être une tâche ardue, car l'erreur peut être levée d'un emplacement en profondeur dans la pile des appels.  L'objet JavaScript `Error` a des propriétés supplémentaires qui apparaissent uniquement lorsque l'erreur est levée d'une méthode asynchrone Windows Runtime et ce, lorsque l'application s'exécute en mode débogage.  
  
## Propriétés spéciales d'erreur  
 Un objet d'erreur résultant d'une opération asynchrone Windows Runtime en mode débogage ayant échoué, a les propriétés spéciales suivantes :  
  
-   `asyncOpSource` \(Objet\) obtient des informations à propos de l'emplacement d'origine d'où l'appel a été effectué et qui a engendré une erreur.  La propriété `asyncOpSource.originatingCall` \(Chaîne\) affiche l'emplacement dans le code utilisateur étant à l'origine de l'opération asynchrone.  
  
-   l'asyncOpType \(Chaîne\) obtient le nom du type de l'opération asynchrone qui a déclenché l'erreur.  
  
 Pour plus d'informations sur les erreurs avec les opérations asynchrones, consultez :  
  
-   [How to handle errors with promises](http://msdn.microsoft.com/fr-fr/01d5a901-c4ea-46f6-8005-6d39c32203eb)  
  
-   [Dépannage des erreurs Windows Runtime](http://msdn.microsoft.com/fr-fr/1ef7d7df-82ac-441d-8ad0-54ab1318de64)