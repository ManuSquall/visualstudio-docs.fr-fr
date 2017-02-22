---
title: "CA1020&#160;: &#201;viter les espaces de noms comportant peu de types | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1020"
  - "AvoidNamespacesWithFewTypes"
helpviewer_keywords: 
  - "AvoidNamespacesWithFewTypes"
  - "CA1020"
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1020&#160;: &#201;viter les espaces de noms comportant peu de types
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNamespacesWithFewTypes|  
|CheckId|CA1020|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un espace de noms autre que l'espace de noms global contient moins que cinq types.  
  
## Description de la règle  
 Assurez\-vous que chacun de vos espaces de noms bénéficie d'une organisation logique, et qu'une raison valide justifie le placement des types dans un espace de noms peu rempli.  Les espaces de noms doivent contenir des types utilisés ensemble dans la plupart des scénarios.  Lorsque leurs applications sont mutuellement exclusives, les types doivent être placés dans des espaces de noms distincts.  Par exemple, l'espace de noms <xref:System.Web.UI> contient des types utilisés dans des applications Web, et l'espace de noms <xref:System.Windows.Forms> des types utilisés dans des applications [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)].  Bien que les deux espaces de noms aient des types que les aspects de contrôle de l'interface utilisateur, ces types ne sont pas conçu pour une utilisation dans la même application.  Par conséquent, ils se trouvent dans les espaces de noms distincts.  Une organisation soignée des espaces de noms peut également s'avérer utile car elle augmente la possibilité de découverte d'une fonctionnalité.  En examinant la hiérarchie des espaces de noms, les consommateurs de bibliothèques doivent être en mesure de localiser les types qui implémentent une fonctionnalité.  
  
> [!NOTE]
>  Pour se conformer à cette directive, les types et les autorisations du moment du design ne doivent pas être fusionnés dans d'autres espaces de noms.  Ces types appartiennent à leurs propres espaces de noms, eux\-mêmes subordonnés à votre espace de noms principal. Ces espaces de noms doivent respectivement se terminer par `.Design` et `.Permissions`.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, essayez de mixer les espaces de noms qui contiennent un petit nombre de types dans un espace de noms unique.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle quand l'espace de noms ne contient aucun type utilisé avec les types présents dans vos autres espaces de noms.