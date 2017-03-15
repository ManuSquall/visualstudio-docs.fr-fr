---
title: "Erreurs FxCopCmd | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FxCopCmd (erreurs)"
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# Erreurs FxCopCmd
FxCopCmd ne considère pas toutes les erreurs comme fatales.  Si FxCopCmd a des informations suffisantes pour effectuer une analyse partielle, il le fait et signale les erreurs qui se sont produites.  Le code d'erreur qui est un entier 32 bits contient une combinaison d'opérations de bits des valeurs numériques qui correspondent aux erreurs.  
  
 Le tableau suivant décrit les codes d'erreur retournés par FxCopCmd :  
  
|Erreur|Valeur numérique|  
|------------|----------------------|  
|Pas d'erreurs|0x0|  
|Erreur d'analyse|0x1|  
|Exceptions de règle|0x2|  
|Erreur de chargement du projet|0x4|  
|Erreur de chargement de l'assembly|0x8|  
|Erreur de chargement de la bibliothèque de la règle|0x10|  
|Erreur de chargement du rapport d'importation|0x20|  
|Erreur de sortie|0x40|  
|Erreur du commutateur de ligne de commande|0x80|  
|Erreur d'initialisation|0x100|  
|Erreur des références d'assembly|0x200|  
|BuildBreakingMessage|0x400|  
|Erreur inconnue|0x1000000|  
  
 L'erreur d'analyse est retournée pour les erreurs irrécupérables.  Elle indique que l'analyse n'a pas pu être terminée.  Lorsque cela est possible, le code d'erreur contient également la cause sous\-jacente de l'erreur irrécupérable.  Les conditions suivantes génèrent des erreurs irrécupérables :  
  
-   L'analyse n'a pas pu être effectuée en raison d'une entrée insuffisante.  
  
-   L'analyse a levé une exception qui n'est pas gérée par FxCopCmd.  
  
-   Le fichier projet spécifié est introuvable ou endommagé.  
  
-   L'option de sortie n'a pas été spécifiée ou le fichier n'a pas pu être écrit.  
  
    > [!NOTE]
    >  Le code retour FxCopCmd « Erreur des références d'assembly » 0x200 seul est un avertissement plutôt qu'une erreur.  Ce code retour indique que des références indirectes manquantes ont été trouvées mais que FxCopCmd a pu les traiter.  Cet avertissement indique que certains résultats d'analyse ont peut\-être été compromis.  Considérez le code retour « Erreur des références d'assembly » comme une erreur lorsqu'il est combiné à un autre code retour.  
  
## Voir aussi  
 [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)