---
title: Vue de modèle de contenu du Concepteur de schémas XML
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 830dbdda0027551a25747235e6ad9dffbbc11b23
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592911"
---
# <a name="content-model-view"></a>Vue de modèle de contenu

La vue de modèle de contenu fournit une représentation graphique des nœuds de schéma locaux et globaux et de leurs composants, notamment les types simples et complexes, les éléments, les groupes de modèles, les attributs et les groupes d'attributs. Il est impossible d'afficher les commentaires et les instructions de traitement XML dans la vue de modèle de contenu. La vue de modèle de contenu contient deux panneaux : un panneau d' **espace de travail** qui contient une liste des nœuds de l' [espace de travail du concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md)et l’aire de conception dans laquelle vous pouvez voir le modèle de contenu des nœuds de schéma qui sont sélectionnés dans le panneau **de l’espace de travail** . La vue de modèle de contenu comprend également la barre d'outils Concepteur de schémas XML et la barre de fil d'Ariane (breadcrumb).

Dans l’image suivante, le volet **espace de travail** contient six nœuds de schéma. Le nœud `purchaseOrder` est sélectionné dans le panneau **de l’espace de travail** et s’affiche dans l’aire de conception.

![Vue de modèle de contenu du Concepteur de schémas XML](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Panneau de l’espace de travail

Une fois que vous avez ajouté des nœuds à l’espace de travail, la liste des nœuds s’affiche dans le panneau de l' **espace de travail** de la vue de modèle de contenu. Lorsque vous sélectionnez des nœuds dans le panneau **de l’espace de travail** , ils s’affichent sur l’aire de conception de la vue de modèle de contenu. Pour supprimer des nœuds de l’espace de travail, utilisez la barre d’outils du concepteur XSD, le menu contextuel du volet **de l’espace de travail** ou la touche **Suppr** .

Pour plus d’informations sur l’ajout de nœuds, consultez la section « Ajout de nœuds à l’espace de travail » dans l' [espace de travail du concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Aire de conception

Lorsqu’un nœud est sélectionné dans le panneau **de l’espace de travail** , il est ajouté à l’aire de conception de la vue de modèle de contenu où vous pouvez afficher les détails du nœud.

Le modèle de contenu d'un nœud est représenté par une arborescence graphique développable avec des éléments et des attributs qui apparaissent sous forme de nœuds d'arbre. Un seul niveau est développé par défaut. D’autres informations, telles que les compositeurs, les noms de type, les groupes et d’autres conteneurs sont placés dans une barre verticale (lorsque ces informations sont développées) le long des éléments et des attributs qu’ils encadrent. Lorsque vous double-cliquez sur une barre verticale, elle devient horizontale et l’arborescence est réduite. Lorsque vous double-cliquez sur une barre horizontale, elle devient verticale et l’arborescence est développée. La sélection de la barre verticale sélectionne tous les nœuds du conteneur. Les expanseurs apparaissent à droite d’un nœud si un élément peut être développé ou réduit.

Si l’aire de conception est vide, l’éditeur XML, l' **Explorateur de schémas XML**et le filigrane sont affichés. Le *filigrane* est une liste de liens vers toutes les vues du concepteur XSD. Si le jeu de schémas comporte des erreurs, le texte suivant est affiché à la fin de la liste : « Utilisez la liste d'erreurs pour afficher et résoudre les erreurs dans le jeu ».

## <a name="breadcrumb-bar"></a>Barre de navigation

La barre de fil d'Ariane (breadcrumb) en bas de la vue de modèle de contenu indique l'emplacement du nœud sélectionné dans le jeu de schémas.

## <a name="context-menus"></a>Menus contextuels

Lorsque vous cliquez avec le bouton droit sur un élément dans l’aire de conception ou dans le panneau **de l’espace de travail** , un menu contextuel s’affiche. Le tableau suivant décrit les options qui sont disponibles pour l'aire de conception de la vue de modèle de contenu.

|Option|Description|
|-|-----------------|
|**Afficher dans l’Explorateur de schémas XML**|Met le focus sur l'Explorateur de schémas et met en surbrillance le nœud de jeu de schémas.|
|**Afficher dans la vue du graphique**|Bascule vers la vue du graphique.|
|**Générer un exemple de code XML**|Disponible uniquement pour les éléments globaux. Génère un exemple de fichier XML pour l'élément global.|
|**Afficher la documentation**|Affiche ou masque le contenu du nœud Annotation/Documentation.|
|**Exporter le diagramme en tant qu’image**|Enregistre l'aire de conception dans un fichier XPS.|
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l’éditeur XML. L’élément sélectionné dans l’Explorateur de **schémas XML** est également sélectionné dans l’éditeur XML.|
|**Propriétés (fenêtre)**|Ouvre la fenêtre **Propriétés** (si elle n’est pas déjà ouverte). Cette fenêtre affiche des informations sur le nœud.|

Le tableau suivant décrit les options disponibles pour le panneau **de l’espace de travail** .

|Option|Description|
|-|-----------------|
|**Afficher dans l’Explorateur de schémas XML**|Met le focus sur l'Explorateur de schémas et met en surbrillance le nœud de jeu de schémas.|
|**Afficher dans la vue du graphique**|Bascule vers la vue du graphique.|
|**Effacer l’espace de travail**|Efface l'espace de travail et l'aire de conception.|
|**Supprimer de l’espace de travail**|Supprime les nœuds sélectionnés de l'espace de travail et de l'aire de conception.|
|**Supprimer tout sauf la sélection dans l’espace de travail**|Supprime les nœuds qui ne sont pas sélectionnés dans l'espace de travail et l'aire de conception.|
|**Générer un exemple de code XML**|Disponible uniquement pour les éléments globaux. Génère un exemple de fichier XML pour l'élément global.|
|**Tout sélectionner**|Sélectionne tous les nœuds dans le panneau **de l’espace de travail** .|
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l’éditeur XML. L’élément sélectionné dans l’Explorateur de **schémas XML** est également sélectionné dans l’éditeur XML.|
|**Propriétés (fenêtre)**|Ouvre la fenêtre **Propriétés** (si elle n’est pas déjà ouverte). Cette fenêtre affiche des informations sur le nœud.|

## <a name="properties-window"></a>Propriétés (fenêtre)

Utilisez le menu contextuel pour ouvrir initialement la fenêtre **Propriétés** . Par défaut, la fenêtre **Propriétés** s’affiche dans le coin inférieur droit de Visual Studio. Lorsque vous cliquez sur un nœud affiché dans la vue de modèle de contenu, les propriétés de ce nœud s’affichent dans la fenêtre **Propriétés** .

## <a name="xsd-designer-toolbar"></a>Barre d’outils du concepteur XSD

Les boutons de la barre d'outils du Concepteur XSD suivants sont activés lorsque la vue de modèle de contenu est active.

![Barre d'outils du Concepteur de schémas XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Option|Description|
|-|-----------------|
|**Afficher la vue de départ**|Bascule vers la [vue de départ](../xml-tools/start-view.md). Cette vue est accessible à l’aide du raccourci clavier : **Ctrl**+**1**.|
|**Afficher la vue de modèle de contenu**|Bascule vers la [vue de modèle de contenu](../xml-tools/content-model-view.md). Cette vue est accessible à l’aide du raccourci clavier : **Ctrl**+**2**.|
|**Afficher la vue du graphique**|Bascule vers la [vue du graphique](../xml-tools/graph-view.md). Cette vue est accessible à l’aide du raccourci clavier : **Ctrl**+**3**.|
|**Effacer l’espace de travail**|Efface l'espace de travail et l'aire de conception.|
|**Supprimer de l’espace de travail**|Supprime les nœuds sélectionnés de l'espace de travail et de l'aire de conception.|
|**Supprimer tout sauf la sélection dans l’espace de travail**|Supprime les nœuds qui ne sont pas sélectionnés dans l'espace de travail et l'aire de conception.|
|**Afficher la documentation**|Affiche ou masque le contenu du nœud Annotation/Documentation.|

## <a name="panscroll"></a>Panoramique/Défilement

Vous pouvez effectuer un panoramique de l’aire de conception à l’aide des barres de défilement ou en maintenant la touche **CTRL** enfoncée tout en cliquant et en faisant glisser la souris. Lorsque vous effectuez un panoramique de l’aire de conception en cliquant et en faisant glisser, le curseur se transforme en quatre flèches qui pointent dans quatre directions.

## <a name="undoredo"></a>Annuler/Rétablir

La fonction d'annulation/de rétablissement est activée dans la vue de modèle de contenu pour les actions suivantes :

- Ajout d'un nœud unique par glisser-déplacer.

- Ajout de plusieurs nœuds de la fenêtre des résultats de recherche dans l'Explorateur de schémas.

- Ajout de nœuds à partir de la vue de départ.

- Suppression d'un ou plusieurs nœuds.

## <a name="zoom"></a>Zoom

Le zoom est disponible dans le coin inférieur droit de la vue de modèle de contenu.

Le zoom peut être contrôlé des façons suivantes :

- En maintenant la touche **CTRL** enfoncée et en tournant la roulette de la souris lorsque la souris pointe sur la surface de la vue de modèle de contenu.

- En utilisant le contrôle Slider. Le curseur affiche le niveau de zoom actuel.

Le curseur de zoom est opaque quand vous le sélectionnez, pointez dessus, ou utilisez **CTRL** avec la molette de la souris pour effectuer un zoom. à tous les autres moments, il est transparent.

## <a name="xml-editor-integration"></a>Intégration de l’éditeur XML

Vous pouvez basculer entre le **Concepteur XSD** et l’éditeur XML en utilisant le menu contextuel.

Si vous apportez des modifications au jeu de schémas dans l’éditeur XML, les modifications sont synchronisées dans la vue de modèle de contenu. Pour plus d’informations, consultez [intégration avec l’éditeur XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Voir aussi

- [Espace de travail du Concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md)
