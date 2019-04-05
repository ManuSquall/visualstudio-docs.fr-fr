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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fd03e1a8615e75d3f00f79eb10b7a7ff97f0eb33
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001636"
---
# <a name="correlateson-definition-dialog-box"></a>Boîte de dialogue Définition CorrelatesOn
Le **CorrelatesOn** boîte de dialogue est utilisée dans [!INCLUDE[wfd1](../includes/wfd1-md.md)] pour modifier la <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> propriété d’un <xref:System.ServiceModel.Activities.Receive> activité. [!INCLUDE[crdefault](../includes/crdefault-md.md)] le [réception](../workflow-designer/receive-activity-designer.md) rubrique.  
  
 La corrélation entre les activités <xref:System.ServiceModel.Activities.Receive> spécifie la manière dont différentes opérations de service se connectent les unes aux autres dans un workflow.  
  
 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **CorrelatesOn** boîte de dialogue.  
  
|Élément d'interface utilisateur|Description|  
|----------------|-----------------|  
|**CorrelatesWith**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> utilisé pour router le message vers l'instance de workflow appropriée.|  
|**Requêtes XPath**|Paire clé/valeur qui contient les requêtes utilisées pour extraire les données de corrélation des messages entrants. Cette valeur correspond à la propriété <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>. Les requêtes XPath sont contenues dans un objet <xref:System.ServiceModel.MessageQuerySet>.|  
  
## <a name="to-launch-the-correlateson-dialog-box"></a>Pour lancer la boîte de dialogue Définition CorrelatesOn  
 Le **réception** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../includes/wfd2-md.md)] surface, là où les activités sont généralement placées. Cette opération crée une activité <xref:System.ServiceModel.Activities.Receive> avec une propriété <xref:System.Activities.Activity.DisplayName%2A> affectée de la valeur par défaut Receive. Sélectionnez le **réception** Concepteur d’activités et cliquez sur le bouton de sélection en regard du texte (Collection) pour le **CorrelatesOn** propriété dans la grille des propriétés pour le **définition CorrelatesOn**  la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Activities.Receive>   
 [Ajouter la boîte de dialogue d’initialiseurs de corrélation](../workflow-designer/add-correlationinitializers-dialog-box.md)   
 [Initialiser la corrélation, boîte de dialogue](../workflow-designer/initialize-correlation-dialog-box.md)