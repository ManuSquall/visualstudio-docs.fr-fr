---
title: "CA1726&#160;: Utilisez les termes par d&#233;faut | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePreferredTerms"
  - "CA1726"
helpviewer_keywords: 
  - "UsePreferredTerms"
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# CA1726&#160;: Utilisez les termes par d&#233;faut
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Catégorie|Microsoft.Naming|  
|Modification avec rupture|Avec rupture \- lorsque déclenchée sur les assemblys<br /><br /> Sans rupture \- lorsque déclenchée sur les paramètres de type|  
  
## Cause  
 Le nom d'un identificateur visible de l'extérieur contient un terme pour lequel un autre terme par défaut existe.  Le nom peut également inclure le terme Indicateur ou Indicateurs.  
  
## Description de la règle  
 Cette règle analyse un identificateur dans des jetons.  Chaque jeton unique et chaque combinaison de jetons doubles contigus sont comparés aux termes intégrés dans la règle et dans la section Déconseillé des dictionnaires personnalisés.  Le tableau suivant présente les termes intégrés dans la règle et leurs termes de remplacement par défaut.  
  
|Terme obsolète|Terme par défaut|  
|--------------------|----------------------|  
|Arent|AreNot|  
|Annulé|Canceled|  
|Cant|Cannot|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|Dont|DoNot|  
|Indicateur ou Indicateurs|Il n'existe aucun autre terme.  Ne pas utiliser.|  
|Hadnt|HadNot|  
|Hasn't|HasNot|  
|Havent|HaveNot|  
|Index|Index|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|Werent|WereNot|  
|Wont|WillNot|  
|Wouldnt|WouldNot|  
|Writeable|Writable|  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez le terme par le terme de remplacement par défaut.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle uniquement si le nom de l'identificateur se rapporte intentionnellement et spécifiquement au terme d'origine, au lieu du terme par défaut.  
  
## Règles connexes  
 [Avertissements liés à l’affectation de noms](../code-quality/naming-warnings.md)