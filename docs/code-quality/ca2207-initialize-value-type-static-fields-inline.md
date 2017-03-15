---
title: "CA2207&#160;: Initialisez les champs statiques des types valeur en ligne | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InitializeValueTypeStaticFieldsInline"
  - "CA2207"
helpviewer_keywords: 
  - "CA2207"
  - "InitializeValueTypeStaticFieldsInline"
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2207&#160;: Initialisez les champs statiques des types valeur en ligne
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InitializeValueTypeStaticFieldsInline|  
|CheckId|CA2207|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type valeur référence déclare un constructeur statique explicite.  
  
## Description de la règle  
 Lorsqu'un type valeur est déclaré, il fait l'objet d'une initialisation par défaut, dans laquelle la valeur de tous ses champs de type valeur est mise à zéro et tous les champs de type référence se voient attribuer la valeur `null` \(`Nothing` en Visual Basic\).  L'exécution d'un constructeur statique explicite est garantie uniquement avant l'appel à un constructeur d'instance ou d'un membre statique du type.  Par conséquent, si le type est créé sans appeler de constructeur d'instance, l'exécution du constructeur statique n'est pas garantie.  
  
 Si toutes les données statiques sont initialisées inline et si aucun constructeur statique explicite n'est déclaré, les compilateurs C\# et Visual Basic ajoutent l'indicateur `beforefieldinit` à la définition de classe MSIL.  Les compilateurs ajoutent également un constructeur statique privé qui contient le code d'initialisation statique.  L'exécution de ce constructeur statique privé est garantie avant l'accès à tout champ statique du type.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu'elles sont déclarées et supprimez le constructeur statique.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Règles connexes  
 [CA1810 : Initialisez les champs statiques de type référence en ligne](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)