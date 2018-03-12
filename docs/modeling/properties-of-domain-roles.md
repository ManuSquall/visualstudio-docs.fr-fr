---
title: "Propriétés des rôles de domaine | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 61537deec73a5da8d647639a588641d7cf773da3
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2018
---
# <a name="properties-of-domain-roles"></a>Propriétés des rôles de domaine
Les propriétés dans le tableau suivant sont associées à un rôle de domaine. Pour plus d’informations sur les rôles de domaine, consultez [fonctionnement des modèles, des Classes et des relations](../modeling/understanding-models-classes-and-relationships.md). Pour plus d’informations sur la façon d’utiliser ces propriétés, consultez [personnalisation et l’extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriété|Description|Par défaut|
|--------------|-----------------|-------------|
|Type de collection|Si ce rôle a une multiplicité 0.. * ou 1... \*, cette propriété personnalise le type générique qui est utilisé pour stocker la collection de liens.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> est utilisé|
|Attributs personnalisés|Les attributs que vous spécifiez ici seront ajoutés en tant qu’attributs à la classe du code généré.|< aucun\>|
|Propriété ne se prête|Si `True`, et si la multiplicité de la relation est la valeur 0.. 1 ou 1.. 1, la propriété de rôle peut être parcourue par l’utilisateur dans le **propriétés** fenêtre. La propriété affiche le nom de l’élément à l’autre extrémité du lien de relation.|`True`|
|Générateur de propriété|Si `True`, une propriété de rôle est générée pour ce rôle, vous pouvez utiliser pour parcourir la relation dans le code de programme. Si vous affectez la valeur false, vous pouvez parcourir la relation de manière moins efficace à l’aide des méthodes statiques de la relation de domaine.|`True`|
|Modificateur d’accès de l’accesseur Get de propriété|Le modificateur d’accès pour l’accesseur Get de la propriété générée (`public`, `internal`, `private`, `protected`, ou `protected internal`).|`public`|
|Modificateur d’accès de la méthode Setter de propriété|Le modificateur d’accès pour l’accesseur Set pour la propriété générée (`public`, `internal`, `private`, `protected`, ou `protected internal`).|`public`|
|Multiplicité|Le nombre d’éléments de modèle qui peut jouer le rôle opposé (`0..1`, `1..1`, `0..*`, ou `1..*`). Si la multiplicité est `0..*` ou `1..*`, puis la propriété générée représente une collection ; sinon, la propriété générée représente un élément de modèle unique.|Dépend du type de relation et si c’est le rôle de source ou cible dans la relation.|
|Name|Le nom du rôle de domaine. Cette propriété ne peut pas contenir un espace blanc.|Le nom de la classe de domaine de l’acteur de rôle pour ce rôle.|
|Propage la copie|`DoNotPropagateCopy` -L’acteur de rôle copié n’aura aucune copie de ce lien.<br /><br /> `PropagateCopyToLinkOnly` -Les points de lien copié à l’acteur de rôle opposé.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Le lien copié pointe vers une copie de l’acteur de rôle opposé.|`PropagateCopyToLinkAndOppositeRolePlayer` pour les rôles de la source des incorporations.<br /><br /> `DoNotPropagateCopy` pour d’autres rôles.<br /><br /> Pour plus d’informations, consultez [personnalisation de comportement de copie](../modeling/customizing-copy-behavior.md)|
|Propage la suppression|`True` Pour supprimer l’élément qui joue ce rôle lorsque le lien associé est supprimé.|`True` pour la cible d’un rôle d’incorporation.<br /><br /> `False` pour d’autres rôles.<br /><br /> Pour plus d’informations, consultez [comportement de suppression de personnalisation](../modeling/customizing-deletion-behavior.md).|
|Nom de la propriété|Le nom de la propriété générée dans le code de l’acteur de rôle. Ce nom ne peut pas contenir d’espaces blancs.|Le nom de rôle opposé si ce rôle dispose d’un zéro-à-un ou une multiplicité de 1 à 1 ; Sinon, le nom pluralized de rôle opposé.|
|Acteur de rôle|La classe de domaine de l’élément qui peut jouer ce rôle dans la relation. Cette propriété est en lecture seule.|La classe de domaine de l’acteur de rôle pour ce rôle.|
|Notes|Notes informelles qui sont associées au rôle de domaine.|< aucun\>|
|Category|La catégorie sous laquelle la propriété générée s’affiche dans le **propriétés** fenêtre du concepteur généré. Si cette propriété est vide, la propriété générée apparaît sous le **divers** catégorie|< aucun\>|
|Description|La description qui est utilisée pour documenter du code et est utilisée dans l’interface utilisateur du concepteur généré.<br /><br /> La description s’affiche dans l’info-bulle IntelliSense pour la propriété générée sur la classe d’acteur de rôle.|`Description for` *le nom complet du rôle*|
|Nom complet|Le nom qui s’affiche dans le concepteur généré pour le rôle de domaine.|La valeur ajustée de la propriété Name.|
|Help Keyword|Le mot clé facultatif qui sert à l’index d’aide (F1) pour le rôle de domaine.|\<none>|
|Nom complet de propriété|Le nom qui s’affiche dans le concepteur généré pour la propriété role généré.|La valeur de la propriété de nom de la propriété ajustée.|

> [!NOTE]
>  La valeur par défaut d’un nom d’affichage est basée sur la valeur de propriété associée en insérant des espaces avant chaque caractère majuscule, qui est précédé d’un caractère en minuscule, et qui n’est pas suivi d’un autre caractère majuscule.

## <a name="see-also"></a>Voir aussi
 [Propriétés des relations de domaine](../modeling/properties-of-domain-relationships.md)