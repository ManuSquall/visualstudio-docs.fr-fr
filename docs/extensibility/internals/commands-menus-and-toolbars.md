---
title: Commandes, menus et barres d’outils Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2be2f719d0f123328d5c518c08e30df2185e2a19
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709503"
---
# <a name="commands-menus-and-toolbars"></a>Commandes, menus et barres d’outils
Les menus et les barres d’outils sont la façon dont les utilisateurs accèdent aux commandes dans votre VSPackage. Les commandes sont des fonctions qui accomplissent des tâches, comme l’impression d’un document, l’actualisation d’une vue ou la création d’un fichier. Les menus et barres d’outils s’avèrent pratiques pour présenter graphiquement vos commandes aux utilisateurs. En règle générale, les commandes associées sont regroupées dans le même menu ou la même barre d’outils.

- Les menus apparaissent généralement sous la forme de chaînes contenant un seul mot rassemblées sur une ligne en haut de l’environnement de développement intégré (IDE) ou d’une fenêtre Outil. Ils peuvent également apparaître après un clic droit et sont alors appelés menus contextuels. Quand vous cliquez dessus, les menus se développent pour présenter une ou plusieurs commandes. Les commandes, quand vous cliquez dessus, permettent d’effectuer des tâches ou de lancer des sous-menus qui contiennent d’autres commandes. Certains noms de menu bien connus sont **Fichier**, **Edit**, **Voir**, et **fenêtre**. Pour plus d’informations, voir [Menus et commandes Extend](../../extensibility/extending-menus-and-commands.md).

- Les barres d’outils sont généralement des rangées de boutons et autres contrôles, comme des zones de liste modifiable, des zones de liste, des zones de texte et des contrôleurs de menu. Tous les contrôles de barre d’outils sont associés à des commandes. Quand vous cliquez sur un bouton de barre d’outils, sa commande associée est activée. Les boutons de barre d’outils comportent généralement des icônes qui suggèrent les commandes sous-jacentes, comme une imprimante pour une commande Imprimer. Dans un contrôle de liste déroulante, chaque élément de la liste est associé à une commande différente. Un contrôleur de menu est un hybride dans lequel un côté du contrôle est un bouton de barre d’outils et l’autre côté est une flèche vers le bas qui présente des commandes supplémentaires quand vous cliquez dessus. Pour plus d’informations, voir [Ajouter un contrôleur de menu à une barre d’outils](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Quand vous créez une commande, vous devez également lui créer un gestionnaire d’événements. Le gestionnaire d’événements détermine quand la commande est visible ou activée, vous permet de modifier son texte et garantit que la commande répond correctement (« itinéraires ») lors de son activation. Dans la plupart des cas, l’IDE gère les commandes à l’aide de l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Les commandes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] défilent de façon hiérarchique, en commençant par le contexte de commande le plus central, selon la sélection locale, puis en continuant avec le contexte le plus périphérique, selon la sélection globale. Les commandes ajoutées au menu principal sont immédiatement disponibles pour les scripts. Pour plus d’informations, voir [MenuCommands vs OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015) and [Selection context objects](../../extensibility/internals/selection-context-objects.md).

  Pour définir de nouveaux menus et barres d’outils, vous devez les décrire dans un fichier visual studio de commande *(.vsct).* Le modèle de paquet Visual Studio crée ce fichier pour vous, ainsi que les éléments nécessaires pour prendre en charge les commandes, les barres d’outils et les éditeurs que vous avez sélectionnés dans le modèle. Alternativement, vous pouvez écrire votre propre fichier *.vsct,* en utilisant le schéma XML décrit ici: [VSCT XML référence schéma](../../extensibility/vsct-xml-schema-reference.md).

  Pour plus d’informations sur le travail avec des fichiers *.vsct,* voir [Visual Studio table de commande (.vsct) fichiers](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

  Les sujets de cette section expliquent comment les commandes, les menus et les barres d’outils fonctionnent dans VSPackages.

## <a name="in-this-section"></a>Contenu de cette section
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Une description en profondeur des spécifications de format de tableau de commande.

- [Fichiers visualister de table de commande de studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Décrit une syntaxe et un compilateur basés sur XML pour les tables de commande.

- [Placement par défaut de commande, de groupe et de barre d’outils](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Décrit les commandes prédéfinies, les groupes, les menus et les barres d’outils.

- [Commandes, menus et groupes définis par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Spécifie les menus, commandes et groupes de commande [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prédéfinis disponibles pour une utilisation par l’IDE.

- [Conception de commande](../../extensibility/internals/command-design.md)

 Explique comment concevoir des commandes.

- [Optimiser les commandes de menu et de barre d’outils](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Donne des lignes directrices pour les commandes.

- [Rendre les commandes disponibles](../../extensibility/internals/making-commands-available.md)

 Explique comment mettre les commandes à la disposition de Visual Studio.

- [Commandes et menus qui utilisent des assemblages interop](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Explique comment mettre en œuvre des commandes qui utilisent des assemblages interop.

## <a name="related-sections"></a>Sections connexes
- [Itinéraire de commande dans VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Explique le routage de commande dans VSPackages.
