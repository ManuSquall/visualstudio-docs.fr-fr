---
title: Propriétés des rôles de domaine
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 854f282b22427fd805091d39377654b8d988084b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919147"
---
# <a name="properties-of-domain-roles"></a>Propriétés des rôles de domaine
Les propriétés dans le tableau suivant sont associées à un rôle de domaine. Pour plus d’informations sur les rôles de domaine, consultez [présentation des modèles, des Classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriété|Description|Par défaut|
|-|-|-|
|Type de collection|Si ce rôle a une multiplicité 0.. * ou 1... \*, cette propriété personnalise le type générique qui est utilisé pour stocker la collection de liens.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> est utilisé|
|Attributs personnalisés|Les attributs que vous spécifiez ici seront ajoutés en tant qu’attributs à la classe de code généré.|< aucun\>|
|Propriété est consultable|Si `True`, et si la multiplicité de la relation est la valeur 0.. 1 ou 1.. 1, la propriété de rôle peut être parcourue par l’utilisateur dans le **propriétés** fenêtre. La propriété affiche le nom de l’élément à l’autre extrémité du lien de relation.|`True`|
|Générateur de propriété|Si `True`, une propriété de rôle est générée pour ce rôle, vous pouvez utiliser pour parcourir la relation dans le code de programme. Si vous affectez la valeur false, vous pouvez parcourir la relation de manière moins efficace à l’aide des méthodes statiques de la relation de domaine.|`True`|
|Modificateur d’accès de méthode Getter de propriété|Le modificateur d’accès pour l’accesseur Get de la propriété générée (`public`, `internal`, `private`, `protected`, ou `protected internal`).|`public`|
|Modificateur d’accès de méthode Setter de propriété|Le modificateur d’accès pour l’accesseur Set pour la propriété générée (`public`, `internal`, `private`, `protected`, ou `protected internal`).|`public`|
|Multiplicité|Le nombre d’éléments de modèle qui peuvent jouer le rôle opposé (`0..1`, `1..1`, `0..*`, ou `1..*`). Si la multiplicité est `0..*` ou `1..*`, puis la propriété générée représente une collection ; sinon, la propriété générée représente un élément de modèle unique.|Varie selon le type de relation et si c’est le rôle source ou cible dans la relation.|
|Name|Le nom du rôle de domaine. Cette propriété ne peut pas contenir un espace blanc.|Le nom de la classe de domaine de l’acteur de rôle pour ce rôle.|
|Propage la copie|`DoNotPropagateCopy` -L’acteur de rôle copié n’aura aucune copie de ce lien.<br /><br /> `PropagateCopyToLinkOnly` -Les points de lien copié à l’objet de l’acteur de rôle opposé.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Le lien copié pointe vers une copie de l’acteur de rôle opposé.|`PropagateCopyToLinkAndOppositeRolePlayer` pour les rôles de la source des incorporations.<br /><br /> `DoNotPropagateCopy` pour d’autres rôles.<br /><br /> Pour plus d’informations, consultez [personnalisation du comportement de copie](../modeling/customizing-copy-behavior.md)|
|Propage la suppression|`True` Pour supprimer l’élément qui joue ce rôle lorsque le lien associé est supprimé.|`True` pour la cible d’un rôle d’incorporation.<br /><br /> `False` pour d’autres rôles.<br /><br /> Pour plus d’informations, consultez [personnalisation du comportement de suppression](../modeling/customizing-deletion-behavior.md).|
|Nom de la propriété|Le nom de la propriété générée dans le code de l’acteur de rôle. Ce nom ne peut pas contenir d’espaces blancs.|Le nom du rôle opposé si ce rôle dispose d’un zéro-à-un ou une-à-un multiplicité ; Sinon, le nom pluralisée du rôle opposé.|
|Acteur de rôle|La classe de domaine de l’élément qui peut jouer ce rôle dans la relation. Cette propriété est en lecture seule.|La classe de domaine de l’acteur de rôle pour ce rôle.|
|Notes|Remarques informelles associées avec le rôle de domaine.|< aucun\>|
|Category|La catégorie sous laquelle la propriété générée apparaît dans le **propriétés** fenêtre dans le concepteur généré. Si cette propriété est vide, la propriété générée apparaît sous le **divers** catégorie|< aucun\>|
|Description|La description qui est utilisée pour documenter le code et est utilisée dans l’interface utilisateur du concepteur généré.<br /><br /> La description s’affiche dans l’info-bulle IntelliSense pour la propriété générée sur la classe d’acteur de rôle.|`Description for` *le nom complet du rôle*|
|Nom complet|Le nom qui s’affiche dans le concepteur généré pour le rôle de domaine.|Valeur ajustée de la propriété Name.|
|Help Keyword|Le mot clé facultatif qui est utilisé pour indexer l’aide F1 pour le rôle de domaine.|\<aucune>|
|Nom d’affichage de propriété|Le nom qui s’affiche dans le concepteur généré pour la propriété de rôle généré.|La valeur de la propriété de nom de la propriété corrigée.|

> [!NOTE]
> La valeur par défaut d’un nom d’affichage est basée sur la valeur de propriété associée en insérant des espaces avant chaque caractère majuscule, qui est précédé par un caractère minuscule, et qui n’est pas suivi par un autre caractère majuscule.

## <a name="see-also"></a>Voir aussi

- [Propriétés des relations de domaine](../modeling/properties-of-domain-relationships.md)