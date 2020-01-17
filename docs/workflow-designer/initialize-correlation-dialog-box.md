---
title: Concepteur de flux de travail boîte de dialogue initialiser la corrélation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04f0a3bb70dbab31e0faa5c38caac9b54c6154fe
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114773"
---
# <a name="initialize-correlation-dialog-box"></a>Boîte de dialogue Initialiser la corrélation

La boîte de dialogue **initialiser la corrélation** est utilisée dans Concepteur de flux de travail pour modifier la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> d’une activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. Pour plus d’informations, consultez [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **initialiser la corrélation** :

|Élément de l'interface utilisateur|Description|
|-|-----------------|
|**Corrélation**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> de la corrélation à initialiser.|
|**Initialiser sur**|Paire clé/valeur qui contient les données à initialiser. Cette valeur correspond à la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Une clé nommée « OrderID » associée à une variable nommée OrderID est un exemple de paire clé/valeur valide.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Pour lancer la boîte de dialogue Initialiser la corrélation

Cliquez sur **Afficher** dans le concepteur d’activités **InitializeCorrelation** ou sélectionnez une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> dans Concepteur de flux de travail. Ensuite, cliquez sur le bouton de sélection en regard de la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> dans la grille des propriétés.

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
