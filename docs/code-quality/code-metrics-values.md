---
title: "Valeurs de la m&#233;trique du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "métrique du code"
  - "analyse du code"
  - "mesurer la qualité du code"
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 20
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 20
---
# Valeurs de la m&#233;trique du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La métrique du code est un jeu de mesures de logiciel qui fournit aux développeurs plus de détails sur le code qu'ils développent.  En utilisant la métrique du code, les développeurs peuvent comprendre quels types et\/ou méthodes doivent être retravaillées ou testées de manière plus approfondie.  Les équipes de développement peuvent identifier les risques potentiels, comprendre l'état actuel d'un projet et suivre la progression durant le développement du logiciel.  
  
## Dimensions du logiciel  
 La liste suivante affiche les résultats de la métrique du code que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] calcule :  
  
-   **Indice de maintenabilité** – Calcule une valeur d'indice entre 0 et 100 qui représente la facilité relative de la maintenance du code.  Une valeur élevée signifie une meilleure facilité de maintenance.  Il est possible d'utiliser des évaluations de couleur pour identifier rapidement les points problématiques dans le code.  Une évaluation verte correspond à une plage entre 20 et 100 et indique que le code présente une bonne facilité de maintenance.  Une évaluation jaune correspond à une plage entre 10 et 19 et indique que le code présente une facilité de maintenance moyenne.  Enfin, une évaluation rouge correspond à une plage entre 0 et 9 et indique une facilité de maintenance faible.  
  
-   **Complexité cyclomatic** – Mesure la complexité structurelle du code.  Il est créé en calculant le nombre de chemins d'accès à du code différents, dans le flux du programme.  Un programme dont le flux de contrôle est complexe requiert des tests supplémentaires pour atteindre une bonne couverture du code et est moins facile à gérer.  
  
    > [!NOTE]
    >  Dans certains cas, le calcul de la complexité de cyclomatique d'une méthode dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] diffère des versions antérieures.  Pour plus d'informations, consultez la section « Modifications dans les calculs de la complexité du code Visual Studio 2010 » dans [Résolution des problèmes liés à la métrique du code](../code-quality/troubleshooting-code-metrics-issues.md).  
  
-   **Profondeur d'héritage** \- Indique le nombre des définitions de classe qui s'étendent à la racine de la hiérarchie de classes.  Plus la hiérarchie est profonde, plus il peut être difficile de comprendre où des méthodes et champs particuliers sont définis et\/ou redéfinis.  
  
-   **Couplage de classe** \- Mesure le couplage avec des classes uniques via des paramètres, des variables locales, des types de retour, des appels de méthode, des instanciations génériques ou du modèle, des classes de base, des implémentations d'interface, des champs définis sur des types externes et une décoration d'attribut.  Une bonne conception logicielle implique que les types et méthodes aient une cohésion élevée et un couplage bas.  Un couplage élevé indique une conception difficile à réutiliser et à gérer en raison des ses nombreuses interdépendances avec d'autres types.  
  
-   **Lignes de code** \- Indique le nombre approximatif de lignes dans le code.  Le compte est basé sur le code IL \(Intermediate Language\) et ne correspond pas, par conséquent, au nombre exact de lignes du fichier de code source.  Un compte très élevé peut indiquer qu'un type ou une méthode essaie de faire trop de travail et doit être fractionné.  Il peut également indiquer que le type ou la méthode est difficile à gérer.  
  
## Méthodes anonymes  
 Une *méthode anonyme* est simplement une méthode sans nom.  Les méthodes anonymes sont le plus souvent utilisées pour passer un bloc de code en paramètre de délégué.  Les résultats de métrique d'une méthode anonyme déclarée dans un membre, tel qu'une méthode ou un accesseur, sont associés au membre qui déclare la méthode.  Ils ne sont pas associés au membre qui appelle la méthode.  
  
 Pour plus d'informations sur la façon dont la métrique du code traite les méthodes anonymes, consultez [Méthodes anonymes et analyse du code](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## Code généré  
 Certains outils logiciels et compilateurs génèrent un code qui est ajouté à un projet et que le développeur ne voit pas ou ne doit pas changer.  La plupart du temps, la métrique du code ignore le code généré lorsqu'il calcule les valeurs de métrique.  Cela permet aux valeurs de métrique de refléter ce que le développeur peut voir et changer.  
  
 Le code généré pour les formulaires Windows n'est pas ignoré, car il s'agit du code que le développeur peut voir et changer.  
  
## Voir aussi  
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)