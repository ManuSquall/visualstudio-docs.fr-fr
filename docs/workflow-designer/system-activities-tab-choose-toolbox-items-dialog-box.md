---
title: 'Concepteur de flux de travail : System.Activities, choisir des éléments de boîte à outils'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd25b939519bb1a1cb179ab5bbd4d20b9307f920
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747767"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Onglet System.Activities, boîte de dialogue Choisir des éléments de boîte à outils

Cet onglet de la **Choose Toolbox Items** boîte de dialogue affiche une liste d’activités Windows Workflow Foundation (WF), les modèles et les éléments disponibles pour vous. Pour afficher cette liste, sélectionnez **Choose Toolbox Items** à partir de la **outils** menu ou en double-cliquant sur le **boîte à outils** et en sélectionnant **choisir des éléments de**pour afficher le **Choose Toolbox Items** boîte de dialogue, puis son **System.Activities** onglet. Dès le départ, la liste contient les activités de flux de travail à partir des assemblys System.Activities, System.ServiceModel.Activities et System.Activities.Core.Presentation ; Toutefois, uniquement fourni par le système illustrées des activités et les activités ajoutées via d’autres assemblys affichés dans le **boîte à outils** sont cochées par défaut. Récemment ajouté les activités sont sélectionnées automatiquement et figurent dans le **boîte à outils** lorsque vous cliquez sur **OK** sur la boîte de dialogue. En outre, ces éléments s’affichent dans le **boîte à outils** sous une nouvelle catégorie qui correspond à l’espace de noms dans lequel se trouve l’activité / / modèle d’élément.

> [!WARNING]
> Si vous essayez d'ajouter un assembly qui ne contient pas d'activités de workflow, un boîte de dialogue d'erreur s'affiche pour expliquer que l'assembly ne contient pas d'activités.

Cette boîte de dialogue est indépendant du projet et, par conséquent, le **System.Activities** onglet continue de s’afficher dans autonome XAML ou un type de projet de flux de travail non.

Le filtrage s’effectue sous chaque onglet, et il n’est pas possible d’ajouter des activités de workflow via le **composant .NET** onglet. Les ajouter via le **System.Activities** onglet lui-même.

Vous pouvez désélectionner les éléments que vous ne souhaitez pas voir dans le **boîte à outils** à partir de cette boîte de dialogue tab, ou vous pouvez également, vous pouvez le faire avec le **supprimer** avec le bouton droit d’option de menu dans le **boîte à outils**et supprimant la référence à un assembly ne supprime pas l’élément à partir de la **boîte à outils**.

L’instanciation de l’activité, en la faisant glisser et en la déposant sur le concepteur, ajoute automatiquement l’assembly qui contient l’élément à la liste des assemblys référencés. Par ailleurs, si l'activité fait référence à un assembly C, elle n'ajoute pas C à la liste des assemblys référencés. L’assembly C doit se trouver dans le GAC ou dans le même répertoire que l’activité B. Dans le cas autonome, l’assembly doit se trouver dans le GAC ou dans les chemins d’accès de sonde de Visual Studio. Vous ne pouvez faire glisser et déposer l’activité sur l’aire du concepteur de workflow qu’à ce moment-là.

**Boîte à outils** paramètres sont enregistrés par défaut en tant qu’options de l’utilisateur, afin que la prochaine fois, lorsque vous ouvrez le **boîte à outils**, il affiche votre liste d’activités de flux de travail personnalisée. Un effet secondaire de ce qui est si vous avez ajouté vos éléments de domaine spécifique à la **boîte à outils** via la **Choose Toolbox Items** boîte de dialogue, vous continuer à voir ces éléments lorsque vous travaillez un Application Console de workflow ainsi. Si vous ne souhaitez pas les voir, puis supprimez-les à l’aide du menu contextuel ou désactivez-les via la **Choose Toolbox Items** boîte de dialogue, comme indiqué précédemment.

Les colonnes dans cette boîte de dialogue contiennent les informations suivantes :

Nom\
Répertorie les noms des activités de workflow enregistrées actuellement sur votre ordinateur local.

Namespace\
Affiche la hiérarchie de l’espace de noms .NET qui définit la structure de l’activité.

Assembly Name\
Affiche le nom et la version de l’assembly .NET qui contient l’activité.

Directory.
Affiche l’emplacement de l’assembly .NET qui contient les activités de flux de travail. L'emplacement par défaut de tous les assemblys est le Global Assembly Cache.

Pour trier la liste des composants, cliquez sur un en-tête de colonne.