---
title: TaskExtension, classe de base | Microsoft Docs
description: En savoir plus sur les paramètres que la classe de base Microsoft. Build. Tasks. TaskExtension ajoute aux tâches qui en héritent.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tool task base class
- tool task base class [MSBuild]
ms.assetid: 08bb8059-b7e2-4565-89ba-d9034d4f0e16
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6692cb16b3861d72bf713c22b2ecfb2ee95bc036
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965978"
---
# <a name="taskextension-base-class"></a>Classe de base TaskExtension

De nombreuses tâches héritent de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, laquelle hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Cette chaîne d'héritage ajoute plusieurs paramètres aux tâches qui en dérivent. Ces paramètres sont répertoriés dans ce document.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres des classes de base.

|Paramètre|Description|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Paramètre <xref:Microsoft.Build.Framework.IBuildEngine> facultatif.<br /><br /> Spécifie l’interface du moteur de génération disponible pour les tâches. Le moteur de génération définit automatiquement ce paramètre pour permettre aux tâches d'être rappelées.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Paramètre <xref:Microsoft.Build.Framework.IBuildEngine2> facultatif.<br /><br /> Spécifie l’interface du moteur de génération disponible pour les tâches. Le moteur de génération définit automatiquement ce paramètre pour permettre aux tâches d'être rappelées.<br /><br /> Il s'agit d'une propriété de convenance qui permet aux auteurs de tâches qui héritent de cette classe de ne pas avoir à effectuer un cast de la valeur de `IBuildEngine` vers `IBuildEngine2`.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Paramètre <xref:Microsoft.Build.Framework.IBuildEngine3> facultatif.<br /><br /> Spécifie l'interface du moteur de génération fournie par l'hôte.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Paramètre <xref:Microsoft.Build.Framework.ITaskHost> facultatif.<br /><br /> Spécifie l'instance de l'objet hôte (peut être null). Le moteur de génération définit cette propriété si l'IDE hôte a associé un objet hôte à cette tâche particulière.|
|<xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>|Paramètre en lecture seule <xref:Microsoft.Build.Utilities.TaskLoggingHelper> facultatif.<br /><br /> Obtient un objet `TaskLoggingHelperExtension` qui contient des méthodes de journalisation des tâches.|

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Tâches](../msbuild/msbuild-tasks.md)
