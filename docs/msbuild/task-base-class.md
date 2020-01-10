---
title: Classe de base des tâches | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 6c3f6238-b9f0-4325-b8b0-de61090bd0a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b3aaef85c53dfacf592251c95772d17b1a6ff96
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566395"
---
# <a name="task-base-class"></a>Classe de base Task
De nombreuses tâches héritent au final de la classe <xref:Microsoft.Build.Utilities.Task>. Cette classe ajoute plusieurs paramètres aux tâches qui en dérivent. Ces paramètres sont répertoriés dans ce document.

## <a name="parameters"></a>Parameters
 Le tableau ci-dessous décrit les paramètres de cette classe de base.

|Paramètre|Description|
|---------------|-----------------|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Paramètre <xref:Microsoft.Build.Framework.IBuildEngine> facultatif.<br /><br /> Spécifie l’interface du moteur de génération disponible pour les tâches. Le moteur de génération définit automatiquement ce paramètre pour permettre aux tâches d'être rappelées.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Paramètre <xref:Microsoft.Build.Framework.IBuildEngine2> facultatif.<br /><br /> Spécifie l’interface du moteur de génération disponible pour les tâches. Le moteur de génération définit automatiquement ce paramètre pour permettre aux tâches d'être rappelées.<br /><br /> Il s'agit d'une propriété de convenance qui permet aux auteurs de tâches qui héritent de cette classe de ne pas avoir à effectuer un cast de la valeur de `IBuildEngine` vers `IBuildEngine2`.|
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Paramètre <xref:Microsoft.Build.Framework.IBuildEngine3> facultatif.<br /><br /> Spécifie l'interface du moteur de génération fournie par l'hôte.|
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Paramètre <xref:Microsoft.Build.Framework.ITaskHost> facultatif.<br /><br /> Spécifie l'instance de l'objet hôte (peut être null). Le moteur de génération définit cette propriété si l'IDE hôte a associé un objet hôte à cette tâche particulière.|
|<xref:Microsoft.Build.Utilities.Task.Log%2A>|Paramètre en lecture seule <xref:Microsoft.Build.Utilities.TaskLoggingHelper> facultatif.<br /><br /> Objet application d’assistance de journalisation...|

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Tâches MSBuild](../msbuild/msbuild-tasks.md)
