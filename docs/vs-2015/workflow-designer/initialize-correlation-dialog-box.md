---
title: Boîte de dialogue initialiser la corrélation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ab913027a6a992494dad609b98ab11dbc6ae61c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659053"
---
# <a name="initialize-correlation-dialog-box"></a>Boîte de dialogue Initialiser la corrélation
La boîte de dialogue **initialiser la corrélation** est utilisée dans [!INCLUDE[wfd1](../includes/wfd1-md.md)] pour modifier la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> d’une activité <xref:System.ServiceModel.Activities.InitializeCorrelation>. [!INCLUDE[crdefault](../includes/crdefault-md.md)] la rubrique [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) .

 Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **initialiser la corrélation** .

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Corrélation**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> de la corrélation à initialiser.|
|**Initialiser sur**|Paire clé/valeur qui contient les données à initialiser. Cette valeur correspond à la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Une clé nommée « OrderID » associée à une variable nommé « OrderID » constitue un exemple de paire clé/valeur valide.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Pour lancer la boîte de dialogue Initialiser la corrélation

- Cliquez sur **affichage** dans le concepteur d’activités **InitializeCorrelation** ou sélectionnez une activité <xref:System.ServiceModel.Activities.InitializeCorrelation> dans [!INCLUDE[wfd2](../includes/wfd2-md.md)] puis cliquez sur le bouton de sélection en regard de la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> dans la grille des propriétés.

## <a name="see-also"></a>Voir aussi
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)