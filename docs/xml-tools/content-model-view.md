---
title: Vue de modèle de contenu du concepteur de schémas XML
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b858d0b5fb8aab1dabb90ae47d234869412adf2e
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525789"
---
# <a name="content-model-view"></a>Vue de modèle de contenu

La vue de modèle de contenu fournit une représentation graphique des nœuds de schéma locaux et globaux et de leurs composants, notamment les types simples et complexes, les éléments, les groupes de modèles, les attributs et les groupes d'attributs. Il est impossible d'afficher les commentaires et les instructions de traitement XML dans la vue de modèle de contenu. La vue de modèle de contenu contient deux panneaux : un **espace de travail** panneau qui contient une liste des nœuds dans le [espace de travail de Concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md)et l’aire de conception dans laquelle vous pouvez voir le modèle de contenu de schéma les nœuds sont sélectionnés dans le **espace de travail** Panneau de configuration. La vue de modèle de contenu comprend également la barre d'outils Concepteur de schémas XML et la barre de fil d'Ariane (breadcrumb).

Dans l’image suivante, le **espace de travail** panneau contient six nœuds de schéma. Le `purchaseOrder` nœud est sélectionné dans le **espace de travail** panneau et s’affiche dans l’aire de conception.

![Vue de modèle de contenu du concepteur de schémas XML](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Panneau espace de travail

Une fois que vous ajoutez des nœuds à l’espace de travail, la liste de nœuds s’affiche dans le **espace de travail** Panneau de configuration de l’affichage du modèle de contenu. Lorsque vous sélectionnez des nœuds dans le **espace de travail** panneau, ils apparaissent sur l’aire de conception vue de modèle de contenu. Pour supprimer des nœuds à partir de l’espace de travail, utilisez la barre d’outils Concepteur XSD, la **espace de travail** menu de clic droit du panneau, ou le **supprimer** clé.

Pour plus d’informations sur l’ajout de nœuds, consultez la section « Ajout de nœuds à l’espace de travail » dans [espace de travail de Concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Aire de conception

Lorsqu’un nœud est sélectionné dans le **espace de travail** Panneau de configuration, il est ajouté à l’aire de conception vue de modèle de contenu où vous pouvez afficher les détails du nœud.

Le modèle de contenu d'un nœud est représenté par une arborescence graphique développable avec des éléments et des attributs qui apparaissent sous forme de nœuds d'arbre. Un seul niveau est développé par défaut. D'autres informations, telles que les compositeurs, les noms de type, les groupes et d'autres conteneurs sont placés dans une barre verticale (lorsque ces informations sont développées) le long des éléments et des attributs qu'ils encadrent. Lorsque vous double-cliquez sur une barre verticale, elle devient horizontale et l'arborescence est réduite. Lorsque vous double-cliquez sur une barre horizontale, elle devient verticale et l’arborescence est développée. En sélectionnant la barre verticale sélectionne tous les nœuds dans le conteneur. Développeurs apparaissent à droite d’un nœud si un élément peut être développé ou réduit.

Si l’aire de conception est vide, l’éditeur XML, le **Explorateur de schémas XML**, et le filigrane sont affichés. Le *filigrane* est une liste de liens vers toutes les vues du concepteur XSD. Si le jeu de schémas comporte des erreurs, le texte suivant s’affiche à la fin de la liste : « Utiliser la liste d’erreurs pour afficher et corriger les erreurs dans le jeu. »

## <a name="breadcrumb-bar"></a>Barre de navigation

La barre de fil d'Ariane (breadcrumb) en bas de la vue de modèle de contenu indique l'emplacement du nœud sélectionné dans le jeu de schémas.

## <a name="context-menus"></a>Menus contextuels

Lorsque vous cliquez sur un élément sur l’aire de conception ou **espace de travail** panneau, un menu contextuel s’affiche. Le tableau suivant décrit les options qui sont disponibles pour l'aire de conception de la vue de modèle de contenu.

|Option|Description|
|-|-----------------|
|**Afficher dans l’Explorateur de schémas XML**|Met le focus sur l'Explorateur de schémas et met en surbrillance le nœud de jeu de schémas.|
|**Afficher dans la vue du graphique**|Bascule vers la vue du graphique.|
|**Générer un exemple de XML**|Disponible uniquement pour les éléments globaux. Génère un exemple de fichier XML pour l'élément global.|
|**Afficher la Documentation**|Affiche ou masque le contenu du nœud Annotation/Documentation.|
|**Exporter le diagramme en tant qu’Image**|Enregistre l'aire de conception dans un fichier XPS.|
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l’éditeur XML. L’élément est sélectionné dans le **Explorateur de schémas XML** est également sélectionné dans l’éditeur XML.|
|**Propriétés (fenêtre)**|Ouvre le **propriétés** fenêtre (si elle n’est pas déjà ouvert). Cette fenêtre affiche des informations sur le nœud.|

Le tableau suivant décrit les options disponibles pour le **espace de travail** Panneau de configuration.

|Option|Description|
|-|-----------------|
|**Afficher dans l’Explorateur de schémas XML**|Met le focus sur l'Explorateur de schémas et met en surbrillance le nœud de jeu de schémas.|
|**Afficher dans la vue du graphique**|Bascule vers la vue du graphique.|
|**Effacer l’espace de travail**|Efface l'espace de travail et l'aire de conception.|
|**Supprimer à partir de l’espace de travail**|Supprime les nœuds sélectionnés de l'espace de travail et de l'aire de conception.|
|**Supprimer toutes les valeurs sauf la sélection à partir de l’espace de travail**|Supprime les nœuds qui ne sont pas sélectionnés dans l'espace de travail et l'aire de conception.|
|**Générer un exemple de XML**|Disponible uniquement pour les éléments globaux. Génère un exemple de fichier XML pour l'élément global.|
|**Sélectionner tout**|Sélectionne tous les nœuds dans le **espace de travail** Panneau de configuration.|
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l’éditeur XML. L’élément est sélectionné dans le **Explorateur de schémas XML** est également sélectionné dans l’éditeur XML.|
|**Propriétés (fenêtre)**|Ouvre le **propriétés** fenêtre (si elle n’est pas déjà ouvert). Cette fenêtre affiche des informations sur le nœud.|

## <a name="properties-window"></a>Fenêtre Propriétés

Utilisez le menu contextuel (contexte) pour ouvrir la **propriétés** fenêtre. Par défaut, le **propriétés** fenêtre apparaît dans le coin inférieur droit de Visual Studio. Lorsque vous cliquez sur un nœud qui est affiché dans la vue de modèle de contenu, les propriétés de ce nœud sont affichées dans le **propriétés** fenêtre.

## <a name="xsd-designer-toolbar"></a>Barre d’outils Concepteur XSD

Les boutons de la barre d'outils du Concepteur XSD suivants sont activés lorsque la vue de modèle de contenu est active.

![Barre d'outils du concepteur de schémas XML](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Option|Description|
|-|-----------------|
|**Afficher la vue de départ**|Bascule vers le [démarrer l’affichage](../xml-tools/start-view.md). Cette vue est accessible en utilisant le raccourci clavier : **Ctrl**+**1**.|
|**Afficher la vue de modèle de contenu**|Bascule vers le [vue du modèle de contenu](../xml-tools/content-model-view.md). Cette vue est accessible en utilisant le raccourci clavier : **Ctrl**+**2**.|
|**Afficher la vue du graphique**|Bascule vers le [vue graphique](../xml-tools/graph-view.md). Cette vue est accessible en utilisant le raccourci clavier : **Ctrl**+**3**.|
|**Effacer l’espace de travail**|Efface l'espace de travail et l'aire de conception.|
|**Supprimer à partir de l’espace de travail**|Supprime les nœuds sélectionnés de l'espace de travail et de l'aire de conception.|
|**Supprimer toutes les valeurs sauf la sélection à partir de l’espace de travail**|Supprime les nœuds qui ne sont pas sélectionnés dans l'espace de travail et l'aire de conception.|
|**Afficher la Documentation**|Affiche ou masque le contenu du nœud Annotation/Documentation.|

## <a name="panscroll"></a>Panoramique/Défilement

Vous pouvez effectuer un panoramique l’aire de conception en utilisant les barres de défilement ou en maintenant la **Ctrl** enfoncée pendant que vous cliquez et faites glisser la souris. Lorsque vous affichez un panoramique de l’aire de conception à l’aide de clic et glisser, le curseur se transforme en cercle contenant quatre flèches qui pointent dans quatre directions.

## <a name="undoredo"></a>Annuler/Rétablir

La fonction d'annulation/de rétablissement est activée dans la vue de modèle de contenu pour les actions suivantes :

-   Ajout d'un nœud unique par glisser-déplacer.

-   Ajout de plusieurs nœuds de la fenêtre des résultats de recherche dans l'Explorateur de schémas.

-   Ajout de nœuds à partir de la vue de départ.

-   Suppression d'un ou plusieurs nœuds.

## <a name="zoom"></a>Zoom

Le zoom est disponible dans le coin inférieur droit de la vue de modèle de contenu.

Le zoom peut être contrôlé des façons suivantes :

-   En maintenant la **Ctrl** wheel de clé et la rotation de la souris lorsque la souris passe sur la surface de la vue de modèle de contenu.

-   En utilisant le contrôle Slider. Le curseur affiche le niveau de zoom actuel.

Le curseur de Zoom est opaque lorsque vous sélectionnez il, pointez dessus ou utilisez **Ctrl** avec la roulette de la souris pour effectuer un zoom ; toutes les autres fois, il est transparent.

## <a name="xml-editor-integration"></a>Intégration de l’éditeur XML

Vous pouvez basculer entre les **concepteur XSD** et l’éditeur XML à l’aide du menu contextuel (contexte).

Si vous apportez des modifications au schéma défini dans l’éditeur XML, les modifications sont synchronisées dans la vue de modèle de contenu. Pour plus d’informations, consultez [intégration avec l’éditeur XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Voir aussi

- [Espace de travail du Concepteur de schémas XML](../xml-tools/xml-schema-designer-workspace.md)