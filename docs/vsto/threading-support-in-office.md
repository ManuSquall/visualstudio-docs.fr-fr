---
title: "Prise en charge des threads dans Office"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "threads multiples (développement Office dans Visual Studio)"
  - "modèles objet (développement Office dans Visual Studio), prise en charge du modèle de thread"
  - "applications Office (développement Office dans Visual Studio), prise en charge du modèle de thread"
  - "threads (développement Office dans Visual Studio)"
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2157
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Prise en charge des threads dans Office
  Cette rubrique fournit des informations sur la prise en charge des threads dans le modèle objet Microsoft Office.  Le modèle objet Office n'est pas thread\-safe, mais il est possible de travailler avec plusieurs threads dans une solution Office.  Les applications Office sont des serveurs COM \(Component Object Model\).  COM permet aux clients d'appeler des serveurs COM sur des threads arbitraires.  Pour les serveurs COM qui ne sont pas thread\-safe, COM fournit un mécanisme pour sérialiser les appels simultanés afin qu'un seul thread logique s'exécute sur le serveur à tout moment.  Ce mécanisme est connu sous le nom de modèle STA \(Single\-Threaded Apartment\).  Étant donné que les appels sont sérialisés, les appelants peuvent être bloqués pendant un certain temps alors que le serveur est occupé ou gère d'autres appels sur un thread d'arrière\-plan.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Connaissances requises pour les procédures multithread  
 Pour travailler avec plusieurs threads, vous devez au moins avoir des connaissances de base sur les aspects suivants du multithreading :  
  
-   les API Windows ;  
  
-   les concepts liés aux objets COM multithread ;  
  
-   l'accès concurrentiel ;  
  
-   Synchronisation  
  
-   le marshaling.  
  
 Pour des informations générales sur le multithreading, consultez [Multithreading in Components](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779).  
  
 Office s'exécute sur le STA principal.  Sachant ce que cela implique, il est plus facile de comprendre l'utilisation de plusieurs threads avec Office.  
  
## Scénario multithread de base  
 Le code dans les solutions Office s'exécute toujours sur le thread d'interface utilisateur principal.  Vous pouvez harmoniser les performances de l'application en exécutant une tâche séparée sur un thread d'arrière\-plan.  L'objectif est d'effectuer deux tâches apparemment en même temps au lieu d'une tâche après l'autre, ce qui devrait harmoniser leur exécution \(c'est la raison principale d'utiliser plusieurs threads\).  Par exemple, le code de l'événement peut s'exécuter sur le thread d'interface utilisateur Excel principal et, sur un thread d'arrière\-plan, vous pouvez exécuter une tâche qui rassemble les données d'un serveur et met à jour les cellules dans l'interface utilisateur Excel avec les données du serveur.  
  
## Threads d'arrière\-plan qui appellent le modèle objet Office  
 Lorsqu'un thread d'arrière\-plan appelle l'application Office, l'appel est marshalé automatiquement dans les limites du mode STA.  Toutefois, il n'existe aucune garantie que l'application Office puisse gérer l'appel au moment où le thread d'arrière\-plan l'émet.  Il existe plusieurs possibilités :  
  
1.  L'application Office doit pomper des messages pour l'appel pour avoir la possibilité de s'ouvrir.  Cela peut prendre du temps si le traitement est difficile et qu'aucun résultat n'est obtenu.  
  
2.  Le nouveau thread ne peut pas entrer si un autre thread logique se trouve déjà dans l'apartment.  Cela arrive souvent lorsqu'un thread logique entre dans l'application Office puis émet un rappel réentrant à l'apartment de l'appelant.  L'application est bloquée dans l'attente du retour de cet appel.  
  
3.  Excel peut être dans l'incapacité de gérer immédiatement un appel entrant.  Par exemple, il se peut que l'application Office affiche une boîte de dialogue modale.  
  
 Pour les possibilités 2 et 3, COM fournit l'interface [IMessageFilter](http://msdn.microsoft.com/fr-fr/e12d48c0-5033-47a8-bdcd-e94c49857248).  Si le serveur l'implémente, tous les appels entrent via une méthode appelée [HandleIncomingCall](http://msdn.microsoft.com/fr-fr/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be).  Pour la possibilité 2, les appels sont rejetés automatiquement.  Pour la possibilité 3, le serveur peut rejeter l'appel en fonction des circonstances.  Si l'appel est rejeté, l'appelant doit décider des actions suivantes.  Normalement, l'appelant implémente [IMessageFilter](http://msdn.microsoft.com/fr-fr/e12d48c0-5033-47a8-bdcd-e94c49857248), auquel cas le rejet serait notifié par la méthode [RetryRejectedCall](http://msdn.microsoft.com/fr-fr/3f800819-2a21-4e46-ad15-f9594fac1a3d).  
  
 Toutefois, dans le cas de solutions créées à l'aide des outils de développement Office dans Visual Studio, COM Interop convertit tous les appels rejetés en <xref:System.Runtime.InteropServices.COMException> \(« Le filtre de messages indique que l'application est occupée »\).  À chaque appel de modèle objet sur un thread d'arrière\-plan, vous devez vous attendre à gérer cette exception.  En général, vous devrez réessayer pendant un certain temps avant qu'une boîte de dialogue ne s'affiche.  Toutefois, vous pouvez également créer le thread d'arrière\-plan en tant que STA, puis enregistrer un filtre de messages pour ce thread afin de gérer cette situation.  
  
## Démarrage correct du thread  
 Lorsque vous créez un nouveau thread STA, définissez l'état de cloisonnement sur STA avant de démarrer le thread.  L'exemple de code suivant montre comment procéder.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/ThisWorkbook.vb#5)]  
  
 Pour plus d’informations, consultez [Managed Threading Best Practices](http://msdn.microsoft.com/library/e51988e7-7f4b-4646-a06d-1416cee8d557).  
  
## Formulaires non modaux  
 Un formulaire non modal permet certain type d'interaction avec l'application pendant qu'il est affiché.  L'utilisateur interagit avec le formulaire et le formulaire interagit avec l'application sans se fermer.  Le modèle objet Office prend en charge des formulaires non modaux managés. Toutefois, ils ne peuvent pas être utilisés sur un thread d'arrière\-plan.  
  
## Voir aussi  
 [Multithreading in Components](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)   
 [Managed Threading](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87)   
 [Threads &#40;C&#35; et Visual Basic&#41;](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)   
 [Using Threads and Threading](http://msdn.microsoft.com/library/9b5ec2cd-121b-4d49-b075-222cf26f2344)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)  
  
  