---
title: "Propri&#233;t&#233;s des r&#244;les de domaine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 9
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 9
---
# Propri&#233;t&#233;s des r&#244;les de domaine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les propriétés dans le tableau suivant sont associées à un rôle de domaine.  Pour plus d'informations sur les rôles de domaine, consultez l' [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md).  Pour plus d'informations sur l'utilisation de ces propriétés, consultez [Personnalisation et extension d'un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriété|Description|Par défaut|  
|---------------|-----------------|----------------|  
|type de collection|Si ce rôle possède la multiplicité de 0. \* ou 1. \*, cette propriété personnalise le type générique utilisé pour stocker la collection de liens.|`(none)`\- <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> est utilisé|  
|Attributs personnalisés|Les attributs spécifiées ici seront ajoutés en tant qu'attributs à la classe du code généré.|\<aucune\>|  
|Est la propriété être exploré|Si `True`, et si la multiplicité de la relation est 0..1 ou 1..1, le rôle de la propriété peut être parcouru par l'utilisateur dans la fenêtre de **Propriétés** .  La propriété affiche le nom de l'élément à l'autre extrémité du lien de relation.|`True`|  
|Est le concepteur de propriété|Si `True`, rôle de la propriété est généré pour ce rôle, que vous pouvez utiliser pour parcourir les relations dans le code du programme.  Si vous définissez cette valeur false, vous pouvez parcourir la relation de façon moins efficace à l'aide de méthodes statiques de la relation de domaine.|`True`|  
|modificateur d'accès d'accesseur Get de propriété|Le modificateur d'accès de l'accesseur Get pour la propriété générée \(`public`, `internal`, `private`, `protected`, ou `protected internal`\).|`public`|  
|modificateur d'accès d'accesseur Set de propriété|Le modificateur d'accès de l'accesseur Set de la propriété générée \(`public`, `internal`, `private`, `protected`, ou `protected internal`\).|`public`|  
|Multiplicité|le nombre d'éléments de modèle qui peuvent jouer le rôle opposé \(`0..1`, `1..1`, `0..*`, ou `1..*`\).  Si la multiplicité est `0..*` ou `1..*`, la propriété générée représente une collection ; sinon, la propriété générée représente un élément de modèle unique.|Dépend du type de relation et si c'est la source ou la cible le rôle dans la relation.|  
|Nom|Le nom de rôle du domaine.  Cette propriété ne peut pas contenir d'espaces blancs.|La classe de nom de domaine du rôle lecteur pour ce rôle.|  
|copie de propagations|`DoNotPropagateCopy` \- le rôle lecteur copié n'aura pas de copie de ce lien.<br /><br /> `PropagateCopyToLinkOnly` \- les points copiés de lien à l'existant du paramètre du rôle lecteur.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`\- les points copiés de lien à une copie du rôle lecteur opposé.|`PropagateCopyToLinkAndOppositeRolePlayer` pour les rôles de source les incorporations.<br /><br /> `DoNotPropagateCopy` pour d'autres rôles.<br /><br /> Pour plus d'informations, consultez [Personnalisation du comportement de la commande copier](../modeling/customizing-copy-behavior.md).|  
|suppression de propagations|`True` pour supprimer l'élément qui lit ce rôle lorsque le lien associé est supprimé.|`True` pour la cible d'un rôle d'incorporation.<br /><br /> `False` pour d'autres rôles.<br /><br /> Pour plus d'informations, consultez [Personnalisation du comportement de la commande de suppression](../modeling/customizing-deletion-behavior.md).|  
|Nom de la propriété|Le nom de la propriété générée dans le code du rôle lecteur.  Ce nom ne peut pas contenir d'espaces blancs.|Le nom du rôle opposé si ce rôle a zéro\-à\-un ou d'une multiplicité linéaire ; sinon, le nom pris le nom du rôle opposé.|  
|Rôle lecteur|La classe de domaine de l'élément qui peut lire ce rôle dans la relation.  Cette propriété est en lecture seule.|La classe de domaine du rôle lecteur pour ce rôle.|  
|Remarques|Remarques informelles associées au rôle de domaine.|\<aucune\>|  
|Catégorie|La catégorie dans laquelle la propriété générée s'affiche dans la fenêtre de **Propriétés** dans le concepteur généré.  Si cette propriété est vide, la propriété générée s'affiche sous la catégorie de **Divers**|\<aucune\>|  
|Description|La description qui est utilisée pour documenter du code et est utilisée dans l'interface utilisateur du concepteur généré.<br /><br /> La description s'affiche dans l'info\-bulle Intellisense pour la propriété générée sur le rôle de classe de lecteur.|`Description for` *le nom complet du rôle*|  
|Nom complet|Le nom qui s'affiche dans le concepteur généré pour le rôle de domaine.|La valeur ajustée de la propriété Name.|  
|mot clé d'aide|Le mot clé facultative utilisée pour indexer l'aide F1 pour le rôle de domaine.|\<aucune\>|  
|nom complet de propriété|Le nom qui s'affiche dans le concepteur généré pour le rôle généré de propriété.|La valeur ajustée de la propriété nom de la propriété.|  
  
> [!NOTE]
>  La valeur par défaut d'un nom complet est basée sur la valeur de propriété associée en insérant les espaces précédant chaque majuscule qui est précédée par une minuscule et qui n'est pas suivie par une autre majuscule.  
  
## Voir aussi  
 [Propriétés des relations de domaine](../modeling/properties-of-domain-relationships.md)