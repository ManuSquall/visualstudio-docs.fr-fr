---
title: Vue de modèle de contenu du concepteur de schémas XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d7f04c482149cbc063a3788dd6be44c643bae6a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751791"
---
# <a name="content-model-view"></a>Vue de modèle de contenu

La vue de modèle de contenu fournit une représentation graphique des nœuds de schéma locaux et globaux et de leurs composants, notamment les types simples et complexes, les éléments, les groupes de modèles, les attributs et les groupes d'attributs. Il est impossible d'afficher les commentaires et les instructions de traitement XML dans la vue de modèle de contenu. La vue de modèle de contenu contient deux volets : un **espace de travail** Panneau de configuration qui contient une liste des nœuds dans le [espace de travail de Concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md)et l’aire de conception dans laquelle vous pouvez voir le modèle de contenu de schéma les nœuds sélectionnés dans le **espace de travail** Panneau de configuration. La vue de modèle de contenu comprend également la barre d'outils Concepteur de schémas XML et la barre de fil d'Ariane (breadcrumb).

 Dans l’image suivante, le **espace de travail** panneau contient six nœuds de schéma. Le `purchaseOrder` nœud est sélectionné dans le **espace de travail** panneau et est affiché dans l’aire de conception.

 ![Vue de modèle de contenu du concepteur de schémas XML](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Panneau espace de travail

 Après avoir ajouté des nœuds à l’espace de travail, la liste des nœuds s’affiche dans le **espace de travail** Panneau de configuration de l’affichage du modèle de contenu. Lorsque vous sélectionnez des nœuds dans le **espace de travail** panneau, ils apparaissent sur l’aire de conception vue de modèle de contenu. Pour supprimer des nœuds à partir de l’espace de travail, utilisez la barre d’outils Concepteur XSD, les **espace de travail** menu contextuel du Panneau de configuration, ou le **supprimer** clé.

 Pour plus d’informations sur l’ajout de nœuds, consultez la section « Ajout de nœuds à l’espace de travail » dans [espace de travail de Concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Aire de conception

 Lorsqu’un nœud est sélectionné dans le **espace de travail** Panneau de configuration, il est ajouté à l’aire de conception vue de modèle de contenu où vous pouvez afficher les détails du nœud.

 Le modèle de contenu d’un nœud est représenté par une arborescence graphique développable avec des éléments et des attributs qui apparaissent sous forme de nœuds d’arbre. Un seul niveau est développé par défaut. D'autres informations, telles que les compositeurs, les noms de type, les groupes et d'autres conteneurs sont placés dans une barre verticale (lorsque ces informations sont développées) le long des éléments et des attributs qu'ils encadrent. Lorsque vous double-cliquez sur une barre verticale, elle devient horizontale et l'arborescence est réduite. Lorsque vous double-cliquez sur une barre horizontale, elle devient verticale et l’arborescence est développée. Sélection de la barre verticale de sélectionne tous les nœuds dans le conteneur. Les EXPANSEURS apparaissent à droite d’un nœud si un élément peut être développé ou réduit.

 Si l’aire de conception est vide, l’éditeur XML, le **Explorateur de schémas XML**, et le filigrane sont affichés. Le *filigrane* est une liste de liens vers toutes les vues du concepteur XSD. Si le jeu de schémas comporte des erreurs, le texte suivant est affiché à la fin de la liste : « Utilisez la liste d'erreurs pour afficher et résoudre les erreurs dans le jeu ».

## <a name="breadcrumb-bar"></a>Barre de navigation

 La barre de fil d'Ariane (breadcrumb) en bas de la vue de modèle de contenu indique l'emplacement du nœud sélectionné dans le jeu de schémas.

## <a name="context-menus"></a>Menus contextuels

 Lorsque vous cliquez sur un élément sur l’aire de conception ou **espace de travail** panneau, un menu contextuel s’affiche. Le tableau suivant décrit les options qui sont disponibles pour l'aire de conception de la vue de modèle de contenu.

|Option|Description|
|------------|-----------------|
|**Afficher dans l’Explorateur de schémas XML**|Met le focus sur l'Explorateur de schémas et met en surbrillance le nœud de jeu de schémas.|
|**Afficher dans la vue du graphique**|Bascule vers la vue du graphique.|
|**Générer un exemple XML**|Disponible uniquement pour les éléments globaux. Génère un exemple de fichier XML pour l'élément global.|
|**Afficher la Documentation**|Affiche ou masque le contenu du nœud Annotation/Documentation.|
|**Exporter le diagramme en tant qu’Image**|Enregistre l’aire de conception dans un fichier XPS.|
|**Afficher le Code**|Ouvre le fichier qui contient le nœud sélectionné dans l'Éditeur XML. L’élément est sélectionné dans le **Explorateur de schémas XML** est également sélectionné dans l’éditeur XML.|
|**Propriétés (fenêtre)**|Ouvre le **propriétés** fenêtre (s’il n’est pas déjà). Cette fenêtre affiche des informations sur le nœud.|

 Le tableau suivant décrit les options disponibles pour le **espace de travail** Panneau de configuration.

|Option|Description|
|------------|-----------------|
|**Afficher dans l’Explorateur de schémas XML**|Met le focus sur l'Explorateur de schémas et met en surbrillance le nœud de jeu de schémas.|
|**Afficher dans la vue du graphique**|Bascule vers la vue du graphique.|
|**Désactivez l’espace de travail**|Efface l'espace de travail et l'aire de conception.|
|**Supprimer à partir de l’espace de travail**|Supprime les nœuds sélectionnés de l'espace de travail et de l'aire de conception.|
|**Supprimer tout sauf la sélection à partir de l’espace de travail**|Supprime les nœuds qui ne sont pas sélectionnés dans l'espace de travail et l'aire de conception.|
|**Générer un exemple XML**|Disponible uniquement pour les éléments globaux. Génère un exemple de fichier XML pour l'élément global.|
|**Sélectionner tout**|Sélectionne tous les nœuds dans le **espace de travail** Panneau de configuration.|
|**Afficher le Code**|Ouvre le fichier qui contient le nœud sélectionné dans l'Éditeur XML. L’élément est sélectionné dans le **Explorateur de schémas XML** est également sélectionné dans l’éditeur XML.|
|**Propriétés (fenêtre)**|Ouvre le **propriétés** fenêtre (s’il n’est pas déjà). Cette fenêtre affiche des informations sur le nœud.|

## <a name="properties-window"></a>Fenêtre Propriétés

 Utilisez le menu contextuel pour ouvrir la **propriétés** fenêtre. Par défaut, le **propriétés** fenêtre s’affiche dans le coin inférieur droit de Visual Studio. Lorsque vous cliquez sur un nœud qui est restitué dans la vue de modèle de contenu, les propriétés de ce nœud sont affichées dans le **propriétés** fenêtre.

## <a name="xsd-designer-toolbar"></a>Barre d’outils du concepteur XSD

 Les boutons de la barre d'outils du Concepteur XSD suivants sont activés lorsque la vue de modèle de contenu est active.

 ![Barre d'outils du concepteur de schémas XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Option|Description|
|------------|-----------------|
|**Afficher le mode de démarrage**|Bascule vers le [démarrer l’affichage](../xml-tools/start-view.md). Cette vue est accessible à l’aide du raccourci clavier : **Ctrl**+**1**.|
|**Afficher la vue du modèle de contenu**|Bascule vers le [vue du modèle de contenu](../xml-tools/content-model-view.md). Cette vue est accessible à l’aide du raccourci clavier : **Ctrl**+**2**.|
|**Afficher la vue du graphique**|Bascule vers le [vue graphique](../xml-tools/graph-view.md). Cette vue est accessible à l’aide du raccourci clavier : **Ctrl**+**3**.|
|**Désactivez l’espace de travail**|Efface l'espace de travail et l'aire de conception.|
|**Supprimer à partir de l’espace de travail**|Supprime les nœuds sélectionnés de l'espace de travail et de l'aire de conception.|
|**Supprimer tout sauf la sélection à partir de l’espace de travail**|Supprime les nœuds qui ne sont pas sélectionnés dans l'espace de travail et l'aire de conception.|
|**Afficher la Documentation**|Affiche ou masque le contenu du nœud Annotation/Documentation.|

## <a name="panscroll"></a>Panoramique/Défilement

 Vous pouvez effectuer un panoramique sur l’aire de conception en utilisant les barres de défilement ou en maintenant la **Ctrl** enfoncée tout en vous cliquez et faites glisser la souris. Lorsque vous effectuer un panoramique de l’aire de conception à l’aide de cliquez et faites glisser, le curseur change pour quatre flèches qui pointent dans quatre directions.

## <a name="undoredo"></a>Annuler/Rétablir

 La fonction d'annulation/de rétablissement est activée dans la vue de modèle de contenu pour les actions suivantes :

-   Ajout d'un nœud unique par glisser-déplacer.

-   Ajout de plusieurs nœuds de la fenêtre des résultats de recherche dans l'Explorateur de schémas.

-   Ajout de nœuds à partir de la vue de départ.

-   Suppression d'un ou plusieurs nœuds.

## <a name="zoom"></a>Zoom

 Zoom est disponible dans le coin inférieur droit de la vue de modèle de contenu.

 Le zoom peut être contrôlé des façons suivantes :

-   En maintenant la **Ctrl** roue de clé et en tournant la souris lorsque la souris pointe sur la surface de la vue de modèle de contenu.

-   En utilisant le contrôle Slider. Le curseur affiche le niveau de zoom actuel.

Le curseur de Zoom est opaque lorsque vous sélectionnez, pointez sur celui-ci ou utilisez **Ctrl** avec la roulette de la souris pour effectuer un zoom ; tous les autres moments, il est transparent.

## <a name="xml-editor-integration"></a>Intégration de l’éditeur XML

 Vous pouvez basculer entre les **concepteur XSD** et l’éditeur XML en utilisant le menu contextuel.

 Si vous apportez des modifications au schéma défini dans l’éditeur XML, les modifications sont synchronisées dans la vue de modèle de contenu. Pour plus d’informations, consultez [intégration avec l’éditeur XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Voir aussi

- [Espace de travail du Concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md)