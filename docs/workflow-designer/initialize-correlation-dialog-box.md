---
title: Initialiser la boîte de dialogue de corrélation | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aac62d4439c2280e977ef929c79bb103348c170a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="initialize-correlation-dialog-box"></a>Boîte de dialogue Initialiser la corrélation

Le **initialiser la corrélation** boîte de dialogue est utilisée dans le Concepteur de flux de travail Windows pour modifier la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriété d’un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité. Pour plus d’informations, consultez la [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) rubrique.

 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **initialiser la corrélation** boîte de dialogue.

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Corrélation**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> de la corrélation à initialiser.|
|**Initialiser sur**|Paire clé/valeur qui contient les données à initialiser. Cette valeur correspond à la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Un exemple d’une paire clé/valeur valide est une clé nommée « OrderID » associée à une variable nommée OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Pour lancer la boîte de dialogue Initialiser la corrélation

-   Cliquez sur **vue** sur la **InitializeCorrelation** activité concepteur ou sélectionnez un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] puis cliquez sur le bouton de sélection à côté du <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriété dans la grille des propriétés.

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)