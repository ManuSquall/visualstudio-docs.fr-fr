---
title: "Commandes, Menus et barres d&#39;outils | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menus (Visual Studio SDK), commandes"
  - "commandes (Visual Studio)"
  - "barres d'outils (Visual Studio), commandes"
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: 60
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 60
---
# Commandes, Menus et barres d&#39;outils
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Menus et barres d'outils sont que les manière dont les utilisateurs accéder aux commandes dans votre VSPackage. Commandes sont des fonctions qui accomplissent les tâches, telles que l'impression d'un document, l'actualisation d'une vue ou en créant un nouveau fichier. Menus et barres d'outils constituent un moyen graphique pratique pour présenter vos commandes aux utilisateurs. En règle générale, les commandes associées sont regroupées dans le même menu ou barre d'outils.  
  
-   En règle générale, les menus s'affichent sous forme de chaînes d'un mot en cluster dans une ligne en haut de l'environnement de développement intégré \(IDE\) ou une fenêtre outil. Menus peuvent être affichés à la suite d'un événement de clic droit et sont désignés comme des menus contextuels dans ce contexte. Lorsque vous cliquez dessus, menus développent pour afficher une ou plusieurs commandes. Commandes, cliquez sur cette option peuvent effectuer des tâches ou lancez sous\-menus qui contiennent des commandes supplémentaires. Certains noms de menu bien connus sont fichier, Édition, affichage et fenêtre. Pour plus d'informations, consultez [Extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
-   Barres d'outils sont généralement des lignes de boutons et autres contrôles, tels que les zones de liste déroulante, les zones de liste, les zones de texte et les contrôleurs de menu. Tous les contrôles de barre d'outils sont associés à des commandes. Lorsque vous cliquez sur un bouton de barre d'outils, la commande associée est activée. Boutons de barre d'outils ont généralement des icônes qui propose les commandes sous\-jacent, tel qu'une imprimante pour une commande d'impression. Dans un contrôle de liste déroulante, chaque élément de la liste est associé à une autre commande. Un contrôleur de menu est un hybride dans laquelle un côté du contrôle est un bouton de barre d'outils et l'autre extrémité est une flèche vers le bas qui affiche des commandes supplémentaires lorsque vous cliquez sur. Pour plus d'informations, consultez [Ajout d'un contrôleur de Menu à une barre d'outils](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Lorsque vous créez une commande, vous devez également créer un gestionnaire d'événements. Le Gestionnaire d'événements détermine quand la commande est visible ou activé, vous pouvez ainsi modifier son texte et s'assure que la commande répond correctement \(« itinéraires »\) lors de l'activation. Dans la plupart des cas, l'IDE gère les commandes à l'aide de la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface. Commandes dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] itinéraire dans une structure hiérarchique, en commençant par le contexte de commande plus profond, en fonction de la sélection locale et en cours de traitement pour le contexte le plus extérieur, en fonction de la sélection globale. Les commandes ajoutées au menu principal sont immédiatement disponibles pour le script. Pour plus d’informations, consultez [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) et [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md).  
  
 Pour définir de nouveaux menus et les barres d'outils, vous devez les décrire dans un fichier de la Table de commandes de Visual Studio \(.vsct\). Le modèle de Package Visual Studio crée ce fichier pour vous, ainsi que les éléments nécessaires pour prendre en charge les commandes, les barres d'outils et les éditeurs que vous avez sélectionné dans le modèle. Vous pouvez également écrire votre propre fichier .vsct, en utilisant le schéma xml décrit ici : [Référence de schéma XML de VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Pour plus d'informations sur l'utilisation des fichiers .vsct, consultez la page [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Les rubriques de cette section expliquent le fonctionnement des commandes, des menus et barres d'outils dans les VSPackages.  
  
## Dans cette section  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Une description détaillée de la spécification de Format de Table de commande.  
  
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Décrit une syntaxe basé sur XML et le compilateur pour les tables de la commande.  
  
 [Commande par défaut, le groupe et la sélection élective de la barre d'outils](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 Décrit les barres d'outils, des groupes, des menus et des commandes prédéfinies.  
  
 [Groupes, les Menus et les commandes définies par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Spécifie les menus prédéfinis, les commandes et les groupes de commande disponibles pour une utilisation par le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Création de la commande](../../extensibility/internals/command-design.md)  
 Explique comment concevoir des commandes.  
  
 [Optimisation des menus et des commandes de barre d'outils](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Donne des indications pour les commandes.  
  
 [Disposition des commandes](../../extensibility/internals/making-commands-available.md)  
 Explique comment rendre les commandes disponibles pour Visual Studio.  
  
 [Commandes et des Menus qui utilisent des assemblys PIA](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Explique comment implémenter des commandes qui utilisent des assemblys PIA.  
  
## Rubriques connexes  
 [Routage des commandes dans les packages VS](../../extensibility/internals/command-routing-in-vspackages.md)  
 Explique les VSPackages routage des commandes.