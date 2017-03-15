---
title: "Rechercher des probl&#232;mes potentiels &#224; l’aide des analyseurs de carte du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.progression.codemapanalyzers"
helpviewer_keywords: 
  - "analyse du code, graphiques de dépendance"
  - "graphiques de dépendance, analyse du code"
  - "documents de graphique, analyser"
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 11
author: "alexhomer1"
ms.author: "ahomer"
manager: "douge"
caps.handback.revision: 11
---
# Rechercher des probl&#232;mes potentiels &#224; l’aide des analyseurs de carte du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Exécutez des analyseurs sur des cartes de code pour vous aider à identifier le code susceptible d’être trop complexe ou de devoir être amélioré. Vous pouvez par exemple utiliser ces analyseurs :  
  
|**Pour rechercher du code ayant**|**Examinez ces zones pour voir si**|  
|---------------------------------------|-----------------------------------------|  
|Des boucles ou des dépendances circulaires|Vous pouvez les simplifier et envisager de rompre ces cycles.|  
|Trop de dépendances|Elles exécutent trop de fonctions ou pour déterminer l’impact de la modification de ces zones. Une carte de code correcte affiche un nombre minimal de dépendances. Pour que le code soit plus facile à tenir à jour, à modifier, à tester et à réutiliser, essayez de refactoriser ces zones pour qu’elles soient plus clairement définies ou de fusionner du code qui exécute des fonctions similaires.|  
|Aucune dépendance|Elles sont nécessaires ou si vous devez supprimer ce code.|  
  
## Analyser les cartes de code  
  
1.  Dans la barre d’outils de carte, choisissez **Disposition**, **Analyseurs**, puis sélectionnez l’analyseur que vous souhaitez exécuter :  
  
    |**Analyseur**|**Pour identifier les nœuds qui**|  
    |-------------------|---------------------------------------|  
    |**Analyseur de références circulaires**|Ont des dépendances circulaires les unes envers les autres. **Note:**  Les dépendances circulaires qui se trouvent dans le groupe **Génériques** ne figurent pas sur la carte quand vous développez le groupe.|  
    |**Rechercher l’analyseur de hubs**|Figurent dans les premiers 25 % des nœuds hautement connectés<br /><br /> **Pour masquer tous les autres nœuds de la carte**<br /><br /> -   Ouvrez le menu contextuel de la carte, sélectionnez **Avancé**, **Sélectionner**, **Masquer les éléments non sélectionnés**.<br />     La carte masque les nœuds non sélectionnés et l’analyseur identifie les nouveaux nœuds en tant que hubs.|  
    |**Analyseur de nœuds non référencés**|N’ont pas de références d’autres nœuds. **Caution:**  Vérifiez chacun de ces cas avant de supposer que le code n’est pas utilisé. Certaines dépendances, telles que les dépendances XAML et d’exécution, sont introuvables statiquement dans le code.|  
  
 Les analyseurs de carte de code continuent de s’exécuter après leur application. Si vous modifiez la carte, les analyseurs appliqués retraitent automatiquement la carte mise à jour. Pour arrêter l’exécution d’un analyseur, dans la barre d’outils de la carte, sélectionnez **Disposition**, **Analyseurs**. Désactivez l’analyseur sélectionné.  
  
> [!TIP]
>  Si votre carte est très grande, l’exécution d’un analyseur peut provoquer une exception en raison de mémoire insuffisante. Si cela se produit, modifiez la carte pour réduire sa portée ou générez\-en une plus petite, puis exécutez l’analyseur.  
  
## Voir aussi  
 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)   
 [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Mapper les méthodes sur la pile des appels tout en déboguant](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)