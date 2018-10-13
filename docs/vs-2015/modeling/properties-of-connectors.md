---
title: Propriétés des connecteurs | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, connectors
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b78858b14674eafeb044b168a8bb8927af9f5769
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171845"
---
# <a name="properties-of-connectors"></a>Propriétés des connecteurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Connecteurs représentent les relations de domaine dans un concepteur généré.  
  
 Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Les connecteurs ont les propriétés qui sont répertoriées dans le tableau suivant.  
  
|Propriété|Description|Par défaut|  
|--------------|-----------------|-------------|  
|Color|La couleur de ce connecteur.|Noir|  
|Style de ligne|Le style de tiret pour la ligne de ce connecteur (solide, tiret, point, tiret, DashDotDot ou personnalisé).|Unie|  
|Style de l’extrémité source|Le style de fin de source de ce connecteur (HollowArrow, d’EmptyArrow, FilledArrow, d’EmptyDiamond, FilledDiamond ou aucun).|Aucun.|  
|Style de l’extrémité cible|Le style de fin de cible de ce connecteur (HollowArrow, d’EmptyArrow, FilledArrow, d’EmptyDiamond, FilledDiamond ou aucun).|Aucun.|  
|Couleur du texte|La couleur qui est utilisée pour les éléments décoratifs de texte qui sont associés à ce connecteur.|Noir|  
|Thickness|L’épaisseur de la ligne de ce connecteur, mesurée en pouces.|0.03125|  
|Modificateur d'accès|Le niveau d’accès de la classe (`public` ou `internal`).|Public|  
|Attributs personnalisés|Utilisé pour ajouter des attributs à la classe de code source qui est générée à partir de ce connecteur.|\<Aucun >|  
|Génère le Double dérivée|Si `True`, une classe de base et une classe partielle (pour prendre en charge la personnalisation via des substitutions) sont générés. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|A le constructeur personnalisé|Si `True`, un constructeur personnalisé est fourni dans le code source. Pour plus d’informations, consultez [substitution et extension des Classes générées](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificateur d’héritage|Décrit le type d’héritage de la classe de code source qui est générée à partir du connecteur (`none`, `abstract` ou `sealed`).|none|  
|Connecteur de base|La classe de base de ce connecteur.|(aucune)|  
|Name|Le nom de ce connecteur.|Nom actuel|  
|Espace de noms|L’espace de noms qui est affilié à ce connecteur.|Espace de noms actuel|  
|Type de l’info-bulle|Comment l’info-bulle est définie (fixe, variable, ou aucun). Si fixe, puis la valeur de la `Fixed Tooltip Text` propriété est utilisée en tant que l’info-bulle ; si la variable, l’info-bulle est définie dans du code personnalisé.|\<Aucun >|  
|Notes|Remarques informelles associées à ce connecteur.|\<Aucun >|  
|Style de routage|Le style qui est utilisé pour router le connecteur. Un `Rectilinear` connecteur établit à angle droit active en fonction des besoins ; un `Straight` n’est pas le cas du connecteur.|Rectiligne|  
|Couleur exposé en tant que propriété<br /><br /> Style de tiret exposé en tant que propriété<br /><br /> Épaisseur exposé en tant que propriété<br /><br /> Expose la couleur du texte|Si `True`, l’utilisateur peut définir la propriété indiquée d’une forme. Pour définir ceci, avec le bouton droit de la définition de forme, puis cliquez sur **ajouter les objets exposés**.|False|  
|Description|Utilisé pour documenter le concepteur généré.|\<Aucun >|  
|Nom complet|Le nom qui s’affichera dans le concepteur généré pour ce connecteur.|\<Aucun >|  
|Texte d’info-bulle fixe|Le texte qui est utilisé pour une info-bulle fixe.|\<Aucun >|  
|Help Keyword|Le mot clé qui est utilisé pour indexer l’aide F1 pour cet élément.|\<Aucun >|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



