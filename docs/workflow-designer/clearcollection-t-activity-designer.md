---
title: Concepteur d’activités Concepteur de flux de travail-ClearCollection &lt; T &gt;
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 710e221441736ecb2415aec32c7f0bfb9a2d99ac
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711623"
---
# <a name="clearcollectiont-activity-designer"></a>Concepteur d’activités ClearCollection\<T>

Le concepteur d’activités ** \<T> ClearCollection** permet de créer et de configurer une <xref:System.Activities.Statements.ClearCollection%601> activité.

## <a name="the-clearcollectiont-activity"></a>Activité ClearCollection \<T>

L’activité <xref:System.Activities.Statements.ClearCollection%601> efface tous les éléments d’une collection spécifiée.

### <a name="using-the-clearcollectiont-activity-designer"></a>Utilisation du \<T> Concepteur d’activités ClearCollection

Le concepteur d’activités **ClearCollection \<T> ** se trouve dans la catégorie **collection** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** de la concepteur de flux de travail. Vous pouvez également sélectionner **boîte à outils** dans le menu **affichage** ou appuyer sur **CTRL** + **ALT** + **X**.

Le concepteur d’activités **ClearCollection \<T> ** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, là où les activités sont placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . La suppression du concepteur d’activités crée une <xref:System.Activities.Statements.ClearCollection%601> activité avec la valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> ClearCollection<Int32 \> . (Par défaut, le *TypeArgument* est **Int32**. TypeArgument peut être modifié dans la grille des propriétés.) La <xref:System.Activities.Activity.DisplayName%2A> valeur peut être modifiée dans l’en-tête du concepteur d’activités **ClearCollection<T \> ** ou dans la zone **DisplayName** de la grille des propriétés. Les autres propriétés doivent être modifiées dans la grille des propriétés.

### <a name="the-clearcollectiont-properties"></a>Propriétés ClearCollection \<T>

Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.ClearCollection%601> et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Spécifie le nom convivial facultatif de l'activité <xref:System.Activities.Statements.ClearCollection%601>. La valeur par défaut est ClearCollection<Int32 \> . Bien que la valeur de la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Spécifie la collection dont les éléments doivent être effacés. Cette collection est de type **ICollection \<TypeArgument> .** Pour spécifier la collection, tapez une expression Visual Basic dans la grille des propriétés.|
|*TypeArgument*|True|Spécifie le type T des éléments contenus dans l'objet <xref:System.Collections.Generic.ICollection%601>. Par défaut, ce type de *TypeArgument* est défini sur **Int32**. Pour modifier le type, modifiez la valeur de *TypeArgument* dans la zone de liste déroulante de la grille des propriétés.|

## <a name="see-also"></a>Voir aussi

- [Collection](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)