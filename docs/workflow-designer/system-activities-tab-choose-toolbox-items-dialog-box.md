---
title: 'Concepteur de flux de travail : System. Activities, choisir des éléments de boîte à outils'
description: Découvrez comment l’onglet System. Activities affiche la liste des activités, modèles et éléments de Windows Workflow Foundation (WF) à votre disposition.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d13aadb135f6dcf72d146f74ea2804ef34228641
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433893"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>System. Activities, onglet de la boîte de dialogue choisir des éléments de boîte à outils

Cet onglet de la boîte de dialogue **choisir des éléments de boîte à outils** affiche la liste des activités, modèles et éléments de Windows Workflow Foundation (WF) à votre disposition. Pour afficher cette liste, sélectionnez **choisir des éléments de boîte à outils** dans le menu **Outils** ou cliquez avec le bouton droit sur la boîte **à outils** et sélectionnez **choisir les éléments** pour afficher la boîte de dialogue choisir des **éléments de boîte à outils** , puis sélectionnez son onglet **System. Activities** . La liste est prête à l’emploi et contient les activités de flux de travail des assemblys System. Activities, System. ServiceModel. Activities et System. Activities. Core. Presentation. Toutefois, seules les activités fournies par le système affichées et celles ajoutées par le biais d’autres assemblys affichés dans la **boîte à outils** sont activées par défaut. Les activités ajoutées récemment sont automatiquement vérifiées et s’affichent dans la boîte **à outils** lorsque vous cliquez sur **OK** dans la boîte de dialogue. En outre, ces éléments apparaissent dans la **boîte à outils** sous une nouvelle catégorie qui correspond à l’espace de noms où réside l’activité/l’élément/modèle.

> [!WARNING]
> Si vous essayez d'ajouter un assembly qui ne contient pas d'activités de workflow, un boîte de dialogue d'erreur s'affiche pour expliquer que l'assembly ne contient pas d'activités.

Cette boîte de dialogue est indépendante du projet et, par conséquent, l’onglet **System. Activities** continue à s’afficher en XAML autonome ou en tant que type de projet non Workflow.

Le filtrage est effectué sur chaque onglet et il n’est pas possible d’ajouter des activités de flux de travail via l’onglet **composant .net** . Ajoutez-les par le biais de l’onglet **System. Activities** lui-même.

Vous pouvez désélectionner tous les éléments que vous ne souhaitez pas afficher dans la **boîte à outils** à partir de cet onglet de boîte de dialogue. vous pouvez également le faire à l’aide de l’option de menu **supprimer** avec le bouton droit dans la **boîte à outils** et en déréférençant un assembly ne supprime pas l’élément de la **boîte à outils**.

L’instanciation de l’activité, en la faisant glisser et en la déposant sur le concepteur, ajoute automatiquement l’assembly qui contient l’élément à la liste des assemblys référencés. Par ailleurs, si l'activité fait référence à un assembly C, elle n'ajoute pas C à la liste des assemblys référencés. L’assembly C doit figurer dans le GAC ou dans le même répertoire que l’activité B. Dans le cas autonome, l’assembly doit être dans le GAC ou dans les chemins d’accès de la sonde de VS. Vous ne pouvez faire glisser et déposer l’activité sur l’aire du concepteur de workflow qu’à ce moment-là.

Les paramètres de la **boîte à outils** sont enregistrés par défaut en tant qu’options utilisateur. par conséquent, la prochaine fois que vous ouvrirez la **boîte à outils** , elle affiche votre liste personnalisée d’activités de flux de travail. L’un des effets secondaires de cela est que si vous avez ajouté vos éléments de domaine spécifiques à la boîte **à outils** par le biais de la boîte de dialogue **choisir des éléments de boîte à outils** , vous continuez à voir ces éléments quand vous travaillez dans une application console de Workflow. Si vous ne souhaitez pas les afficher, supprimez-les à l’aide du menu contextuel ou décochez-les dans la boîte de dialogue **choisir des éléments de boîte à outils** comme indiqué précédemment.

Les colonnes dans cette boîte de dialogue contiennent les informations suivantes :

Nom\
Répertorie les noms des activités de workflow enregistrées actuellement sur votre ordinateur local.

Joint
Affiche la hiérarchie de l’espace de noms .NET qui définit la structure de l’activité.

Nom de l’assembly \
Affiche le nom et la version de l’assembly .NET qui contient l’activité.

Directory
Affiche l’emplacement de l’assembly .NET qui contient les activités de flux de travail. L'emplacement par défaut de tous les assemblys est le Global Assembly Cache.

Pour trier la liste des composants, cliquez sur un en-tête de colonne.
