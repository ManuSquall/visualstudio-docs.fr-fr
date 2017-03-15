---
title: "Propri&#233;t&#233;s des couloirs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.swimlane"
helpviewer_keywords: 
  - "langage spécifique à un domaine, couloir"
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# Propri&#233;t&#233;s des couloirs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez ajouter des couloirs à un diagramme.  Division de Couloirs un diagramme en zones verticale ou horizontale.  Vous pouvez définir d'autres formes à afficher dans des couloirs.  Pour plus d'informations, consultez [Comment : définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  Pour plus d'informations sur l'utilisation de ces propriétés, consultez [Personnalisation et extension d'un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Couloirs ont les propriétés répertoriées dans le tableau suivant.  
  
|Propriété|Description|Par défaut|  
|---------------|-----------------|----------------|  
|couleur de remplissage de corps|La couleur de remplissage du corps du couloir.|Blanc|  
|couleur de remplissage d'en\-tête|La couleur de remplissage pour l'en\-tête du couloir.|Le gris foncé|  
|couleur de séparateur|La couleur de la ligne de séparation.|Gris clair|  
|Style de séparateur|le style de la ligne de séparateur \(`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, ou `Custom`\).|`Dash`|  
|épaisseur de séparateur|L'épaisseur de pouces d'entrée ligne de séparation.|0.03125|  
|Couleur de texte|La couleur utilisée pour les éléments décoratifs de texte qui sont associés à ce couloir.|Black \(noir\)|  
|Modificateur d'accès|le niveau d'accès de la classe \(`public` ou `internal`\).|Public|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe du code généré à partir de ce couloir.|\<aucune\>|  
|génère double dérivé|Si `True`, une classe de base et une classe partielle \(pour prendre en charge la personnalisation via des substitutions\) est généré.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A un constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source.  Pour plus d'informations, consultez [Substitution et extension des classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d'héritage|Décrit le type d'héritage de la classe de code source générée à partir de le couloir \(`none`, `abstract` ou `sealed`\).|aucun|  
|Couloir de base|La classe de base de ce couloir.|\(aucun\)|  
|Nom|Le nom de ce couloir.|nom actuel|  
|Espace de noms|L'espace de noms qui est affilié à ce couloir.|l'espace de noms actuel|  
|type d'info\-bulle|comment l'info\-bulle est définie \(`fixed`, `variable`, ou `none`\).  Si `fixed`, la valeur de la propriété d' `Fixed Tooltip Text` est utilisé ; si `variable`, l'info\-bulle est défini dans le code personnalisé.|\<aucune\>|  
|Remarques|Remarques informelles associées à ce couloir.|\<aucune\>|  
|Alignement|Alignement horizontal ou vertical.|Vertical|  
|Hauteur de démarrage|La hauteur initiale de ce couloir, en pouces.  Applicable uniquement aux couloirs horizontaux.|0|  
|Largeur de démarrage|La largeur d'origine de ce couloir, en pouces.  Applicable uniquement aux couloirs vertical.|0|  
|Couleur du texte d'expose|Si `True`, l'utilisateur peut définir la couleur d'un couloir dans le concepteur généré.  Pour définir cela, cliquez avec le bouton droit sur la forme de couloir et cliquez sur **ajoutez exposé**.|False|  
|Description|Utilisé pour documenter le concepteur généré.|\<aucune\>|  
|Nom complet|Le nom qui s'affiche dans le concepteur généré pour faire référence à cette classe de couloir.|\<aucune\>|  
|texte fixe d'info\-bulle|Le texte utilisé pour une info\-bulle fixe.|\<aucune\>|  
|mot clé d'aide|Le mot clé utilisé pour indexer l'aide F1 pour ce couloir.|\<aucune\>|  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)