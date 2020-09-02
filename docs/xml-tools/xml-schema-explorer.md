---
title: Explorateur de schémas XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04c6415fed131abc5a102f6ec15c69e33f21fd68
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592345"
---
# <a name="xml-schema-explorer"></a>Explorateur de schémas XML

L' **Explorateur de schémas XML** est intégré à Microsoft Visual Studio et à l’éditeur XML pour vous permettre d’utiliser des schémas en langage XSD (XML Schema Definition). Lorsque vous ouvrez un fichier de schéma XML, le nœud **jeu de schémas** s’affiche dans l' **Explorateur de schémas XML**. Tous les schémas inclus, importés ou redéfinis pour votre fichier cible, ainsi que tous les fichiers référencés via une `include` `import` instruction ou, apparaissent également dans l’Explorateur de **schémas XML**.

L' **Explorateur de schémas XML** vous permet d’effectuer les opérations suivantes :

- obtenir une vue d'ensemble rapide du jeu de schémas ;

- Parcourir et naviguer l’arborescence.

- Effectuer des recherches par mot clé et spécifiques au schéma. Pour plus d’informations, consultez [recherche dans le jeu de schémas](../xml-tools/searching-the-schema-set.md).

- Ajouter les résultats de la recherche à la vue du graphique ou de la vue de modèle de contenu

- trier l’arborescence par ordre des documents, par type ou par nom ; Pour plus d’informations, consultez [Tri, filtrage et regroupement](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- Ouvrez l’éditeur XML et accédez à emplacements de code dans le fichier XSD. Pour plus d’informations, consultez [intégration avec l’éditeur XML](../xml-tools/integration-with-xml-editor.md).

- générer un exemple de code XML pour les éléments globaux.

L' **Explorateur de schémas XML** fournit une vue hiérarchique du jeu de schémas via une arborescence. L' **Explorateur de schémas XML** fournit également des opérations de recherche, de filtrage, de navigation et de tri. Pour accéder à l' **Explorateur de schémas XML**, effectuez l’une des opérations suivantes :

- Si vous êtes dans la [vue de départ](../xml-tools/start-view.md), cliquez sur le lien **Explorateur de schémas XML** .

- Si vous êtes dans la [vue du graphique](../xml-tools/graph-view.md) ou la [vue de modèle de contenu](../xml-tools/content-model-view.md) et que vous avez des nœuds dans votre espace de travail, utilisez le menu contextuel (clic droit) pour sélectionner l’Explorateur de **schémas XML**.

- Vous pouvez également sélectionner l' **Explorateur de schémas XML** dans le menu **affichage** .

- Vous pouvez accéder à l' **Explorateur de schémas XML** à partir d’un fichier *. vb* qui a un littéral XML Visual Basic associé à un fichier *. xsd* . Pour afficher le jeu de schémas dans l' **Explorateur de schémas XML**, cliquez avec le bouton droit sur un nœud XML dans un littéral XML ou une importation d’espace de noms XML, puis sélectionnez la commande **afficher dans l’Explorateur de schémas** . Pour plus d’informations, consultez [intégration de littéraux XML avec l’Explorateur de schémas XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Arborescence
L' **Explorateur de schémas XML** affiche des informations sur le jeu de schémas précompilés dans une arborescence. L'arborescence est organisée comme suit :

- Au niveau supérieur se trouve le nœud de jeu de schémas.

- Le deuxième niveau contient les espaces de noms.

- Le troisième niveau contient les fichiers.

- Le quatrième niveau contient les nœuds globaux. Ceci peut inclure les éléments, les groupes, les types complexes, les types simples, les attributs, les groupes d'attributs, et les instructions `include`, `import` et `redefine`.

Voici un exemple d’arborescence :

![Explorateur de schémas XML](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Sélection et activation
Pour mettre en surbrillance et sélectionner un nœud, cliquez une fois dans l'Explorateur de schémas.

Pour activer un nœud, double-cliquez dessus ou appuyez sur **entrée** lorsque le nœud est sélectionné.

- L'activation d'un nœud ouvre le fichier dans lequel ce nœud est défini (si le fichier n'est pas déjà ouvert) et sélectionne le nœud dans le fichier.

- L'activation d'un nœud de fichier ouvre le fichier sélectionné (s'il n'est pas déjà ouvert) et met en surbrillance le nœud `<schema>`.

- L'activation d'un jeu de schémas ou d'un nœud d'espace de noms n'aboutit à rien.

## <a name="drag-and-drop-nodes"></a>Glisser-déplacer des nœuds
Vous pouvez déplacer des nœuds, des nœuds de fichier et des nœuds d'espace de noms par glisser-déplacer dans une vue du concepteur XSD. Si la vue actuelle est la vue de [départ](../xml-tools/start-view.md), le fait de faire glisser un nœud sur la vue permet d’ouvrir la [vue du graphique](../xml-tools/graph-view.md). Si la vue actuelle est la vue de [modèle de contenu](../xml-tools/content-model-view.md) ou de graphique, la vue ne change pas lorsque vous déposez un nœud sur celui-ci.

La suppression de fichiers sur la vue ajoute tous les nœuds globaux dans le fichier à l' [espace de travail du concepteur XSD](../xml-tools/xml-schema-designer-workspace.md). Le dépôt d’espaces de noms sur la vue ajoute tous les nœuds globaux dans l’espace de noms à l’espace de travail. L'espace de travail est partagé entre toutes les vues.

 Vous ne pouvez pas faire glisser-déplacer des importations ou des nœuds locaux.

## <a name="see-also"></a>Voir aussi

- [Procédure : ajouter des nœuds à l’espace de travail à partir de l’Explorateur de schémas XML](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
