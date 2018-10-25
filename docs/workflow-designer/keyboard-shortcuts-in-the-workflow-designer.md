---
title: Concepteur de flux de travail - raccourcis clavier dans le Concepteur de flux de travail
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDKeyboardShortcuts.UI
ms.assetid: 9be75438-a4a3-4781-94e5-45b7ec082358
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e4040a5b370674e7794b09e4d1cae68f424c7792
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887369"
---
# <a name="keyboard-shortcuts-in-the-workflow-designer"></a>Raccourcis clavier dans Workflow Designer

Toutes les fonctionnalités de base du Concepteur de flux de travail sont accessibles par le clavier.

## <a name="navigating-the-workflow-designer-using-the-keyboard"></a>Navigation dans Workflow Designer à l'aide du clavier

À l’intérieur de Visual Studio, les raccourcis globaux et les raccourcis de débogage s’appliquent au Concepteur de Workflow. En outre, un nombre de raccourcis de clavier spécifiques au Concepteur de flux de travail créé. Dans Visual Studio, tous les raccourcis clavier peuvent être remappés. Toutefois, dans une application réhébergée, ces raccourcis clavier sont encodés de manière irréversible.

### <a name="workflow-designer-keyboard-shortcuts"></a>Raccourcis clavier de Workflow Designer

Le tableau suivant récapitule les raccourcis clavier par défaut affectés aux commandes du Concepteur de Workflow.

|Raccourci|Objectif|
|-|-------------|
|CTRL+E, A|Affiche ou masque le concepteur d'arguments.|
|CTRL+E, C|Réduit l'activité sélectionnée sur place.|
|CTRL+E, E|Développe l'activité sélectionnée sur place.|
|CTRL+E, F|Connecte les activités sélectionnées dans un organigramme.|
|CTRL+E, I|Affiche ou masque le concepteur d'importations.|
|CTRL+E, M|Déplace le focus clavier vers l'élément suivant dans l'ordre de tabulation.|
|CTRL+E, N|Crée une variable dans la portée de l'activité sélectionnée (ou la plus proche).|
|CTRL+E, O|Affiche ou masque la vue d'ensemble.|
|CTRL+E, P|Accède au parent de l'activité sélectionnée. Cette commande permet de monter d'un niveau dans l'exploration à l'aide de la barre de navigation et et de modifier l'activité racine dans l'aire du concepteur.|
|CTRL+E, S|Ajoute l'élément avec le focus clavier à la sélection actuelle.|
|CTRL+E, V|Affiche ou masque le concepteur de variables.|
|CTRL+E, X|Développe toutes les activités dans le flux de travail.|
|CTRL+ALT+F6|Déplace le focus clavier de la zone actuelle de l'interface utilisateur vers la zone suivante dans la séquence. L'ordre suivi est le suivant :<br /><br /> 1.  Barre d'exploration à l'aide de la barre de navigation<br />2.  Aire du concepteur<br />3.  Concepteur d’arguments/de variables/d’importations, s’il est ouvert<br />4.  Shell|

### <a name="flowchart"></a>Organigramme

La liste suivante affiche les mouvements utilisés pour construire un organigramme à l'aide du clavier. Comme dans le reste du Workflow Designer, les activités sont ajoutées à l’aire du concepteur en utilisant les raccourcis de boîte à outils globaux fournis avec Visual Studio.

- Pour déplacer une activité, sélectionnez-la et utilisez les touches de direction pour la repositionner.

- Pour redimensionner un organigramme, déplacez une activité au-delà de la bordure actuelle de l'organigramme à l'aide des touches de direction. L'organigramme est redimensionné automatiquement.

- Pour définir une activité en tant que le nœud de départ, utilisez le **définir en tant que StartNode** commande dans le menu contextuel.

- Pour connecter des activités :

    1.  Sélectionnez l'activité source en y accédant par tabulation.

    2.  Appuyez sur CTRL+E, M autant de fois que nécessaire pour déplacer le focus clavier sur l'activité de destination.

    3.  Appuyez sur CTRL+E, S pour ajouter l'activité de destination à la sélection.

    4.  Appuyez sur CTRL+E, F pour ajouter le connecteur de la source à la destination.

Remarques à propos de la connexion des activités à l'aide du clavier :

- Vous pouvez établir plusieurs connexions en même temps en ajoutant des activités à la sélection avant d'appuyer sur CTRL+E, F. Les connexions sont créées dans l'ordre dans lequel les activités ont été ajoutées à la sélection.

- Si une paire d'activités ne peut pas être connectée, par exemple si l'activité source possède déjà une connexion sortante, d'autres connexions entre les activités de la sélection sont établies dans la mesure du possible.

- Quand un **FlowDecision** est inclus dans la sélection et la **FlowDecision** ne possède aucun lien sortant, le connecteur est placé sur le **True** branche.

### <a name="expression-editing"></a>Édition d'expressions

Par défaut, les raccourcis clavier par défaut pour la modification de texte Visual Basic s’appliquent à l’intérieur de l’éditeur d’expressions dans le Concepteur de flux de travail, avec les limitations suivantes :

- Le remappage des raccourcis clavier correspondant aux commandes suivantes n'a aucun effet. Vous pouvez utiliser uniquement les raccourcis clavier par défaut pour accéder aux commandes suivantes lors de la modification d'une expression.

   - Couper
   - Copier
   - Coller
   - Sélectionner tout
   - Annuler
   - Rétablir

- Pour remapper les raccourcis clavier pour les commandes de modification d’expression à l’intérieur du Concepteur de flux de travail dans Visual Studio, modifier les raccourcis figurant dans la portée du Concepteur de Workflow. Modifications apportées dans la portée de l’éditeur de texte ne s’appliquent pas automatiquement au Concepteur de flux de travail. Si vous souhaitez remapper des raccourcis dans ces deux éléments, vous devez appliquer les modifications deux fois (une fois pour chaque interface).