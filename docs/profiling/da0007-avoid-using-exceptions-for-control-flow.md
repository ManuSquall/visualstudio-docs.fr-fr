---
title: "DA0007&#160;: Ne pas utiliser d&#39;exceptions pour le flux de contr&#244;le | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAExceptionsThrown"
  - "vs.performance.7"
  - "vs.performance.rules.DA0007"
  - "vs.performance.DA0007"
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# DA0007&#160;: Ne pas utiliser d&#39;exceptions pour le flux de contr&#244;le
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID de la règle|DA0007|  
|Catégorie|Utilisation du .NET Framework|  
|Méthodes de profilage|Tous|  
|Message|De nombreuses exceptions sont levées.  Réduisez l'utilisation d'exceptions dans la logique du programme.|  
|Type de message|Avertissement|  
  
 Lorsque vous profilez en utilisant les méthodes d'échantillonnage, de mémoire. NET ou de conflits de ressources, vous devez collecter au moins 25 échantillons pour déclencher cette règle.  
  
## Cause  
 Un taux élevé de gestionnaires d'exceptions .NET Framework a été appelé dans les données de profilage.  Utilisez une autre logique de flux de contrôle pour réduire le nombre d'exceptions levées.  
  
## Description de la règle  
 Alors que l'utilisation de gestionnaires d'exceptions pour intercepter des erreurs et d'autres événements qui interrompent l'exécution du programme est une méthode conseillée, l'utilisation de gestionnaire d'exceptions dans le cadre de la logique d'exécution du programme normale peut être coûteuse et doit être évitée.  Dans la plupart des cas, les exceptions doivent être utilisées uniquement pour les circonstances qui se produisent rarement et ne sont pas attendues.  Les exceptions ne doivent pas être utilisées pour retourner des valeurs dans le cadre du flux normal du programme.  Dans de nombreux cas, vous pouvez éviter de déclencher des exceptions en validant des valeurs et en utilisant la logique conditionnelle pour arrêter l'exécution des instructions qui provoquent le problème.  
  
 Pour plus d'informations consultez [Gestion des exceptions](http://go.microsoft.com/fwlink/?LinkID=177825) la section " **Chapter 5 — Improving Managed Code Performance** dans le volume **Improving .NET Application Performance and Scalability** de la bibliothèque **Microsoft Patterns and Practices** sur MSDN.  
  
## Comment examiner un avertissement  
 Double\-cliquez sur le message dans la fenêtre Liste d'erreurs pour naviguer jusqu'à l'affichage Marques.  Recherchez la colonne qui contient les mesures **Exceptions CLR .NET\(@ProcessInstance\)\\Nombre d'exceptions levées\/s**.  Déterminez s'il y a des phases spécifiques d'exécution du programme où la gestion des exceptions est plus fréquente que d'autres.  À l'aide d'un profil d'échantillonnage, essayez d'identifier les instructions throw et les blocs try\/catch qui génèrent des exceptions fréquentes.  Si nécessaire, ajoutez la logique aux blocs catch pour vous aider à comprendre quelles exceptions sont le plus fréquemment gérées.  Lorsque c'est possible, remplacez des instructions throw ou des blocs catch exécutés fréquemment par la logique de contrôle de flux simple ou le code de validation.  
  
 Par exemple, si vous constatez que votre application gère des exceptions DivideByZeroException fréquentes, l'ajout d'une logique à votre programme pour rechercher des dénominateurs avec les valeurs zéro améliorera la performance de l'application.