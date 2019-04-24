---
title: À l’aide du Concepteur d’activités hérité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5755c6a3b4ece5b40c7799d83bdf33966d5c2b3e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070782"
---
# <a name="using-the-legacy-activity-designer"></a>Utilisation du concepteur d'activités hérité
Cette rubrique décrit comment utiliser le concepteur d'activités dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le concepteur hérité lorsque vous ciblez le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Le concepteur d'activités vous permet de créer vos propres activités personnalisées.  
  
## <a name="creating-a-custom-activity"></a>Création d'une activité personnalisée  
 Procédez comme suit pour créer une activité personnalisée à l'aide du concepteur d'activités :  
  
1. Sur le **projet** menu, cliquez sur **ajouter une activité**.  
  
2. Sélectionnez le **activité** ou **activité (avec séparation de code)** modèle.  
  
   1. Utilisez le **activité** modèle pour créer une activité avec la définition d’activité et le code utilisateur dans le même fichier de code.  
  
   2. Utilisez le **activité (avec séparation de code)** modèle pour créer une activité avec la définition d’activité exprimée sous la forme de balisage de flux de travail et le code utilisateur dans un fichier de code séparé.  
  
3. Tapez un nom d’activité ou conservez le nom par défaut, puis cliquez sur **ajouter**.  
  
   Vous pouvez également créer un ensemble d’activités personnalisées en créant un nouveau projet de type **Workflow Activity Library**. Pour plus d’informations sur ce type de projet, consultez [Comment : Créer une bibliothèque d’activités de flux de travail (hérité)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).  
  
## <a name="configuring-an-activity"></a>Configuration d'une activité  
 Lorsque le concepteur d'activités est actif, vous pouvez utiliser l'explorateur de propriétés pour configurer les propriétés répertoriées dans le tableau suivant.  
  
|Propriété|Commentaires|  
|--------------|--------------|  
|**Name**|Nom de l'activité.|  
|**Classe de base**|Classe de base dont dérive l'activité. La classe de base par défaut est [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). Dans le **propriétés** fenêtre, cliquez sur le **une classe de Base** ellipses **[...]**  pour sélectionner une autre classe de base dans le [Parcourir et sélectionner une boîte de dialogue de Type .NET (hérité)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Description**|Description de l'activité définie par l'utilisateur.|  
|**Activé**|La valeur **True** par défaut pour permettre l’exécution de l’activité et la validation. La valeur **False** pour désactiver l’exécution de l’activité et la validation. Pour plus d’informations sur l’exécution de l’activité et la validation, consultez [développement d’activités de flux de travail](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## <a name="adding-child-activities"></a>Ajout d'activités enfants  
 Vous pouvez faire glisser des activités enfants de la boîte à outils vers l'activité que vous concevez. Vous pouvez ensuite configurer chaque activité enfant à l'aide de l'explorateur de propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’activités de flux de travail](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Création d’activités personnalisées](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Activités de flux de travail hérité](../workflow-designer/legacy-workflow-activities.md)   
 [Exemples d’activités personnalisées](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Guide pratique pour Créer une bibliothèque d’activités de flux de travail (hérité)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [Utilisation du Concepteur de flux de travail hérité](../workflow-designer/using-the-legacy-workflow-designer.md)