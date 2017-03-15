---
title: "Vue d’ensemble des barres d’outils, menus et commandes | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "essentiel des menus [SDK Visual Studio]"
  - "essentiel des barres d’outils [SDK Visual Studio]"
ms.assetid: cbdaceaa-7dd3-4a56-aea6-b759e48d83d6
caps.latest.revision: 19
caps.handback.revision: 19
manager: "douge"
---
# Vue d’ensemble des barres d’outils, menus et commandes
Les menus et barres d’outils constituent un moyen graphique pratique pour les utilisateurs d’accéder aux commandes de votre VSPackage. Les commandes sont des fonctions qui accomplissent des tâches, comme l’impression d’un document, l’actualisation d’une vue ou la création d’un fichier. Les menus et barres d’outils s’avèrent pratiques pour présenter graphiquement vos commandes aux utilisateurs. En règle générale, les commandes associées sont regroupées dans le même menu ou la même barre d’outils.  
  
-   Les menus apparaissent généralement sous la forme de chaînes contenant un seul mot rassemblées sur une ligne en haut de l’environnement de développement intégré \(IDE\) ou d’une fenêtre Outil. Ils peuvent également apparaître après un clic droit et sont alors appelés menus contextuels. Quand vous cliquez dessus, les menus se développent pour présenter une ou plusieurs commandes. Les commandes, quand vous cliquez dessus, permettent d’effectuer des tâches ou de lancer des sous\-menus qui contiennent d’autres commandes. Parmi les menus les plus connus figurent les menus Fichier, Edition, Affichage et Fenêtre. Pour plus d’informations, consultez [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md).  
  
-   Les barres d’outils sont généralement des rangées de boutons et autres contrôles, comme des zones de liste modifiable, des zones de liste, des zones de texte et des contrôleurs de menu. Tous les contrôles de barre d’outils sont associés à des commandes. Quand vous cliquez sur un bouton de barre d’outils, sa commande associée est activée. Les boutons de barre d’outils comportent généralement des icônes qui suggèrent les commandes sous\-jacentes, comme une imprimante pour une commande Imprimer. Dans un contrôle de liste déroulante, chaque élément de la liste est associé à une commande différente. Un contrôleur de menu est un hybride dans lequel un côté du contrôle est un bouton de barre d’outils et l’autre côté est une flèche vers le bas qui présente des commandes supplémentaires quand vous cliquez dessus. Pour plus d’informations, consultez [Comment : créer des barres d’outils pour les fenêtres Outil](../misc/how-to-create-toolbars-for-tool-windows.md) et [Ajouter des icônes aux commandes de Menu](../extensibility/adding-icons-to-menu-commands.md).  
  
-   Quand vous créez une commande, vous devez également lui créer un gestionnaire d’événements. Le gestionnaire d’événements détermine quand la commande est visible ou activée, vous permet de modifier son texte et garantit que la commande répond correctement \(« itinéraires »\) lors de son activation. Dans la plupart des cas, l’IDE gère les commandes à l’aide de l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>. Les commandes de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] défilent de façon hiérarchique, en commençant par le contexte de commande le plus central, selon la sélection locale, puis en continuant avec le contexte le plus périphérique, selon la sélection globale. Les commandes ajoutées au menu principal sont immédiatement disponibles pour les scripts. Pour plus d’informations, consultez [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md) et [Objets de contexte de sélection](../extensibility/internals/selection-context-objects.md).  
  
 Pour définir de nouveaux menus et de nouvelles barres d’outils, vous devez les décrire dans un fichier Visual Studio Command Table \(.vsct\). Le modèle de package Visual Studio crée ce fichier pour vous, ainsi que les éléments nécessaires pour prendre en charge les commandes, barres d’outils et éditeurs que vous avez sélectionnés dans le modèle. Vous pouvez également écrire votre propre fichier .vsct en utilisant le schéma xml décrit ici : [Référence de schéma XML de VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
 Pour plus d’informations sur l’utilisation des fichiers .vsct, consultez [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) ou essayez l’une des [Procédures pas à pas pour les éléments d’interface utilisateur](../misc/walkthroughs-for-user-interface-elements.md).  
  
 Pour obtenir une vue d’ensemble plus précise des menus et barres d’outils, consultez [Création de la commande](../extensibility/internals/command-design.md).  
  
## Voir aussi  
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Packages VS](../extensibility/internals/vspackages.md)