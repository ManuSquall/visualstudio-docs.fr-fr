---
title: Concepteur de flux de travail - boîte de dialogue initialiser la corrélation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fab86b39cd927d516bc627630a29feee1698daa
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919883"
---
# <a name="initialize-correlation-dialog-box"></a>Boîte de dialogue Initialiser la corrélation

Le **initialiser la corrélation** boîte de dialogue est utilisée dans le Concepteur de flux de travail pour modifier la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriété d’un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité. Pour plus d’informations, consultez [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md).

Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **initialiser la corrélation** boîte de dialogue :

|Élément d'interface utilisateur|Description|
|-|-----------------|
|**Corrélation**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> de la corrélation à initialiser.|
|**Initialiser sur**|Paire clé/valeur qui contient les données à initialiser. Cette valeur correspond à la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriété. Un exemple d’une paire clé/valeur valide est une clé nommée « OrderID » associée à une variable nommée OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Pour lancer la boîte de dialogue Initialiser la corrélation

Cliquez sur **vue** sur le **InitializeCorrelation** activité concepteur ou sélectionnez un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité dans le Concepteur de flux de travail. Ensuite, cliquez sur le bouton de sélection à côté du <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriété dans la grille des propriétés.

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)