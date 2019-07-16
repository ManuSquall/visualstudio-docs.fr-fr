---
title: Propriétés des associations dans UML des diagrammes de classes | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1c029a29b2d81f7a6ca64f47aab15caf5119d172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154885"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>Propriétés des associations dans les diagrammes de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un diagramme de classes UML, vous pouvez dessiner *associations* entre toute paire de types. Un type est une classe, une interface ou une énumération.  

 Une association indique que le système que vous développez stocke des liens d'un genre spécifique entre les instances des types associés. En général, elle n'indique rien concernant l'implémentation des liens. Par exemple, il peut s'agir de pointeurs, de lignes d'une table, de noms faisant l'objet de références croisées au format XML, etc.  

 Une association est une méthode schématique permettant d'afficher un attribut ou une paire d'attributs. Par exemple, si vous avez défini une classe Restaurant avec un attribut de type Menu, vous pouvez déclarer la même définition en dessinant une association entre Restaurant et Menu.  

 Pour dessiner une association, cliquez sur **Association** dans la boîte à outils, cliquez sur le premier type, puis sur le second. Vous pouvez cliquer deux fois sur le même type pour indiquer que les instances peuvent être associées à d'autres instances du même type.  

## <a name="properties"></a>Properties  
 Il s'agit des propriétés d'une association dans un diagramme de classes UML.  

 Pour afficher les propriétés d’une association, cliquez sur l’association, puis **propriétés**. Les propriétés s'affichent dans la fenêtre Propriétés.  

 Certaines des propriétés sont également visibles dans le diagramme, comme le montre l'illustration suivante.  

 ![Propriétés sur les associations](../modeling/media/uml-classprop.png "UML_ClassProp")  

|**Propriété**|Description|  
|------------------|-----------------|  
|**Nom (1)**|Identifie l'association. Apparaît également dans le diagramme, près du point central de l'association.|  
|**Nom qualifié**|Identifie l'association de manière unique. A pour préfixe le nom qualifié du package qui contient le premier rôle de l'association.|  
|**Éléments de travail**|Nombre d'éléments de travail liés à cette association. Pour lier des éléments de travail, voir [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|  
|**Couleur**|Couleur du connecteur. Contrairement aux autres propriétés, il s'agit d'une propriété de cette vue de l'association, et non d'une propriété de la relation sous-jacente dans le modèle.|  
|**Premier rôle**<br /><br /> **Second rôle**|Chaque extrémité de l'association correspond à un rôle. Chaque rôle décrit les propriétés de l'attribut équivalent sur la classe, à l'extrémité opposée de l'association.<br /><br /> Dans l'exemple de diagramme, l'association entre Menu et Élément de menu dispose de rôles appelés Menu et Contenu.<br /><br /> Le contenu correspond au nom d'un attribut sur la classe Menu.|  

### <a name="properties-of-each-role"></a>Propriétés de chaque rôle  
 Pour afficher les propriétés de chaque rôle, développez la **premier rôle** ou **Second rôle** propriété.  

|     **Propriété**     |          **Par défaut**          |                                                                                                                                                                                                                                                                                                                                        Description                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Nom du rôle (2)**   | Nom du type de ce rôle |                                                                                                                                                                                                                                                                                                       Nom du rôle. Apparaît près de l'extrémité de l'association dans le diagramme.                                                                                                                                                                                                                                                                                                        |
|   **Aggregation**    |             Aucun              |                                                                        **Aucun** (4) - représente une relation générale entre les instances des classes.<br /><br /> **Composite** (5) : l’objet de ce rôle contient l’objet du rôle opposé. Vous pouvez utiliser la **Composite** outil pour créer une association avec une agrégation Composite.<br /><br /> **Partagé** (6) - objet de ce rôle contient des références à l’objet à l’autre rôle. Vous pouvez utiliser la **agrégation** outil pour créer une association avec une agrégation partagée.<br /><br /> L'interprétation exacte est ouverte à la convention locale.                                                                         |
|    **Est dérivée**    |             False             |                                                                                                                                                                                                                          Si la valeur est True, l'objet se trouvant à cette extrémité du lien est calculé à partir d'autres attributs et associations. Par exemple, MyWorkPlace est calculé à partir de MyEmployer.WorkPlace. Les détails doivent être tapés dans la description ou un commentaire joint.                                                                                                                                                                                                                           |
| **Est dérivé d’Union** |             False             |                                                                                                                                                                                                                                                                                                             Si la valeur est True, le rôle correspond à l'union d'un ensemble de rôles dans les types dérivés.                                                                                                                                                                                                                                                                                                             |
|   **Est Navigable**   |             True              |                                                 L'association peut être lue dans cette direction. En fonction d'une instance du rôle opposé, les logiciels que vous décrivez peuvent déterminer efficacement l'instance associée dans ce rôle.<br /><br /> Si un rôle est navigable et que l'autre ne l'est pas, une flèche apparaît (7) sur l'association dans la direction navigable.<br /><br /> Par défaut, l'outil d'association crée une association qui est navigable dans une seule direction. Pour la convertir en association bidirectionnelle, vous pouvez sélectionner l’association, cliquez sur la balise d’Action qui s’affiche, puis cliquez sur **Make Bidirectional**.                                                 |
|   **Est en lecture seule**   |             False             |                                                                                                                                                                                                                                                                                   Si la valeur est True, une instance de l'association ne peut pas être modifiée après sa création. Le lien pointe toujours vers le même objet.                                                                                                                                                                                                                                                                                    |
| **Multiplicité (3)** |               1               | **1** -cette extrémité de l’association est toujours liée à un objet. Dans l'illustration, chaque élément de menu possède un menu.<br /><br /> **valeur 0.. 1** - soit cette extrémité de l’association liée à un objet, ou il n’existe aucun lien.<br /><br /> **\\** \* -chaque objet à l’autre extrémité de l’association est lié à une collection d’objets à cette fin, et la collection peut être vide.<br /><br /> **1..\\**  \* -chaque objet à l’autre extrémité de l’association est lié au moins un objet à cette fin. Dans l'illustration, chaque menu possède au moins un élément de menu.<br /><br /> *n* **..** *m* -chaque objet à l’autre extrémité possède une collection d’entre *n* et *m* des liens vers des objets de cette extrémité. |
|    **Est ordonné**    |             False             |                                                                                                                                                                                                                                                                                                  Si la valeur est True, la collection retournée forme une liste séquentielle. Pour une valeur Multiplicity supérieure à 1.                                                                                                                                                                                                                                                                                                   |
|    **Est unique**     |             False             |                                                                                                                                                                                                                                                                                              Si la valeur est True, la collection retournée ne contient pas de valeur en double. Pour une valeur Multiplicity supérieure à 1.                                                                                                                                                                                                                                                                                              |
|    **Visibilité**    |            Public             |                                                                                                                                                                                                                                 Public : visible globalement<br /><br /> Private : non visible en dehors du type propriétaire<br /><br /> Protected : visible par les types dérivés du propriétaire<br /><br /> Package : visible par les autres types dans le même package                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Voir aussi  
 [Diagrammes de classes UML : Référence](../modeling/uml-class-diagrams-reference.md)   
 [Propriétés de types de diagrammes de classes UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Propriétés d’attributs dans des diagrammes de classes UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Propriétés d’opérations sur les diagrammes de classes UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Diagrammes de classes UML : Recommandations](../modeling/uml-class-diagrams-guidelines.md)
