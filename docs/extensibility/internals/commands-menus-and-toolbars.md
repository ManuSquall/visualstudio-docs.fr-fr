---
title: "Commandes, Menus et barres d’outils | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: "60"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa1513bcd61ac63fb9d2a59f69a8b2ce22cf5114
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="commands-menus-and-toolbars"></a>Commandes, Menus et barres d’outils
Menus et barres d’outils sont aux que manière dont les utilisateurs accéder aux commandes de votre VSPackage. Les commandes sont des fonctions qui accomplissent des tâches, comme l’impression d’un document, l’actualisation d’une vue ou la création d’un fichier. Les menus et barres d’outils s’avèrent pratiques pour présenter graphiquement vos commandes aux utilisateurs. En règle générale, les commandes associées sont regroupées dans le même menu ou la même barre d’outils.  
  
-   Les menus apparaissent généralement sous la forme de chaînes contenant un seul mot rassemblées sur une ligne en haut de l’environnement de développement intégré (IDE) ou d’une fenêtre Outil. Ils peuvent également apparaître après un clic droit et sont alors appelés menus contextuels. Quand vous cliquez dessus, les menus se développent pour présenter une ou plusieurs commandes. Les commandes, quand vous cliquez dessus, permettent d’effectuer des tâches ou de lancer des sous-menus qui contiennent d’autres commandes. Parmi les menus les plus connus figurent les menus Fichier, Edition, Affichage et Fenêtre. Pour plus d’informations, consultez [étendant les Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
-   Les barres d’outils sont généralement des rangées de boutons et autres contrôles, comme des zones de liste modifiable, des zones de liste, des zones de texte et des contrôleurs de menu. Tous les contrôles de barre d’outils sont associés à des commandes. Quand vous cliquez sur un bouton de barre d’outils, sa commande associée est activée. Les boutons de barre d’outils comportent généralement des icônes qui suggèrent les commandes sous-jacentes, comme une imprimante pour une commande Imprimer. Dans un contrôle de liste déroulante, chaque élément de la liste est associé à une commande différente. Un contrôleur de menu est un hybride dans lequel un côté du contrôle est un bouton de barre d’outils et l’autre côté est une flèche vers le bas qui présente des commandes supplémentaires quand vous cliquez dessus. Pour plus d’informations, consultez [Ajout d’un contrôleur de Menu à une barre d’outils](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Quand vous créez une commande, vous devez également lui créer un gestionnaire d’événements. Le gestionnaire d’événements détermine quand la commande est visible ou activée, vous permet de modifier son texte et garantit que la commande répond correctement (« itinéraires ») lors de son activation. Dans la plupart des cas, l’IDE gère les commandes à l’aide de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Commandes dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] itinéraire de façon hiérarchique, en commençant par le contexte de commande plus profond, en fonction de la sélection locale, puis en continuant pour le contexte le plus extérieur, en fonction de la sélection globale. Les commandes ajoutées au menu principal sont immédiatement disponibles pour les scripts. Pour plus d’informations, consultez [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) et [les objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md).  
  
 Pour définir de nouveaux menus et de nouvelles barres d’outils, vous devez les décrire dans un fichier Visual Studio Command Table (.vsct). Le modèle de package Visual Studio crée ce fichier pour vous, ainsi que les éléments nécessaires pour prendre en charge les commandes, barres d’outils et éditeurs que vous avez sélectionnés dans le modèle. Vous pouvez également écrire votre propre fichier .vsct, en utilisant le schéma xml décrit ici : [référence du schéma XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Pour plus d’informations sur l’utilisation des fichiers .vsct, consultez [Visual Studio Command Table (. Fichiers VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Les rubriques de cette section expliquent le fonctionnement des commandes, des menus et barres d’outils dans les VSPackages.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Une description détaillée de la spécification de Format de Table de commande.  
  
 [Fichiers Visual Studio Command Table (.Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Décrit une syntaxe basée sur XML et le compilateur pour les tables de la commande.  
  
 [Emplacement de commande, de groupe et de barre d’outils par défaut](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Décrit les barres d’outils, des groupes, des menus et des commandes prédéfinies.  
  
 [Commandes, menus et groupes définis par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Spécifie les menus prédéfinis, les commandes et les groupes de commandes disponibles pour une utilisation par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Création de commande](../../extensibility/internals/command-design.md)  
 Explique comment concevoir des commandes.  
  
 [Optimisation des commandes de menu et de barre d’outils](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Fournit des recommandations pour les commandes.  
  
 [Rendre les commandes disponibles](../../extensibility/internals/making-commands-available.md)  
 Explique comment rendre disponibles les commandes de Visual Studio.  
  
 [Commandes et menus utilisant des assemblys d’interopérabilité](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Explique comment implémenter des commandes qui utilisent des assemblys PIA.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Routage des commandes dans VSPackages](../../extensibility/internals/command-routing-in-vspackages.md)  
 Explique le routage des commandes dans des VSPackages.