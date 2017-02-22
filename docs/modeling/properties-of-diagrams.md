---
title: "Propri&#233;t&#233;s des diagrammes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "langage spécifique à un domaine, schéma"
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# Propri&#233;t&#233;s des diagrammes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez définir des propriétés qui spécifient comment les diagrammes d'affichage dans le concepteur généré.  Par exemple, vous pouvez spécifier une couleur par défaut du texte dans le diagramme.  
  
 Pour plus d'informations, consultez [Comment : définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  Pour plus d'informations sur l'utilisation de ces propriétés, consultez [Personnalisation et extension d'un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Le tableau suivant répertorie les propriétés des diagrammes.  
  
|Propriété|Description|Par défaut|  
|---------------|-----------------|----------------|  
|couleur de remplissage|La couleur de remplissage du diagramme.|Blanc|  
|Couleur de texte|La couleur du texte affiché dans le diagramme.|Black \(noir\)|  
|Modificateur d'accès|le modificateur d'accès de la classe \(public ou interne\).|Public|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe du code généré.|\<aucune\>|  
|génère double dérivé|Si `True`, une classe de base et une classe partielle \(pour prendre en charge la personnalisation via des substitutions\) est généré.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d'héritage|Décrit le type d'héritage de la classe de code source générée à partir de le diagramme \(`none`, `abstract` ou `sealed`\).|Aucun|  
|diagramme de base|la classe de base de ce diagramme.|\(aucun\)|  
|Nom|le nom de ce diagramme.|nom actuel|  
|Espace de noms|L'espace de noms qui est affilié à ce diagramme.|l'espace de noms actuel|  
|classe représentée|la classe de domaine racine que ce diagramme représente.|Classe racine actuelle cas échéant|  
|Remarques|Remarques informelles associées à cet élément.|\<aucune\>|  
|Couleur de remplissage d'expose une propriété|Si `True`, l'utilisateur peut définir la couleur de remplissage du diagramme du concepteur généré.  Pour définir cela, cliquez avec le bouton droit sur la forme du diagramme et cliquez sur **ajoutez Explosed**.|False|  
|Couleur du texte d'expose une propriété|Si `True`, l'utilisateur peut définir la couleur de texte du diagramme dans le concepteur généré.  Pour définir cela, cliquez avec le bouton droit sur la forme du diagramme et cliquez sur **ajoutez Explosed**.|False|  
|Description|La description qui est utilisée pour documenter le concepteur généré.|\<aucune\>|  
|Nom complet|Le nom qui s'affiche dans le concepteur généré pour ce diagramme.|\<aucune\>|  
|mot clé d'aide|Le mot clé utilisé pour indexer l'aide F1 pour ce diagramme.|\<aucune\>|  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)