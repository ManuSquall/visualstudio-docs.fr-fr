---
title: "Propri&#233;t&#233;s des formes de compartiment | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.compartmentshape"
helpviewer_keywords: 
  - "langage spécifique à un domaine, forme de compartiment"
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# Propri&#233;t&#233;s des formes de compartiment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les formes de compartiment sont l'une des formes que vous pouvez utiliser pour afficher une classe de domaine dans un langage spécifique au domaine.  Vous pouvez développer et réduire les compartiments.  
  
 Pour plus d'informations, consultez [Comment : définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  Pour plus d'informations sur l'utilisation de ces propriétés, consultez [Personnalisation et extension d'un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Les formes de compartiment ont les propriétés répertoriées dans le tableau suivant.  
  
|Propriété|Description|Par défaut|  
|---------------|-----------------|----------------|  
|La valeur par défaut développez l'état réduit|Si `Expanded`, les compartiments sont affichés sur la conception.  si `Collapsed`, ils ne sont pas.|Étendu|  
|couleur de remplissage|la couleur de remplissage de cette forme.|Blanc|  
|mode de dégradé de remplissage|Le mode de remplissage dégradé de cette forme.|Horizontal|  
|Geometry|la géométrie de cette forme \(rectangle ou rectangle arrondi\).|Rectangle|  
|Présente les points de connexion par défaut|Si `True`, la forme utilisera le bord supérieur, inférieur, gauche, et de bons points de connexion dans le concepteur généré.|False|  
|Est l'en\-tête de compartiment unique visible|Si `False`, et la forme comprend un compartiment unique, l'en\-tête de compartiment n'est pas visible.|True|  
|couleur d'ensemble|la couleur d'ensemble de cette forme.|Black \(noir\)|  
|Contour du style de ligne|Le style de ligne d'ensemble de cette forme \(unie, tiret, pointez, DashDot, DashDotDot, personnaliser\).|Plein|  
|Contour de l'épaisseur|l'épaisseur d'ensemble de cette forme.|0.03125|  
|Couleur de texte|La couleur utilisée pour les éléments décoratifs de texte qui sont associés aux la forme.|Black \(noir\)|  
|Modificateur d'accès|le niveau d'accès de la forme de compartiment \(`public` ou `internal`\).|Public|  
|Attributs personnalisés|utilisé pour ajouter des attributs à la classe de code source qui est générée de cette forme de compartiment|\<aucune\>|  
|génère double dérivé|Si `True`, une classe de base et une classe partielle \(pour prendre en charge la personnalisation via des substitutions\) est généré.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d'héritage|Décrit le type d'héritage de la classe de code source qui est générée de la forme de compartiment \(`none`, `abstract` ou `sealed`\).|Aucun|  
|forme de base de compartiment|la classe de base de cette forme.|\(aucun\)|  
|Nom|le nom de cette forme.|nom actuel|  
|Espace de noms|L'espace de noms qui est affilié à l'aide de la forme.|l'espace de noms actuel|  
|type d'info\-bulle|comment l'info\-bulle est définie \(résolu, variable, ou aucune\).  Si résolue, la valeur de la propriété d' `Fixed Tooltip Text` est utilisée comme info\-bulle ; si la variable, l'info\-bulle est définie dans du code personnalisé.|aucun|  
|Remarques|Remarques informelles qui sont associées à cette forme.|\<aucune\>|  
|Initiales la hauteur|la hauteur initiale de cette forme, en pouces.  Pour les formes de compartiment, il s'agit de la hauteur de la section d'en\-tête uniquement et il ne peut pas être redimensionné.|1|  
|Largeur de démarrage|La largeur d'origine de cette forme, en pouces.|1.5|  
|Couleur de remplissage exposée comme une propriété<br /><br /> Mode exposé à dégradé de remplissage<br /><br /> Couleur exposée d'ensemble en tant que propriété<br /><br /> Style de ligne exposé d'ensemble en tant que propriété<br /><br /> Épaisseur exposé d'ensemble en tant que propriété<br /><br /> Couleur du texte d'expose|si `True`, l'utilisateur peut définir la propriété indiquée d'une forme.  Pour définir cela, cliquez avec le bouton droit sur la définition de forme et cliquez sur **ajoutez exposé**.|False|  
|Description|Utilisé pour documenter le concepteur généré.|\<aucune\>|  
|Nom complet|Le nom qui s'affiche dans le concepteur généré pour cette forme.|\<aucune\>|  
|texte fixe d'info\-bulle|Le texte utilisé pour une info\-bulle fixe.|\<aucune\>|  
|mot clé d'aide|Le mot clé utilisé pour indexer l'aide F1 pour cette forme.|\<aucune\>|  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)