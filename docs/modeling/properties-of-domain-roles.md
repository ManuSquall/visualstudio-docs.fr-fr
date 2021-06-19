---
title: Propriétés des rôles de domaine
description: En savoir plus sur les propriétés associées à un rôle de domaine, telles que le type de collection, les attributs de personnalisation et l’exploration des propriétés.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 670704a86f0c149d26c7c869259c0f2f6bb75881
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385146"
---
# <a name="properties-of-domain-roles"></a>Propriétés des rôles de domaine
Les propriétés du tableau suivant sont associées à un rôle de domaine. Pour plus d’informations sur les rôles de domaine, consultez [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriété|Description|Default|
|-|-|-|
|Type de collection|Si ce rôle a la multiplicité 0.. * ou 1.. \* , cette propriété personnalise le type générique utilisé pour stocker la collection de liens.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> est utilisé|
|Attributs personnalisés|Les attributs que vous spécifiez ici seront ajoutés en tant qu’attributs à la classe de code générée.|<aucun\>|
|Est une propriété pouvant être explorée|Si `True` , et si la multiplicité de la relation est 0.. 1 ou 1.. 1, la propriété de rôle peut être parcourue par l’utilisateur dans la fenêtre **Propriétés** . La propriété affiche le nom de l’élément à l’autre extrémité du lien de relation.|`True`|
|Est un générateur de propriétés|Si la valeur `True` est, une propriété de rôle est générée pour ce rôle, que vous pouvez utiliser pour parcourir la relation dans le code de programme. Si vous définissez cette valeur false, vous pouvez parcourir la relation de manière moins efficace à l’aide de méthodes statiques de la relation de domaine.|`True`|
|Modificateur d’accès de l’accesseur Get de propriété|Modificateur d’accès pour l’accesseur Get de la propriété générée ( `public` , `internal` ,, `private` `protected` ou `protected internal` ).|`public`|
|Modificateur d’accès de la propriété Setter|Modificateur d’accès pour la méthode setter de la propriété générée ( `public` , `internal` ,, `private` `protected` ou `protected internal` ).|`public`|
|Multiplicité|Nombre d’éléments de modèle qui peuvent jouer le rôle opposé ( `0..1` , `1..1` , `0..*` ou `1..*` ). Si la multiplicité est `0..*` ou `1..*` , la propriété générée représente une collection ; sinon, la propriété générée représente un élément de modèle unique.|Dépend du type de relation et s’il s’agit du rôle source ou cible dans la relation.|
|Nom|Nom du rôle de domaine. Cette propriété ne peut pas contenir d’espace blanc.|Nom de la classe de domaine de l’acteur de rôle pour ce rôle.|
|Propage la copie|`DoNotPropagateCopy` -L’acteur de rôle copié n’a pas de copie de ce lien.<br /><br /> `PropagateCopyToLinkOnly` -Le lien copié pointe vers l’acteur de rôle opposé existant.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Le lien copié pointe vers une copie de l’acteur de rôle opposé.|`PropagateCopyToLinkAndOppositeRolePlayer` pour les rôles sources des incorporations.<br /><br /> `DoNotPropagateCopy` pour les autres rôles.<br /><br /> Pour plus d’informations, consultez [Personnalisation du comportement](../modeling/customizing-copy-behavior.md) de la copie|
|Propage la suppression|`True` pour supprimer l’élément qui joue ce rôle lorsque le lien associé est supprimé.|`True` pour la cible d’un rôle d’incorporation.<br /><br /> `False` pour les autres rôles.|
|Nom de la propriété|Nom de la propriété générée dans le code de l’acteur de rôle. Ce nom ne peut pas contenir d’espaces.|Nom du rôle opposé si ce rôle a une multiplicité de zéro à un ou un-à-un ; dans le cas contraire, le nom au pluriel du rôle opposé.|
|Joueur de rôle|Classe de domaine de l’élément qui peut jouer ce rôle dans la relation. Cette propriété est en lecture seule.|Classe de domaine de l’acteur de rôle pour ce rôle.|
|Notes|Notes informelles associées au rôle de domaine.|<aucun\>|
|Category|Catégorie sous laquelle la propriété générée apparaît dans la fenêtre **Propriétés** du concepteur généré. Si cette propriété est vide, la propriété générée apparaît sous la catégorie **divers** .|<aucun\>|
|Description|Description utilisée pour documenter le code et utilisée dans l’interface utilisateur du concepteur généré.<br /><br /> La description s’affiche dans l’info-bulle IntelliSense pour la propriété générée sur la classe de l’acteur de rôle.|`Description for`*nom complet du rôle*|
|Nom d’affichage|Nom affiché dans le concepteur généré pour le rôle de domaine.|Valeur ajustée de la propriété Name.|
|Help Keyword|Mot clé facultatif utilisé pour indexer l’aide F1 pour le rôle de domaine.|\<none>|
|Nom complet de la propriété|Nom affiché dans le concepteur généré pour la propriété de rôle générée.|Valeur ajustée de la propriété nom de la propriété.|

> [!NOTE]
> La valeur par défaut d’un nom complet est basée sur la valeur de propriété associée en insérant des espaces avant chaque caractère majuscule précédé d’un caractère minuscule et qui n’est pas suivi d’un autre caractère majuscule.

## <a name="see-also"></a>Voir aussi

- [Propriétés des relations de domaine](../modeling/properties-of-domain-relationships.md)