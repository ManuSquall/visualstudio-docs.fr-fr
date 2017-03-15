---
title: "CA1713&#160;: Les &#233;v&#233;nements ne doivent pas &#234;tre munis d&#39;un pr&#233;fixe Before ou After | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
  - "CA1713"
helpviewer_keywords: 
  - "CA1713"
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1713&#160;: Les &#233;v&#233;nements ne doivent pas &#234;tre munis d&#39;un pr&#233;fixe Before ou After
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le nom d'un événement commence par 'Before' ou 'After'.  
  
## Description de la règle  
 Les noms d'événements doivent décrire l'action qui déclenche l'événement.  Pour nommer des événements associés déclenchés dans une séquence spécifique, utilisez le présent ou le passé pour indiquer la position relative dans la séquence d'actions.  Par exemple, lorsque vous nommez une paire d'événements déclenchés lors de la fermeture d'une ressource, vous pouvez les nommer 'Closing' \(Fermeture\) et 'Closed' \(Fermé\) au lieu de 'BeforeClose' \(AvantFermeture\) et 'AfterClose' \(AprèsFermeture\).  
  
 Les conventions d'affectation des noms confèrent un aspect commun aux bibliothèques qui ciblent le Common Language Runtime.  Elles réduisent ainsi la durée de l'apprentissage requis par les nouvelles bibliothèques de logiciels et confirment au client que la bibliothèque a été développée par une personne compétente en matière de développement de code managé.  
  
## Comment corriger les violations  
 Supprimez le préfixe du nom d'évènement et envisagez de modifier le nom pour utiliser le présent ou passé d'un verbe.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.