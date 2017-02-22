---
title: "Propri&#233;t&#233;s des classes de domaine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine, classe de domaine"
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# Propri&#233;t&#233;s des classes de domaine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

les classes de domaine ont les propriétés dans le tableau suivant.  Pour plus d'informations sur les classes, consultez l' [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md).  Pour plus d'informations sur l'utilisation de ces propriétés, consultez [Personnalisation et extension d'un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriété|Description|Par défaut|  
|---------------|-----------------|----------------|  
|Modificateur d'accès|le niveau d'accès de la classe de domaine \(`public` ou `internal`\).|`public`|  
|Attributs personnalisés|utilisé pour ajouter des attributs à la classe de code source qui est générée de cette classe de domaine.|\<aucune\>|  
|génère double dérivé|Si `True`, une classe de base et une classe partielle \(pour prendre en charge la personnalisation via des substitutions\) est généré.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificateur d'héritage|Décrit le type d'héritage de la classe de code source qui est générée de la classe de domaine \(`none`, `abstract` ou `sealed`\).|`none`|  
|Classe de base|Si cette classe de domaine est dérivée de, le nom de la classe de base.|\<aucune\>|  
|Nom|le nom de cette classe de domaine.|nom actuel|  
|Espace de noms|l'espace de noms de cette classe de domaine.|l'espace de noms actuel|  
|Remarques|Remarques informelles associées à cette classe de domaine.|\<aucune\>|  
|Description|La description qui est utilisée pour documenter l'interface utilisateur du concepteur généré.|\<aucune\>|  
|Nom complet|Le nom qui s'affiche dans le concepteur généré pour cette classe de domaine.|\<aucune\>|  
|mot clé d'aide|Le mot clé facultative utilisée pour indexer l'aide F1 pour cette classe de domaine.|\<aucune\>|  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)