---
title: "CA1716 : Les identificateurs ne doivent pas correspondre &#224; des mots cl&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
helpviewer_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1716 : Les identificateurs ne doivent pas correspondre &#224; des mots cl&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Oui|  
  
## Cause  
 Le nom d'un espace de noms, d'un type ou encore d'un membre d'interface ou virtuel correspond à un mot clé réservé dans un langage de programmation.  
  
## Description de la règle  
 Les identificateurs des espaces de noms, des types et membres virtuels et d'interface ne doivent pas correspondre aux mots clés définis par les langages qui ciblent le Common Language Runtime.  Selon le langage utilisé et le mot clé, des erreurs du compilateur et des ambiguïtés peuvent rendre l'utilisation de la bibliothèque difficile.  
  
 Cette règle vérifie en fonction des mots clés dans les langages suivants :  
  
-   Visual Basic  
  
-   C\#  
  
-   C\+\+\/CLI  
  
 La comparaison qui ne respecte pas la casse est utilisée pour les mots clés [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], et la comparaison sensible à la casse est utilisée pour les autres langages.  
  
## Comment corriger les violations  
 Sélectionnez un nom qui ne figure pas dans la liste des mots clés.  
  
## Quand supprimer les avertissements  
 Vous pouvez supprimer un avertissement de cette règle si vous êtes convaincu que l'identificateur ne confondra pas les utilisateurs de l'API, et que la bibliothèque est utilisable dans toutes les langues disponibles dans [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].