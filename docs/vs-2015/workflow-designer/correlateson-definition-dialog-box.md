---
title: Boîte de dialogue Définition CorrelatesOn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2a9a6f7ec6b8bf246ebfc03c166780b229e1aee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656935"
---
# <a name="correlateson-definition-dialog-box"></a>Boîte de dialogue Définition CorrelatesOn
La boîte de dialogue **CorrelatesOn** est utilisée dans [!INCLUDE[wfd1](../includes/wfd1-md.md)] pour modifier la propriété <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> d’une activité <xref:System.ServiceModel.Activities.Receive>. [!INCLUDE[crdefault](../includes/crdefault-md.md)] la rubrique [Receive](../workflow-designer/receive-activity-designer.md) .

 La corrélation entre les activités <xref:System.ServiceModel.Activities.Receive> spécifie la manière dont différentes opérations de service se connectent les unes aux autres dans un workflow.

 Le tableau suivant décrit les éléments d’interface utilisateur (IU) de la boîte de dialogue **CorrelatesOn** .

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**CorrelatesWith**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour router le message vers l'instance de workflow appropriée.|
|**Requêtes XPath**|Paire clé/valeur qui contient les requêtes utilisées pour extraire les données de corrélation des messages entrants. Cette valeur correspond à la propriété <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Les requêtes XPath sont contenues dans un objet <xref:System.ServiceModel.MessageQuerySet>.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Pour lancer la boîte de dialogue Définition CorrelatesOn
 Le concepteur d’activités **Receive** peut être déplacé de la **boîte à outils** et déposé dans l’aire de [!INCLUDE[wfd2](../includes/wfd2-md.md)], là où les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Receive> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Receive. Sélectionnez le concepteur d’activités **Receive** , puis cliquez sur le bouton de sélection en regard du texte (collection) pour la propriété **CorrelatesOn** dans la grille des propriétés pour afficher la boîte de dialogue **Définition CorrelatesOn** .

## <a name="see-also"></a>Voir aussi
 <xref:System.ServiceModel.Activities.Receive> boîte de dialogue [Ajouter un CorrelationInitializers](../workflow-designer/add-correlationinitializers-dialog-box.md) boîte de dialogue [initialiser la corrélation](../workflow-designer/initialize-correlation-dialog-box.md)