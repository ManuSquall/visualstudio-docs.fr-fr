---
title: Propriétés des rôles de domaine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a0cddfb3d5c95e5636e9dac069106e3010bedff8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671467"
---
# <a name="properties-of-domain-roles"></a>Propriétés des rôles de domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les propriétés du tableau suivant sont associées à un rôle de domaine. Pour plus d’informations sur les rôles de domaine, consultez [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur l’utilisation de ces propriétés, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Property|Description|Valeur par défaut|
|--------------|-----------------|-------------|
|Type de collection|Si ce rôle a la multiplicité 0.. * ou 1.. \*, cette propriété personnalise le type générique utilisé pour stocker la collection de liens.|`(none)`  -  <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> est utilisé|
|Attributs personnalisés|Les attributs que vous spécifiez ici seront ajoutés en tant qu’attributs à la classe de code générée.|\<aucune>|
|Est une propriété pouvant être explorée|Si `True` et si la multiplicité de la relation est 0.. 1 ou 1.. 1, la propriété de rôle peut être parcourue par l’utilisateur dans la fenêtre **Propriétés** . La propriété affiche le nom de l’élément à l’autre extrémité du lien de relation.|`True`|
|Est un générateur de propriétés|Si `True`, une propriété de rôle est générée pour ce rôle, que vous pouvez utiliser pour parcourir la relation dans le code de programme. Si vous définissez cette valeur false, vous pouvez parcourir la relation de manière moins efficace à l’aide de méthodes statiques de la relation de domaine.|`True`|
|Modificateur d’accès de l’accesseur Get de propriété|Modificateur d’accès pour l’accesseur Get de la propriété générée (`public`, `internal`, `private`, `protected` ou `protected internal`).|`public`|
|Modificateur d’accès de la propriété Setter|Modificateur d’accès pour la méthode setter de la propriété générée (`public`, `internal`, `private`, `protected` ou `protected internal`).|`public`|
|Multiplicité|Nombre d’éléments de modèle qui peuvent jouer le rôle opposé (`0..1`, `1..1`, `0..*` ou `1..*`). Si la multiplicité est `0..*` ou `1..*`, la propriété générée représente une collection ; dans le cas contraire, la propriété générée représente un élément de modèle unique.|Dépend du type de relation et s’il s’agit du rôle source ou cible dans la relation.|
|Name|Nom du rôle de domaine. Cette propriété ne peut pas contenir d’espace blanc.|Nom de la classe de domaine de l’acteur de rôle pour ce rôle.|
|Propage la copie|`DoNotPropagateCopy`-l’acteur de rôle copié n’a pas de copie de ce lien.<br /><br /> `PropagateCopyToLinkOnly`-le lien copié pointe vers l’acteur de rôle opposé existant.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`-le lien copié pointe vers une copie de l’acteur de rôle opposé.|`PropagateCopyToLinkAndOppositeRolePlayer` pour les rôles source des incorporations.<br /><br /> `DoNotPropagateCopy` pour d’autres rôles.<br /><br /> Pour plus d’informations, consultez [Personnalisation du comportement](../modeling/customizing-copy-behavior.md) de la copie|
|Propage la suppression|`True` de supprimer l’élément qui joue ce rôle lorsque le lien associé est supprimé.|`True` pour la cible d’un rôle d’incorporation.<br /><br /> `False` pour d’autres rôles.<br /><br /> Pour plus d’informations, consultez [Personnalisation du comportement de suppression](../modeling/customizing-deletion-behavior.md).|
|Nom de propriété|Nom de la propriété générée dans le code de l’acteur de rôle. Ce nom ne peut pas contenir d’espaces.|Nom du rôle opposé si ce rôle a une multiplicité de zéro à un ou un-à-un ; dans le cas contraire, le nom au pluriel du rôle opposé.|
|Joueur de rôle|Classe de domaine de l’élément qui peut jouer ce rôle dans la relation. Cette propriété est en lecture seule.|Classe de domaine de l’acteur de rôle pour ce rôle.|
|Notes|Notes informelles associées au rôle de domaine.|\<aucune>|
|Category|Catégorie sous laquelle la propriété générée apparaît dans la fenêtre **Propriétés** du concepteur généré. Si cette propriété est vide, la propriété générée apparaît sous la catégorie **divers** .|\<aucune>|
|Description|Description utilisée pour documenter le code et utilisée dans l’interface utilisateur du concepteur généré.<br /><br /> La description s’affiche dans l’info-bulle IntelliSense pour la propriété générée sur la classe de l’acteur de rôle.|`Description for` *le nom complet du rôle*|
|Display Name|Nom affiché dans le concepteur généré pour le rôle de domaine.|Valeur ajustée de la propriété Name.|
|Help Keyword|Mot clé facultatif utilisé pour indexer l’aide F1 pour le rôle de domaine.|\<aucune>|
|Nom complet de la propriété|Nom affiché dans le concepteur généré pour la propriété de rôle générée.|Valeur ajustée de la propriété nom de la propriété.|

> [!NOTE]
> La valeur par défaut d’un nom complet est basée sur la valeur de propriété associée en insérant des espaces avant chaque caractère majuscule précédé d’un caractère minuscule et qui n’est pas suivi d’un autre caractère majuscule.

## <a name="see-also"></a>Voir aussi
 [Propriétés des relations de domaine](../modeling/properties-of-domain-relationships.md)
