---
title: "Propri&#233;t&#233;s des formes d&#39;image | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.selectimagedialog"
  - "vs.dsltools.dsldesigner.imageshape"
helpviewer_keywords: 
  - "langage spécifique à un domaine, forme d'image"
ms.assetid: 9ce00ccd-07f2-4640-ac96-2a60481d0d72
caps.latest.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 25
---
# Propri&#233;t&#233;s des formes d&#39;image
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser des formes d'image pour spécifier comment les classes de domaine apparaissent dans un concepteur généré.  Définissez une forme d'image en définissant la propriété d' `Image` de la classe dans un fichier image intégré.  les formats suivants sont pris en charge :  
  
-   .gif  
  
-   .jpg  
  
-   .jpeg  
  
-   .bmp  
  
-   .wmf  
  
-   .emf  
  
-   png  
  
 Par défaut, les fichiers de ressources concepteurs, tels que des fichiers image, se trouvent dans le dossier de **Resources**dans le projet de **DÉSOLÉ** .  
  
 Pour plus d'informations, consultez [Comment : définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  Pour plus d'informations sur l'utilisation de ces propriétés, consultez [Personnalisation et extension d'un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Les formes d'image ont les propriétés répertoriées dans le tableau suivant.  
  
|Propriété|Description|Par défaut|  
|---------------|-----------------|----------------|  
|couleur de remplissage|la couleur de remplissage de cette forme.|Blanc|  
|mode de dégradé de remplissage|Le mode de remplissage dégradé de cette forme.|Horizontal|  
|Présente les points de connexion par défaut|Si `True`, la forme utilisera le bord supérieur, inférieur, gauche, et de bons points de connexion dans le concepteur généré.|False|  
|couleur d'ensemble|la couleur d'ensemble de cette forme.|Black \(noir\)|  
|style de ligne d'ensemble|Le style de ligne d'ensemble de cette forme \(unie, tiret, pointez, DashDot, DashDotDot, ou personnaliser\).|Plein|  
|épaisseur d'ensemble|l'épaisseur d'ensemble de cette forme.|0.03125|  
|Couleur de texte|La couleur utilisée pour les éléments décoratifs de texte qui sont associés aux la forme.|Black \(noir\)|  
|Modificateur d'accès|Le modificateur d'accès de la forme géométrique \(public ou interne\).|Public|  
|Attributs personnalisés|utilisé pour ajouter des attributs à la classe de code source qui est générée de cette forme.|\<aucune\>|  
|génère double dérivé|Si `True`, une classe de base et une classe partielle \(pour prendre en charge la personnalisation via des substitutions\) est généré.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d'héritage|Décrit le type d'héritage de la classe de code source qui est générée de la forme \(images`none`, `abstract` ou `sealed`\).|aucun|  
|forme d'image disque de base|la classe de base de cette forme.|\(aucun\)|  
|Nom|le nom de cette forme.|nom actuel|  
|Espace de noms|L'espace de noms qui est affilié à l'aide de la forme.|l'espace de noms actuel|  
|type d'info\-bulle|l'endroit où l'info\-bulle est définie \(résolu, variable, ou aucune\).  Si résolue, la valeur de la propriété d' `Fixed Tooltip Text` est utilisée comme info\-bulle ; si la variable, l'info\-bulle est définie dans du code personnalisé.|aucun|  
|Remarques|Remarques informelles qui sont associées à cette forme.|\<aucune\>|  
|Hauteur de démarrage|la hauteur initiale de cette forme, en pouces.|1|  
|Largeur de démarrage|La largeur d'origine de cette forme, en pouces.|1.5|  
|Couleur de remplissage exposée comme une propriété<br /><br /> Mode exposé à dégradé de remplissage<br /><br /> Couleur exposée d'ensemble en tant que propriété<br /><br /> Style de ligne exposé d'ensemble en tant que propriété<br /><br /> Épaisseur exposé d'ensemble en tant que propriété<br /><br /> Couleur du texte d'expose|si `True`, l'utilisateur peut définir la propriété indiquée d'une forme.  Pour définir cela, cliquez avec le bouton droit sur la définition de forme et cliquez sur **ajoutez exposé**.|False|  
|Description|Utilisé pour documenter le concepteur généré.|\<aucune\>|  
|Nom complet|Le nom qui s'affiche dans le concepteur généré pour cette forme.|\<aucune\>|  
|texte fixe d'info\-bulle|Le texte utilisé pour une info\-bulle fixe.|\<aucune\>|  
|mot clé d'aide|Le mot clé utilisé pour indexer l'aide F1 pour cet élément.|\<aucune\>|  
|Image|Le chemin d'accès au fichier image utilisée pour cette forme.|\<aucune\>|  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)