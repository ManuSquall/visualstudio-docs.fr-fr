---
title: "D&#233;pannage des exceptions&#160;: System.StackOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "StackOverflowException (classe)"
ms.assetid: 51b71217-c507-4f5b-bc35-0236180d7968
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.StackOverflowException
Une exception <xref:System.StackOverflowException> est levée lorsque la capacité de la pile d'exécution est dépassée suite à un trop grand nombre d'appels à la méthode imbriqués.  
  
## Conseils associés  
 Assurez\-vous que vous n'avez pas une boucle infinie ou une récurrence infinie.  
 Un trop grand nombre d'appels à la méthode est généralement le signe d'une récurrence très profonde ou non liée.  
  
## Notes  
 Vous ne pouvez pas intercepter des exceptions de dépassement de capacité de la pile, car le code de gestion des exceptions peut requérir la pile. En revanche, lorsqu'un dépassement de capacité de la pile se produit dans une application normale, le Common Language Runtime \(CLR\) met fin au processus.  
  
 Une application qui héberge le CLR peut modifier le comportement par défaut et spécifier que le CLR décharge le domaine d'application où l'exception se produit, mais laisse le processus se poursuivre. Pour plus d'informations, consultez [ICLRPolicyManager, interface](../Topic/ICLRPolicyManager%20Interface.md).  
  
## Voir aussi  
 <xref:System.StackOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Loop Structures](/dotnet/visual-basic/programming-guide/language-features/control-flow/loop-structures)