---
title: Onglet System.Activities de la boîte à outils éléments choisir | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2da5aafcc684c9af71aebc094d817c64f579d0ea
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Onglet System.Activities de la boîte de dialogue Choisir des éléments de boîte à outils
Cet onglet de la **choisir des éléments de boîte à outils** boîte de dialogue affiche une liste de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] activités, des modèles et des éléments à votre disposition. Pour afficher la liste, sélectionnez **choisir des éléments de boîte à outils** à partir de la **outils** menu ou en cliquant sur le **boîte à outils** et en sélectionnant **choisir des éléments de**pour afficher les **choisir des éléments de boîte à outils** boîte de dialogue, puis sélectionnez ses **System.Activities** onglet. L’emploi, la liste contient les activités de flux de travail à partir des assemblys System.Activities, System.ServiceModel.Activities et System.Activities.Core.Presentation ; Toutefois, seuls fournie par le système indiquées les activités et les activités ajoutées via d’autres assemblys affichés dans le **boîte à outils** sont cochées par défaut. Récemment ajouté les activités sont sélectionnées automatiquement et s’affichent dans le **boîte à outils** lorsque vous cliquez sur **OK** sur la boîte de dialogue. En outre, ces éléments s’affichent dans le **boîte à outils** sous une nouvelle catégorie qui correspond à l’espace de noms où se trouve l’activité / / modèle d’élément.

> [!WARNING]
> Si vous essayez d'ajouter un assembly qui ne contient pas d'activités de workflow, un boîte de dialogue d'erreur s'affiche pour expliquer que l'assembly ne contient pas d'activités.

 Cette boîte de dialogue est indépendant de projet et par conséquent, le **System.Activities** onglet continue de s’afficher dans XAML autonome ou un type de projet de flux de travail non.

 Le filtrage s'effectue sous chaque onglet. Cela signifie qu’il n’est pas possible d’ajouter des activités de workflow via le **composant .NET** onglet. Ils doivent être ajoutés via le **System.Activities** onglet lui-même.

 Vous pouvez désactiver tous les éléments que vous ne souhaitez pas voir dans le **boîte à outils** cette boîte de dialogue tab, ou vous pouvez également vous pouvez d’effectuer à l’aide de la **supprimer** option de menu contextuel dans le **boîte à outils** et Annuler faisant référence à un assembly ne supprime pas l’élément à partir de la **boîte à outils**.

 L’instanciation de l’activité, en la faisant glisser et en la déposant sur le concepteur, ajoute automatiquement l’assembly qui contient l’élément à la liste des assemblys référencés. Par ailleurs, si l'activité fait référence à un assembly C, elle n'ajoute pas C à la liste des assemblys référencés. L’assembly C doit se trouver dans le GAC ou dans le même répertoire que l’activité B. Dans le cas autonome, l’assembly doit se trouver dans le GAC ou les chemins d’accès de sonde de Visual Studio. Vous ne pouvez faire glisser et déposer l’activité sur l’aire du concepteur de workflow qu’à ce moment-là.

 **Boîte à outils** par défaut, les paramètres sont enregistrés en tant qu’options de l’utilisateur, afin que la prochaine fois, lorsque vous ouvrez le **boîte à outils**, il affiche votre liste personnalisée d’activités de flux de travail. Un effet secondaire de ce qui est si vous avez ajouté vos éléments de domaine spécifique à la **boîte à outils** via la **choisir des éléments de boîte à outils** boîte de dialogue, vous cependant continuez de voir ces éléments lorsque vous travaillez un Application Console de workflow ainsi. Si vous ne souhaitez pas les voir, puis supprimez-les à l’aide du menu contextuel ou désactivez-les via la **choisir des éléments de boîte à outils** boîte de dialogue, comme indiqué précédemment.

 Les colonnes dans cette boîte de dialogue contiennent les informations suivantes :

 Nom répertorie les noms des activités de flux de travail est actuellement enregistré sur votre ordinateur local.

 Namespace affiche la hiérarchie de l’espace de noms de bibliothèque de classes .NET Framework qui définit la structure de l’activité.

 Nom d’assembly affiche le nom et la version de l’assembly .NET Framework qui contient l’activité.

 Répertoire affiche l’emplacement de l’assembly .NET Framework qui contient les activités de flux de travail. L'emplacement par défaut de tous les assemblys est le Global Assembly Cache.

 Pour trier la liste des composants, cliquez sur un en-tête de colonne.