---
title: Concepteur de flux de travail boîte de dialogue initialiser la corrélation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0b23f10184516ea4ffc3b00ac98e32ca8b387c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650191"
---
# <a name="initialize-correlation-dialog-box"></a>Boîte de dialogue Initialiser la corrélation

La boîte de dialogue **initialiser la corrélation** est utilisée dans Concepteur de flux de travail pour modifier la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> d’une activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. Pour plus d’informations, consultez [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **initialiser la corrélation** :

|Élément d'interface utilisateur|Description|
|-|-----------------|
|**Corrélation**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> de la corrélation à initialiser.|
|**Initialiser sur**|Paire clé/valeur qui contient les données à initialiser. Cette valeur correspond à la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Une clé nommée « OrderID » associée à une variable nommée OrderID est un exemple de paire clé/valeur valide.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Pour lancer la boîte de dialogue Initialiser la corrélation

Cliquez sur **Afficher** dans le concepteur d’activités **InitializeCorrelation** ou sélectionnez une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> dans Concepteur de flux de travail. Ensuite, cliquez sur le bouton de sélection en regard de la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> dans la grille des propriétés.

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)