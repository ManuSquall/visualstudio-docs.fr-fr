---
title: Boîte de dialogue Définition de la Concepteur de flux de travail CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 401f72f55f23779f7c6257437034a4ebc294d219
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650599"
---
# <a name="correlateson-definition-dialog-box"></a>Boîte de dialogue Définition CorrelatesOn

La boîte de dialogue **CorrelatesOn** est utilisée dans Concepteur de flux de travail pour modifier la propriété <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> d’une activité <xref:System.ServiceModel.Activities.Receive>. Pour plus d’informations, consultez le [Concepteur d’activités Receive](../workflow-designer/receive-activity-designer.md).

La corrélation entre les activités <xref:System.ServiceModel.Activities.Receive> spécifie la manière dont différentes opérations de service se connectent les unes aux autres dans un workflow.

Le tableau suivant décrit les éléments d’interface utilisateur (IU) de la boîte de dialogue **CorrelatesOn** .

|Élément d'interface utilisateur|Description|
|-|-----------------|
|**CorrelatesWith**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour router le message vers l'instance de workflow appropriée.|
|**Requêtes XPath**|Paire clé/valeur qui contient les requêtes utilisées pour extraire les données de corrélation des messages entrants. Cette valeur correspond à la propriété <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Les requêtes XPath sont contenues dans un objet <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Pour lancer la boîte de dialogue Définition CorrelatesOn

Le concepteur d’activités **Receive** peut être déplacé de la **boîte à outils** et déposé dans l’aire de concepteur de flux de travail, où les activités sont généralement placées. La suppression du concepteur d’activités crée une activité <xref:System.ServiceModel.Activities.Receive> avec un <xref:System.Activities.Activity.DisplayName%2A> par défaut Receive. Pour ouvrir la boîte de dialogue **Définition CorrelatesOn** , sélectionnez le concepteur d’activités **Receive** , puis dans la grille des propriétés, sélectionnez le bouton de sélection en regard du texte de la collection pour la propriété **CorrelatesOn** .

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.Receive>
- [Ajouter des initialiseurs de corrélation, boîte de dialogue](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Initialiser la corrélation, boîte de dialogue](../workflow-designer/initialize-correlation-dialog-box.md)