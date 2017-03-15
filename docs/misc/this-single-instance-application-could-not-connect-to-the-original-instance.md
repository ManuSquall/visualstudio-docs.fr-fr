---
title: "Impossible de connecter cette application &#224; instance unique &#224; l’instance d’origine | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrAppModel_SingleInstanceCantConnect"
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de connecter cette application &#224; instance unique &#224; l’instance d’origine
Impossible de connecter cette application à instance unique à l'instance d'origine. Ce problème peut avoir les causes suivantes :  
  
-   L'instance d'origine a cessé de répondre.  
  
-   L'application n'a pas l'autorisation de créer des objets du noyau. Pour plus d’informations sur les objets noyaux, consultez [Mutexes](../Topic/Mutexes.md).  
  
     Le nom de base des objets du noyau est une concaténation entre le GUID de l'assembly, le numéro de la version principale et le numéro de la version secondaire. Le nom de base pourrait être, par exemple, `3639f15d-9547-43da-8145-60da347829915.1`.  
  
### Pour corriger cette erreur lors du développement d’une application  
  
1.  Vérifiez que l’application continue de répondre.  
  
2.  Vérifiez que l’application dispose d’autorisations suffisantes pour créer des objets noyaux.  
  
3.  Redémarrez l’instance d’origine de l’application.  
  
4.  Redémarrez l’ordinateur pour annuler tout processus susceptible d’utiliser la ressource permettant de se connecter à l’application de l’instance d’origine.  
  
5.  Notez les circonstances dans lesquelles l’erreur s’est produite, puis contactez les services de support technique Microsoft.  
  
## Voir aussi  
 [NIB : Comment : spécifier le comportement d’instanciation pour une application \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/48539ad8-d960-4210-beab-ee65f6c6dc6e)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [PAVEOVER Support technique et accessibilité](http://msdn.microsoft.com/fr-fr/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)