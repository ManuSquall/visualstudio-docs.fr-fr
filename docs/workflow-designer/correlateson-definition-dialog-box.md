---
title: Concepteur de flux de travail - boîte de dialogue Définition CorrelatesOn
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7ed52f7898f10b5f13f55c27cba380334489871
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758132"
---
# <a name="correlateson-definition-dialog-box"></a>Boîte de dialogue Définition CorrelatesOn

Le **CorrelatesOn** boîte de dialogue est utilisée dans le Concepteur de flux de travail pour modifier la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriété d’un <xref:System.ServiceModel.Activities.Receive> activité. Pour plus d’informations, consultez [Concepteur d’activités de réception](../workflow-designer/receive-activity-designer.md).

La corrélation entre les activités <xref:System.ServiceModel.Activities.Receive> spécifie la manière dont différentes opérations de service se connectent les unes aux autres dans un workflow.

Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **CorrelatesOn** boîte de dialogue.

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**CorrelatesWith**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour router le message vers l'instance de workflow appropriée.|
|**Requêtes XPath**|Paire clé/valeur qui contient les requêtes utilisées pour extraire les données de corrélation des messages entrants. Cette valeur correspond à la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriété. Les requêtes XPath sont contenues dans un objet <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Pour lancer la boîte de dialogue Définition CorrelatesOn

Le **réception** Concepteur d’activités peut être déplacé de **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail, partout où les activités sont généralement placées. Suppression du Concepteur d’activités crée un <xref:System.ServiceModel.Activities.Receive> activité avec une valeur par défaut <xref:System.Activities.Activity.DisplayName%2A> de réception. Pour ouvrir le **définition CorrelatesOn** boîte de dialogue, sélectionnez le **réception** activité concepteur, puis dans la grille des propriétés, sélectionnez le bouton de sélection en regard du texte de la Collection pour le  **CorrelatesOn** propriété.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activities.Receive>
- [Ajouter des initialiseurs de corrélation, boîte de dialogue](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Ajouter la boîte de dialogue de corrélation](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Initialiser la corrélation, boîte de dialogue](../workflow-designer/initialize-correlation-dialog-box.md)