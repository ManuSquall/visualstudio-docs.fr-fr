---
title: Utilisation du concepteur d’activités héritées | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a13aeeb3394ee6b8896376c0e7d520b90fb56fa6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302819"
---
# <a name="using-the-legacy-activity-designer"></a>Utilisation du concepteur d'activités hérité
Cette rubrique décrit comment utiliser le concepteur d'activités dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le concepteur hérité lorsque vous ciblez le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Le concepteur d'activités vous permet de créer vos propres activités personnalisées.

## <a name="creating-a-custom-activity"></a>Création d'une activité personnalisée
 Procédez comme suit pour créer une activité personnalisée à l'aide du concepteur d'activités :

1. Dans le menu **Projet**, cliquez sur **Ajouter une activité**.

2. Sélectionnez le modèle **Activité** ou **Activité (avec séparation de code)** .

   1. Utilisez le modèle **Activité** pour créer une activité comportant la définition d'activité et le code utilisateur dans le même fichier de code.

   2. Utilisez le modèle **Activité (avec séparation de code)** pour créer une activité comportant la définition d'activité sous forme de balisage du workflow et le code utilisateur dans un fichier de code séparé.

3. Tapez un nom d'activité ou conservez le nom par défaut, puis cliquez sur **Ajouter**.

   Vous pouvez également créer un ensemble d’activités personnalisées en créant un nouveau projet de type **bibliothèque d’activités de workflow**. Pour plus d’informations sur ce type de projet, consultez [Comment : créer une bibliothèque d’activités de workflow (héritée)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Configuration d'une activité
 Lorsque le concepteur d'activités est actif, vous pouvez utiliser l'explorateur de propriétés pour configurer les propriétés répertoriées dans le tableau suivant.

|Les|Comments|
|--------------|--------------|
|**Nom**|Nom de l'activité.|
|**Classe de base**|Classe de base dont dérive l'activité. La classe de base par défaut est [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). Dans la fenêtre **Propriétés** , cliquez sur les points de suspension de la **classe de base** **[...]** pour sélectionner une autre classe de base dans la [boîte de dialogue Rechercher et sélectionner un type .net (hérité)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Description**|Description de l'activité définie par l'utilisateur.|
|**Activé**|Affectez la valeur **true** par défaut pour activer l’exécution et la validation de l’activité. Affectez la valeur **false** pour désactiver l’exécution et la validation de l’activité. Pour plus d’informations sur l’exécution et la validation d’activités, consultez [développement d’activités de flux de travail](https://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>Ajout d'activités enfants
 Vous pouvez faire glisser des activités enfants de la boîte à outils vers l'activité que vous concevez. Vous pouvez ensuite configurer chaque activité enfant à l'aide de l'explorateur de propriétés.

## <a name="see-also"></a>Voir aussi
 [Développement](https://go.microsoft.com/fwlink?LinkID=65024) d’activités de workflow création d’activités [personnalisées](https://go.microsoft.com/fwlink?LinkID=65021) [activités de workflow héritées](../workflow-designer/legacy-workflow-activities.md) activités [personnalisées exemples](https://go.microsoft.com/fwlink?LinkID=65022) [Comment : créer une bibliothèque d’activités de workflow (héritée)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [à l’aide de la concepteur de flux de travail héritée](../workflow-designer/using-the-legacy-workflow-designer.md)