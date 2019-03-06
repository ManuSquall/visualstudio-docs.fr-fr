---
title: Commandes, Menus et barres d’outils | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a0634105b9b071ac4155adb3248abd2b4be19b29
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606262"
---
# <a name="commands-menus-and-toolbars"></a>Commandes, menus et barres d’outils
Menus et barres d’outils sont que les manière dont les utilisateurs accéder aux commandes dans votre VSPackage. Les commandes sont des fonctions qui accomplissent des tâches, comme l’impression d’un document, l’actualisation d’une vue ou la création d’un fichier. Les menus et barres d’outils s’avèrent pratiques pour présenter graphiquement vos commandes aux utilisateurs. En règle générale, les commandes associées sont regroupées dans le même menu ou la même barre d’outils.

- Les menus apparaissent généralement sous la forme de chaînes contenant un seul mot rassemblées sur une ligne en haut de l’environnement de développement intégré (IDE) ou d’une fenêtre Outil. Ils peuvent également apparaître après un clic droit et sont alors appelés menus contextuels. Quand vous cliquez dessus, les menus se développent pour présenter une ou plusieurs commandes. Les commandes, quand vous cliquez dessus, permettent d’effectuer des tâches ou de lancer des sous-menus qui contiennent d’autres commandes. Certains noms de menu connu **fichier**, **modifier**, **vue**, et **fenêtre**. Pour plus d’informations, consultez [étendre des menus et commandes](../../extensibility/extending-menus-and-commands.md).

- Les barres d’outils sont généralement des rangées de boutons et autres contrôles, comme des zones de liste modifiable, des zones de liste, des zones de texte et des contrôleurs de menu. Tous les contrôles de barre d’outils sont associés à des commandes. Quand vous cliquez sur un bouton de barre d’outils, sa commande associée est activée. Les boutons de barre d’outils comportent généralement des icônes qui suggèrent les commandes sous-jacentes, comme une imprimante pour une commande Imprimer. Dans un contrôle de liste déroulante, chaque élément de la liste est associé à une commande différente. Un contrôleur de menu est un hybride dans lequel un côté du contrôle est un bouton de barre d’outils et l’autre côté est une flèche vers le bas qui présente des commandes supplémentaires quand vous cliquez dessus. Pour plus d’informations, consultez [ajouter un contrôleur de menu à une barre d’outils](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).

- Quand vous créez une commande, vous devez également lui créer un gestionnaire d’événements. Le gestionnaire d’événements détermine quand la commande est visible ou activée, vous permet de modifier son texte et garantit que la commande répond correctement (« itinéraires ») lors de son activation. Dans la plupart des cas, l’IDE gère les commandes à l’aide de l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Les commandes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] défilent de façon hiérarchique, en commençant par le contexte de commande le plus central, selon la sélection locale, puis en continuant avec le contexte le plus périphérique, selon la sélection globale. Les commandes ajoutées au menu principal sont immédiatement disponibles pour les scripts. Pour plus d’informations, consultez [MenuCommands et. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) et [les objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md).

  Pour définir de nouveaux menus et barres d’outils, vous devez les décrire dans une table de commandes de Visual Studio (*.vsct*) fichier. Le modèle de package Visual Studio crée ce fichier pour vous, ainsi que les éléments nécessaires pour prendre en charge les commandes, les barres d’outils et les éditeurs que vous avez sélectionné dans le modèle. Vous pouvez également écrire votre propre *.vsct* de fichiers, en utilisant le schéma XML décrit ici : [Référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md).

  Pour plus d’informations sur l’utilisation de *.vsct* de fichiers, consultez [fichiers Visual Studio command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

  Les rubriques de cette section expliquent le fonctionnement des commandes, menus et barres d’outils dans les VSPackages.

## <a name="in-this-section"></a>Dans cette section
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Une description détaillée de la spécification de format de table de commande.

- [Visual Studio fichiers command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

 Décrit une syntaxe basée sur XML et le compilateur pour les tables de la commande.

- [Placement de commande, le groupe et barre d’outils par défaut](../../extensibility/internals/default-command-group-and-toolbar-placement.md)

 Décrit les barres d’outils, des groupes, des menus et des commandes prédéfinies.

- [Groupes, les menus et commandes définies par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Spécifie les menus prédéfinis, les commandes et les groupes de commandes disponibles pour une utilisation par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- [Conception de la commande](../../extensibility/internals/command-design.md)

 Explique comment concevoir des commandes.

- [Optimiser les commandes de menu et barre d’outils](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)

 Donne des indications pour les commandes.

- [Rendre les commandes disponibles](../../extensibility/internals/making-commands-available.md)

 Explique comment rendre les commandes disponibles pour Visual Studio.

- [Commandes et des menus qui utilisent des assemblys d’interopérabilité](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)

 Explique comment implémenter des commandes qui utilisent des assemblys d’interopérabilité.

## <a name="related-sections"></a>Rubriques connexes
- [Routage des commandes dans VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)

 Explique le routage des commandes dans VSPackages.