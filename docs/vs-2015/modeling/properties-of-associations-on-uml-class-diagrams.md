---
title: Propriétés des associations dans les diagrammes de classes UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c5c914d87f0740dcd7b0f71190a4c2f54727f66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652090"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>Propriétés des associations dans les diagrammes de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un diagramme de classes UML, vous pouvez dessiner des *associations* entre n’importe quelle paire de types. Un type est une classe, une interface ou une énumération.

 Une association indique que le système que vous développez stocke des liens d'un genre spécifique entre les instances des types associés. En général, elle n'indique rien concernant l'implémentation des liens. Par exemple, il peut s'agir de pointeurs, de lignes d'une table, de noms faisant l'objet de références croisées au format XML, etc.

 Une association est une méthode schématique permettant d'afficher un attribut ou une paire d'attributs. Par exemple, si vous avez défini une classe Restaurant avec un attribut de type Menu, vous pouvez déclarer la même définition en dessinant une association entre Restaurant et Menu.

 Pour dessiner une association, cliquez sur **Association** dans la boîte à outils, cliquez sur le premier type, puis sur le second. Vous pouvez cliquer deux fois sur le même type pour indiquer que les instances peuvent être associées à d'autres instances du même type.

## <a name="properties"></a>Propriétés
 Il s'agit des propriétés d'une association dans un diagramme de classes UML.

 Pour afficher les propriétés d’une association, cliquez avec le bouton droit sur l’Association, puis cliquez sur **Propriétés**. Les propriétés s'affichent dans la fenêtre Propriétés.

 Certaines des propriétés sont également visibles dans le diagramme, comme le montre l'illustration suivante.

 ![Propriétés sur les associations](../modeling/media/uml-classprop.png "UML_ClassProp")

|**Propriété**|Description|
|------------------|-----------------|
|**Nom (1)**|Identifie l'association. Apparaît également dans le diagramme, près du point central de l'association.|
|**Nom qualifié**|Identifie l'association de manière unique. A pour préfixe le nom qualifié du package qui contient le premier rôle de l'association.|
|**Éléments de travail**|Nombre d'éléments de travail liés à cette association. Pour lier des éléments de travail, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|
|**Couleur**|Couleur du connecteur. Contrairement aux autres propriétés, il s'agit d'une propriété de cette vue de l'association, et non d'une propriété de la relation sous-jacente dans le modèle.|
|**First Role**<br /><br /> **Second Role**|Chaque extrémité de l'association correspond à un rôle. Chaque rôle décrit les propriétés de l'attribut équivalent sur la classe, à l'extrémité opposée de l'association.<br /><br /> Dans l'exemple de diagramme, l'association entre Menu et Élément de menu dispose de rôles appelés Menu et Contenu.<br /><br /> Le contenu correspond au nom d'un attribut sur la classe Menu.|

### <a name="properties-of-each-role"></a>Propriétés de chaque rôle
 Pour afficher les propriétés de chaque rôle, développez le **premier rôle** ou la deuxième propriété de **rôle** .

|     **Propriété**     |          **Par défaut**          |                                                                                                                                                                                                                                                                                                                                        Description                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Role Name (2)**   | Nom du type de ce rôle |                                                                                                                                                                                                                                                                                                       Nom du rôle. Apparaît près de l'extrémité de l'association dans le diagramme.                                                                                                                                                                                                                                                                                                        |
|   **Agrégation**    |             None              |                                                                        **None** (4) : représente une relation générale entre des instances des classes.<br /><br /> **Composite** (5) : l’objet de ce rôle contient l’objet au rôle opposé. Vous pouvez utiliser l’outil **composite** pour créer une association avec l’agrégation composite.<br /><br /> **Shared** (6) : l’objet de ce rôle contient des références à l’objet à l’autre rôle. Vous pouvez utiliser l’outil d' **agrégation** pour créer une association avec l’agrégation partagée.<br /><br /> L'interprétation exacte est ouverte à la convention locale.                                                                         |
|    **Is Derived**    |             Faux             |                                                                                                                                                                                                                          Si la valeur est True, l'objet se trouvant à cette extrémité du lien est calculé à partir d'autres attributs et associations. Par exemple, MyWorkPlace est calculé à partir de MyEmployer.WorkPlace. Les détails doivent être tapés dans la description ou un commentaire joint.                                                                                                                                                                                                                           |
| **Is Derived Union** |             Faux             |                                                                                                                                                                                                                                                                                                             Si la valeur est True, le rôle correspond à l'union d'un ensemble de rôles dans les types dérivés.                                                                                                                                                                                                                                                                                                             |
|   **Is Navigable**   |             Vrai              |                                                 L'association peut être lue dans cette direction. En fonction d'une instance du rôle opposé, les logiciels que vous décrivez peuvent déterminer efficacement l'instance associée dans ce rôle.<br /><br /> Si un rôle est navigable et que l'autre ne l'est pas, une flèche apparaît (7) sur l'association dans la direction navigable.<br /><br /> Par défaut, l'outil d'association crée une association qui est navigable dans une seule direction. Pour le convertir en association bidirectionnelle, vous pouvez sélectionner l’Association, cliquer sur la balise d’action qui s’affiche, puis cliquer sur **Make bidirectionnel**.                                                 |
|   **Est en lecture seule**   |             Faux             |                                                                                                                                                                                                                                                                                   Si la valeur est True, une instance de l'association ne peut pas être modifiée après sa création. Le lien pointe toujours vers le même objet.                                                                                                                                                                                                                                                                                    |
| **Multiplicity (3)** |               1               | **1** -cette terminaison de l’Association est toujours liée à un objet. Dans l'illustration, chaque élément de menu possède un menu.<br /><br /> **0.. 1** -soit cette terminaison de l’Association est liée à un objet, soit il n’y a aucun lien.<br /><br /> **\\**\* -chaque objet à l’autre extrémité de l’Association est lié à une collection d’objets à cette fin, et la collection peut être vide.<br /><br /> **1.. \\ ** \* -chaque objet à l’autre extrémité de l’Association est lié à au moins un objet à cette fin. Dans l'illustration, chaque menu possède au moins un élément de menu.<br /><br /> *n* **..** *m* -chaque objet à l’autre extrémité a une collection de liens entre *n* et *m* et des objets à cette fin. |
|    **Is Ordered**    |             Faux             |                                                                                                                                                                                                                                                                                                  Si la valeur est True, la collection retournée forme une liste séquentielle. Pour une valeur Multiplicity supérieure à 1.                                                                                                                                                                                                                                                                                                   |
|    **Est unique**     |             Faux             |                                                                                                                                                                                                                                                                                              Si la valeur est True, la collection retournée ne contient pas de valeur en double. Pour une valeur Multiplicity supérieure à 1.                                                                                                                                                                                                                                                                                              |
|    **Visibilité**    |            Public             |                                                                                                                                                                                                                                 Public : visible globalement<br /><br /> Private : non visible en dehors du type propriétaire<br /><br /> Protected : visible par les types dérivés du propriétaire<br /><br /> Package : visible par les autres types dans le même package                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Voir aussi
 [Diagrammes de classes UML : référencer](../modeling/uml-class-diagrams-reference.md) [des propriétés de types dans des diagrammes de classes UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [propriétés d’attributs sur des diagrammes de classes UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [propriétés d’opérations sur](../modeling/properties-of-operations-on-uml-class-diagrams.md) des diagrammes de classes UML [diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)
