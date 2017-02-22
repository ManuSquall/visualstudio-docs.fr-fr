---
title: "CA1053&#160;: Les types de conteneurs statiques ne doivent pas comporter de constructeur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "StaticHolderTypesShouldNotHaveConstructors"
  - "CA1053"
helpviewer_keywords: 
  - "CA1053"
  - "StaticHolderTypesShouldNotHaveConstructors"
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1053&#160;: Les types de conteneurs statiques ne doivent pas comporter de constructeur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public ou imbriqué déclare uniquement des membres statiques et dispose d'un constructeur par défaut public ou protégé.  
  
## Description de la règle  
 Le constructeur est inutile car l'appel à des membres statiques ne requiert aucune instance du type.  Par ailleurs, étant donné que le type ne présente aucun membre non statique, la création d'une instance ne donne accès à aucun des membres du type.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le constructeur par défaut ou rendez\-le privé.  
  
> [!NOTE]
>  Certains compilateurs créent automatiquement un constructeur public par défaut si le type ne définit aucun constructeur.  Si votre type est dans ce cas, ajoutez un constructeur par défaut privé pour éliminer la violation.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  La présence du constructeur laisse entendre que le type n'est pas statique.  
  
## Exemple  
 L'exemple suivant affiche un type qui ne respecte pas cette règle.  Remarquez l'absence de constructeur par défaut dans le code source.  Lorsque ce code est compilé dans un assembly, le compilateur C\# insérera un constructeur par défaut, ce qui violera cette règle.  Pour remédier à cette réaction, déclarez un constructeur privé.  
  
 [!CODE [FxCop.Design.StaticTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.StaticTypes#1)]