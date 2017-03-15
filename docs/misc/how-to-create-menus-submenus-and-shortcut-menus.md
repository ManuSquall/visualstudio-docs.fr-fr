---
title: "Proc&#233;dure&#160;: cr&#233;ation de menus, sous-menus et menus contextuels | Microsoft Docs"
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
  - "barres de commandes, architecture"
  - "menus, création"
  - "menus, architecture"
  - "commandes, menus"
  - "menus"
ms.assetid: 62004fd9-7f99-4f00-8d01-1dde53e23dbb
caps.latest.revision: 46
caps.handback.revision: 46
manager: "douge"
---
# Proc&#233;dure&#160;: cr&#233;ation de menus, sous-menus et menus contextuels
Pour ajouter un menu à l’environnement de développement intégré \(IDE\) Visual Studio, un VSPackage doit utiliser l’architecture [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] pour les menus de groupes de commandes. Un menu de groupes de commandes permet à des composants et à l’IDE de partager des commandes. Pour plus d’informations sur les menus de groupes de commandes, consultez la page [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Dans les VSPackages, les menus sont définis dans la section [Menus](../extensibility/menus-element.md) d’un fichier .vsct. Un fichier .vsct définit des menus, des barres d’outils, des groupes et des commandes. Une commande est un élément sur lequel un utilisateur clique pour exécuter une fonction. Un groupe est un conteneur de commandes. Un menu est un conteneur de groupes. Pour créer un menu de base, vous devez créer un menu, un groupe de commandes et au moins une commande.  
  
 Un menu peut apparaître dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de trois principales manières :  
  
-   Sous forme de menu dans la barre de menus principale  
  
-   Sous forme de sous\-menu d’un autre menu.  
  
-   Sous forme de menu contextuel \(généralement affiché par un clic droit\)  
  
 Cette rubrique montre comment créer chaque type de menu. Les procédures pas à pas suivantes montrent également comment procéder :  
  
-   [Ajout d'un Menu à la barre de menus de Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
  
-   [Ajout d'un sous\-menu à un Menu](../extensibility/adding-a-submenu-to-a-menu.md)  
  
-   [Ajout d'un Menu contextuel dans une fenêtre outil](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md)  
  
### Pour créer un menu, un sous\-menu ou un menu contextuel  
  
1.  Dans votre projet, double\-cliquez sur le fichier .vsct pour l’ouvrir dans l’éditeur.  
  
     Si votre projet n’a pas de fichier .vsct, ajoutez\-en un. Si vous créez un package à l’aide du modèle de package Visual Studio, sélectionnez **Commande de menu** pour générer un fichier .vsct.  
  
2.  Dans la section `Symbols`, recherchez l’élément [GuidSymbol](../extensibility/guidsymbol-element.md) qui contient les groupes et les commandes.  
  
3.  Créez un élément [IDSymbol](../extensibility/idsymbol-element.md) pour chaque menu, groupe ou commande à ajouter, comme illustré dans l’exemple suivant.  
  
     [!CODE [ButtonGroup#01](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#01)]  
  
     Les attributs `name` des éléments `GuidSymbol` et `IDSymbol` fournissent la paire GUID:ID pour chaque nouveau menu, groupe ou commande. Le `GUID` représente un jeu de commandes défini pour votre VSPackage. Vous pouvez définir plusieurs jeux de commandes. Chaque paire GUID:ID doit être unique.  
  
4.  Définissez le nouveau menu dans la section `Menus` comme suit :  
  
    1.  Définissez les champs `guid` et `id` pour qu’ils correspondent à la paire GUID:ID du nouveau menu.  
  
    2.  Définissez l’attribut `priority`.  
  
         L’attribut `priority` est utilisé par le fichier .vsct pour déterminer l’emplacement du menu parmi les autres objets présents dans le groupe parent.  
  
         Les menus qui ont des valeurs de priorité inférieure sont affichés avant ceux qui ont des valeurs de priorité plus élevée. Les valeurs de priorité en double sont autorisées, mais la position relative des menus de même priorité est déterminée par l’ordre dans lequel les VSPackages sont traités au moment de l’exécution, et cet ordre ne peut pas être prédéterminé. Si vous omettez l’attribut `priority`, la valeur 0 lui est affectée.  
  
         Ne définissez pas de priorité pour un menu contextuel, car son emplacement est déterminé par le code qui l’appelle.  
  
    3.  Pour les menus et les sous\-menus, affectez la valeur `Menu` \(qui décrit un menu standard\) à l’attribut `type`. Pour les menus contextuels, affectez la valeur `Context` à l’attribut `type`.  
  
         Pour obtenir une description des autres types de menus valides, tels que les barres d’outils et les contrôleurs de menus, consultez [Élément de menu](../extensibility/menu-element.md).  
  
    4.  Dans la définition du menu, créez un élément [Strings](../extensibility/strings-element.md) contenant un élément [ButtonText](../extensibility/buttontext-element.md) destiné à contenir le nom du menu tel qu’il apparaît dans l’IDE, et un élément [CommandName](../extensibility/commandname-element.md) destiné à contenir le nom de la commande utilisée pour accéder au menu de la fenêtre **Commande**.  
  
         Si la chaîne de texte du bouton comprend le caractère « & », l’utilisateur peut ouvrir le menu en appuyant sur Alt plus le caractère qui suit « & ».  
  
    5.  Ajoutez des indicateurs de commandes, si nécessaire, pour modifier l’apparence et le comportement du menu. Pour ce faire, ajoutez un élément [CommandFlag](../extensibility/command-flag-element.md) dans la définition du menu. Pour plus d'informations, consultez [Élément indicateur de commande](../extensibility/command-flag-element.md).  
  
5.  Définissez le parent du menu. Pour un menu ou un sous\-menu standard, procédez de l’une des façons suivantes, en fonction de votre conception :  
  
    -   Dans l’élément `Menu`, créez un élément [Parent](../extensibility/parent-element.md) et affectez à ses champs `guid` et `id` la valeur GUID:ID du groupe qui hébergera le menu, également appelé *groupe parent principal*. Le groupe parent peut être un groupe que vous avez créé dans la section `Symbols`, un groupe d’un autre package ou un groupe de l’IDE. Par exemple, pour ajouter votre menu à la barre de menus de niveau supérieur de l’IDE, près du menu **Outils**, affectez la valeur guidSHLMainMenu:IDG\_VS\_MM\_TOOLSADDINS au parent.  
  
         L’exemple suivant montre un menu qui s’affiche dans la barre de menus de Visual Studio.  
  
         [!CODE [TopLevelMenu#01](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#01)]  
  
    -   Vous pouvez omettre l’élément `Parent` si le menu doit être positionné en utilisant le placement de commande. Créez une section [CommandPlacements](../extensibility/commandplacements-element.md) avant la section `Symbols` et ajoutez un élément [CommandPlacement](../extensibility/commandplacement-element.md) ayant la paire GUID:ID du menu, une priorité et un parent, comme illustré dans l’exemple suivant.  
  
         [!CODE [ButtonGroup#04](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#04)]  
  
         Si vous créez plusieurs placements de commandes et que leur paire GUID:ID est identique mais pas leurs parents, le menu apparaît à plusieurs endroits. Pour plus d'informations, consultez [Élément de CommandPlacements](../extensibility/commandplacements-element.md).  
  
     Un menu standard doit avoir un groupe dans la barre de menus de Visual Studio comme parent. Pour un sous\-menu, le parent doit être un groupe dans un autre menu \(ou dans une barre d’outils ou autre type de menu\). Pour qu’un menu ou un sous\-menu soit affiché, il doit héberger un groupe qui contient au moins une commande active ou il faut que son indicateur de commande `AlwaysCreate` soit défini.  
  
     Les menus contextuels n’ont pas ni parents, ni placements de commande. Au lieu de cela, ils doivent être activés dans le code. En règle générale, un menu contextuel est activé en réponse à un clic droit sur une surface de contrôle. L’exemple suivant définit un menu contextuel.  
  
     [!CODE [ButtonGroup#06](../CodeSnippet/VS_Snippets_VSSDK/buttongroup#06)]  
  
6.  Dans la section [Groups](../extensibility/groups-element.md), créez un élément [Group](../extensibility/group-element.md) destiné à contenir les commandes qui doivent apparaître dans votre menu. La section `Symbols` doit contenir une entrée ayant la même paire GUID:ID que le nouvel élément `Group`.  
  
    1.  Définissez la priorité du groupe pour qu’il s’affiche là où vous le voulez dans votre menu.  
  
         Les limites de chaque groupe dans le menu sont affichées sous forme de lignes horizontales.  
  
    2.  Affectez comme parent de ce nouveau groupe la paire GUID:ID du menu que vous avez créé. Cela ajoute le groupe de commandes au menu.  
  
     Le groupe dans l’exemple suivant s’affiche dans le menu de niveau supérieur illustré dans l’exemple précédent.  
  
     [!CODE [TopLevelMenu#02](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#02)]  
  
     Les menus peuvent contenir des commandes et des sous\-menus. Un sous\-menu \(parfois appelé menu en cascade\) est un menu ordinaire, sauf qu’il est ajouté au groupe d’un autre menu et est exposé uniquement lorsque cet autre menu est appelé. Si vous placez le menu illustré dans l’exemple suivant dans un groupe dans le menu de niveau supérieur, il devient un sous\-menu.  
  
     [!CODE [TopLevelMenu#06](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#06)]  
  
7.  Ajoutez des commandes au menu en créant des entrées de commande dans la section [Buttons](../extensibility/buttons-element.md) et en affectant comme parent de chacune d’elles la paire GUID:ID de votre groupe. Chaque élément [Button](../extensibility/button-element.md) doit avoir une paire GUID:ID qui correspond à une entrée dans la section `Symbols`.  
  
     Utilisez l’attribut `priority` de chaque entrée de bouton pour spécifier l’ordre dans lequel les commandes sont affichées dans le groupe.  
  
     L’exemple suivant définit une commande qui sera affichée dans le menu de niveau supérieur.  
  
     [!CODE [TopLevelMenu#03](../CodeSnippet/VS_Snippets_VSSDK/toplevelmenu#03)]  
  
     Pour plus d’informations sur les boutons et les éléments de menu, consultez [Élément de bouton](../extensibility/button-element.md).  
  
     Pour plus d’informations sur la façon d’implémenter des commandes de menu dans le code, consultez [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md) ou les procédures pas à pas mentionnées plus haut dans cette rubrique.  
  
### Pour activer un menu contextuel  
  
1.  Obtenez la paire GUID:ID du menu contextuel. Par défaut, le modèle de package crée une classe `GuidList` dans un fichier PkgCmdID.cs pour contenir le GUID du jeu de commandes. Le modèle crée également une classe `PkgCmdIdList` dans un fichier PkgCmdId.cs pour contenir les valeurs d’ID entières des commandes qui sont déclarées dans le modèle. Vous devez déclarer les menus contextuels et les éventuelles commandes supplémentaires une fois le modèle terminé. L’exemple ci\-dessous illustre ces déclarations.  
  
     [!code-cs[TWShortcutMenu#12](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_8.cs)]  
  
     Vous pouvez omettre cette étape si les valeurs GUID et ID seront utilisées directement. Toutefois, nous vous recommandons de définir les valeurs ici pour une meilleure lisibilité.  
  
2.  Attachez à un gestionnaire d’événements. En général, les menus contextuels sont attachés au clic droit d’une surface de contrôle, comme illustré dans l’exemple suivant.  
  
     [!code-cs[TWShortcutMenu#43](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_9.cs)]  
  
     La méthode <xref:System.Windows.Forms.Control.PointToScreen%2A> convertit la position du clic, qui est relative au contrôle, en une position à l’écran. La méthode <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> affiche le menu contextuel.  
  
     Le fichier qui contient le gestionnaire d’événements doit inclure l’espace de noms <xref:System.ComponentModel.Design> pour accéder à la classe <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>, et l’espace de noms <xref:Microsoft.VisualStudio.Shell> pour accéder à l’interface <xref:System.ComponentModel.Design.IMenuCommandService>.  
  
     [!code-cs[TWShortcutMenu#41](../misc/codesnippet/CSharp/how-to-create-menus-submenus-and-shortcut-menus_10.cs)]  
  
## Voir aussi  
 [MenuCommands Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)   
 [Référence de schéma XML de VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)