---
title: Boîte de dialogue Définition de la Concepteur de flux de travail CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d2db5bbfa4f34d86d3bf20cfe6bcc42b3dc00d0
ms.sourcegitcommit: 186c0c250d85ac74274fa1e438b4c7c7108d8a36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86876123"
---
# <a name="correlateson-definition-dialog-box"></a>Boîte de dialogue Définition CorrelatesOn

La boîte de dialogue **CorrelatesOn** est utilisée dans Concepteur de flux de travail pour modifier la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriété d’une <xref:System.ServiceModel.Activities.Receive> activité. Pour plus d’informations, consultez le [Concepteur d’activités Receive](../workflow-designer/receive-activity-designer.md).

La corrélation entre les activités <xref:System.ServiceModel.Activities.Receive> spécifie la manière dont différentes opérations de service se connectent les unes aux autres dans un workflow.

Le tableau suivant décrit les éléments d’interface utilisateur (IU) de la boîte de dialogue **CorrelatesOn** .

|Élément de l’interface utilisateur|Description|
|-|-----------------|
|**CorrelatesWith**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour router le message vers l'instance de workflow appropriée.|
|**Requêtes XPath**|Paire clé/valeur qui contient les requêtes utilisées pour extraire les données de corrélation des messages entrants. Cette valeur correspond à la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriété. Les requêtes XPath sont contenues dans un objet <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Pour lancer la boîte de dialogue Définition CorrelatesOn

Le concepteur d’activités **Receive** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, où les activités sont généralement placées. La suppression du concepteur d’activités crée une <xref:System.ServiceModel.Activities.Receive> activité avec la valeur Receive par défaut <xref:System.Activities.Activity.DisplayName%2A> . Pour ouvrir la boîte de dialogue **Définition CorrelatesOn** , sélectionnez le concepteur d’activités **Receive** , puis dans la grille des propriétés, sélectionnez le bouton de sélection en regard du texte de la collection pour la propriété **CorrelatesOn** .

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.Receive>
- [Boîte de dialogue Ajouter des initialiseurs de corrélation](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Boîte de dialogue Initialiser la corrélation](../workflow-designer/initialize-correlation-dialog-box.md)