---
title: "Propri&#233;t&#233;s des connecteurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine, connecteurs"
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# Propri&#233;t&#233;s des connecteurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les connecteurs représentent des relations de domaine dans un concepteur généré.  
  
 Pour plus d'informations, consultez [Comment : définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  Pour plus d'informations sur l'utilisation de ces propriétés, consultez [Personnalisation et extension d'un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Les connecteurs ont les propriétés répertoriées dans le tableau suivant.  
  
|Propriété|Description|Par défaut|  
|---------------|-----------------|----------------|  
|Couleur|la couleur de ce connecteur.|Black \(noir\)|  
|style de ligne|Le style de ligne pour la ligne pour ce connecteur \(unie, tiret, pointez, DashDot, DashDotDot, ou personnaliser\).|Plein|  
|Style de extrémité source|Le style de extrémité source pour ce connecteur \(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond, ou aucun\).|Aucun|  
|ciblez le style de fin|Le style cible de fin de ce connecteur \(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond, ou aucun\).|Aucun|  
|Couleur de texte|La couleur utilisée pour les éléments décoratifs de texte qui sont associés à ce connecteur.|Black \(noir\)|  
|Thickness|L'épaisseur de la ligne pour ce connecteur, mesurées en pouces.|0.03125|  
|Modificateur d'accès|le niveau d'accès de la classe \(`public` ou `internal`\).|Public|  
|Attributs personnalisés|utilisé pour ajouter des attributs à la classe de code source qui est générée de ce connecteur.|\<aucune\>|  
|génère double dérivé|Si `True`, une classe de base et une classe partielle \(pour prendre en charge la personnalisation via des substitutions\) est généré.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d'héritage|Décrit le type d'héritage de la classe de code source qui est générée du connecteur \(`none`, `abstract` ou `sealed`\).|aucun|  
|basez le connecteur|la classe de base de ce connecteur.|\(aucun\)|  
|Nom|le nom de ce connecteur.|nom actuel|  
|Espace de noms|L'espace de noms qui est affilié à ce connecteur.|l'espace de noms actuel|  
|type d'info\-bulle|comment l'info\-bulle est définie \(résolu, variable, ou aucune\).  Si résolue, la valeur de la propriété d' `Fixed Tooltip Text` est utilisée comme info\-bulle ; si la variable, l'info\-bulle est définie dans du code personnalisé.|\<aucune\>|  
|Remarques|Remarques informelles associées à ce connecteur.|\<aucune\>|  
|style de routage|Le style utilisé pour router le connecteur.  Un connecteur d' `Rectilinear` fait des visites carré au besoin ; un connecteur d' `Straight` ne le fait pas.|rectiligne|  
|Couleur exposée comme une propriété<br /><br /> Style de ligne exposé en tant que propriété<br /><br /> Épaisseur exposé en tant que propriété<br /><br /> Couleur du texte d'expose|si `True`, l'utilisateur peut définir la propriété indiquée d'une forme.  Pour définir cela, cliquez avec le bouton droit sur la définition de forme et cliquez sur **ajoutez exposé**.|False|  
|Description|Utilisé pour documenter le concepteur généré.|\<aucune\>|  
|Nom complet|Le nom qui s'affiche dans le concepteur généré pour ce connecteur.|\<aucune\>|  
|texte fixe d'info\-bulle|Le texte utilisé pour une info\-bulle fixe.|\<aucune\>|  
|mot clé d'aide|Le mot clé utilisé pour indexer l'aide F1 pour cet élément.|\<aucune\>|  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)