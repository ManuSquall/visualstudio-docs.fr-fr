---
title: "D&#233;pannage des exceptions&#160;: System.OutOfMemoryException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "OutOfMemoryException (classe)"
ms.assetid: eb16f008-964e-40a1-91f6-6ad25fa82d5a
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.OutOfMemoryException
Une exception <xref:System.OutOfMemoryException> est levée lors de l'échec d'une tentative d'allocation de mémoire.  
  
## Conseils associés  
 **Si vous créez un tableau, assurez\-vous que la taille est correcte.**  
 Pour plus d’informations, les utilisateurs de Visual Basic peuvent consulter [Tableaux](/dotnet/visual-basic/programming-guide/language-features/arrays/index).  
  
 Pour plus d’informations, les utilisateurs de C\# peuvent consulter [Tableaux](/dotnet/csharp/programming-guide/arrays/index).  
  
 **Vérifiez que vous disposez d'une mémoire suffisante pour les besoins internes et les nouveaux objets managés.**  
 Si vous programmez sur [!INCLUDE[Compact](../extensibility/includes/compact_md.md)], le Common Language Runtime lève cette exception lorsque la mémoire n'est pas suffisante pour les besoins internes et les nouveaux objets managés. Pour empêcher cette exception, évitez de programmer de vastes méthodes qui consomment 64 Ko de mémoire ou davantage.  
  
## Notes  
 L'utilisation excessive de la mémoire managée est généralement provoquée par les situations suivantes :  
  
-   Lecture de groupes de données de grande taille dans la mémoire.  
  
-   Création d'un nombre excessif d'entrées de cache.  
  
-   Transfert ou téléchargement de fichiers de grande taille.  
  
-   Utilisation excessive d'expressions régulières ou de chaînes lors de l'analyse des fichiers.  
  
-   État d'affichage excessif.  
  
-   Trop grand nombre de données dans l'état de session ou trop grand nombre de sessions.  
  
 Cette exception peut être levée avec un message supplémentaire, "Espace de stockage insuffisant pour terminer l'opération", lors de l'appel d'une méthode sur un objet COM qui retourne un type défini par l'utilisateur contenant un tableau sécurisé \(un tableau de taille non fixe\). Elle provient du fait que le .NET Framework ne peut pas marshaler de champ de structure avec un type de tableau sécurisé.  
  
## Voir aussi  
 <xref:System.OutOfMemoryException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)