---
title: 'Concepteur de flux de travail : raccourcis clavier'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8892f46585179ae5857d48deffd982e1cfc0dee
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115384"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Raccourcis clavier dans Workflow Designer

Toutes les fonctionnalités principales du Concepteur de flux de travail sont accessibles par le biais du clavier.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Navigation dans Workflow Designer à l'aide du clavier

Dans Visual Studio, les raccourcis globaux et les raccourcis de débogage s’appliquent au Concepteur de flux de travail. En outre, un certain nombre de Concepteur de flux de travail raccourcis clavier spécifiques ont été créés. Dans Visual Studio, tous les raccourcis clavier peuvent être remappés. Toutefois, dans une application réhébergée, ces raccourcis clavier sont encodés de manière irréversible.

### <a name="workflow-designer-keyboard-shortcuts"></a>Raccourcis clavier de Workflow Designer

Le tableau suivant récapitule les raccourcis clavier par défaut affectés aux commandes Concepteur de flux de travail.

|Raccourci|Fonction|
|-|-------------|
|CTRL+E, A|Affiche ou masque le concepteur d’arguments.|
|CTRL+E, C|Réduit l'activité sélectionnée sur place.|
|CTRL+E, E|Développe l’activité sélectionnée sur place.|
|CTRL+E, F|Connecte les activités sélectionnées dans un organigramme.|
|CTRL+E, I|Affiche ou masque le concepteur d'importations.|
|CTRL+E, M|Déplace le focus clavier vers l'élément suivant dans l'ordre de tabulation.|
|CTRL+E, N|Crée une variable dans la portée de l'activité sélectionnée (ou la plus proche).|
|CTRL+E, O|Affiche ou masque la vue d'ensemble.|
|CTRL+E, P|Accède au parent de l'activité sélectionnée. Cette commande permet de monter d'un niveau dans l'exploration à l'aide de la barre de navigation et et de modifier l'activité racine dans l'aire du concepteur.|
|CTRL+E, S|Ajoute l'élément avec le focus clavier à la sélection actuelle.|
|CTRL+E, V|Affiche ou masque le concepteur de variables.|
|CTRL+E, X|Développe toutes les activités dans le flux de travail.|
|CTRL+ALT+F6|Déplace le focus clavier de la zone actuelle de l'interface utilisateur vers la zone suivante dans la séquence. L'ordre suivi est le suivant :<br /><br /> 1. barre de navigation de navigation.<br />2. surface du concepteur<br />3. arguments/variables/concepteur d’importations s’il est ouvert<br />4. Shell|

### <a name="flowchart"></a>Organigramme

La liste suivante affiche les mouvements utilisés pour construire un organigramme à l'aide du clavier. Comme dans le reste du Concepteur de flux de travail, les activités sont ajoutées à l’aire du concepteur à l’aide des raccourcis de boîte à outils globaux fournis avec Visual Studio.

- Pour déplacer une activité, sélectionnez-la et utilisez les touches de direction pour la repositionner.

- Pour redimensionner un organigramme, déplacez une activité au-delà de la bordure actuelle de l'organigramme à l'aide des touches de direction. L'organigramme est redimensionné automatiquement.

- Pour définir une activité comme nœud de départ, utilisez la commande **définir en tant que StartNode** dans le menu contextuel.

- Pour connecter des activités :

    1. Sélectionnez l'activité source en y accédant par tabulation.

    2. Appuyez sur CTRL+E, M autant de fois que nécessaire pour déplacer le focus clavier sur l'activité de destination.

    3. Appuyez sur CTRL+E, S pour ajouter l'activité de destination à la sélection.

    4. Appuyez sur CTRL+E, F pour ajouter le connecteur de la source à la destination.

Remarques à propos de la connexion des activités à l'aide du clavier :

- Vous pouvez établir plusieurs connexions en même temps en ajoutant des activités à la sélection avant d'appuyer sur CTRL+E, F. Les connexions sont créées dans l'ordre dans lequel les activités ont été ajoutées à la sélection.

- Si une paire d'activités ne peut pas être connectée, par exemple si l'activité source possède déjà une connexion sortante, d'autres connexions entre les activités de la sélection sont établies dans la mesure du possible.

- Lorsqu’un **FlowDecision** est inclus dans la sélection et que le **FlowDecision** n’a pas de connecteurs sortants, le connecteur est placé sur la **vraie** branche.

### <a name="expression-editing"></a>Édition d'expressions

Par défaut, les raccourcis clavier par défaut pour la modification de texte Visual Basic s’appliquent dans l’éditeur d’expressions dans Concepteur de flux de travail, avec les limitations suivantes :

- Le remappage des raccourcis clavier correspondant aux commandes suivantes n'a aucun effet. Vous pouvez utiliser uniquement les raccourcis clavier par défaut pour accéder aux commandes suivantes lors de la modification d'une expression.

  - Couper
  - Copier
  - Coller
  - Sélectionner tout
  - Annuler
  - Rétablir

- Pour remapper les raccourcis clavier des commandes d’édition d’expressions dans Concepteur de flux de travail dans Visual Studio, modifiez les raccourcis dans l’étendue Concepteur de flux de travail. Les modifications apportées à la portée de l’éditeur de texte ne s’appliquent pas automatiquement à Concepteur de flux de travail. Si vous souhaitez remapper des raccourcis dans ces deux éléments, vous devez appliquer les modifications deux fois (une fois pour chaque interface).
