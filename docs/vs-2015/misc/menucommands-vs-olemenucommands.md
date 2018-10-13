---
title: MenuCommands Vs. OleMenuCommands | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
manager: douge
ms.openlocfilehash: c555b306c38d852f8fbd02c6f2b9347f4a359559
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193581"
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommands Vs. OleMenuCommands
Vous pouvez créer des commandes de menu en dérivant de <xref:System.ComponentModel.Design.MenuCommand> ou de l’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> et en implémentant les gestionnaires d’événements appropriés. Dans la plupart des cas, vous pouvez utiliser <xref:System.ComponentModel.Design.MenuCommand>, à l’instar du modèle de projet VSPackage, mais vous pouvez parfois être amené à utiliser <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>.  
  
 Les commandes qu’un VSPackage met à la disposition de l’IDE doivent être visibles et activées avant qu’un utilisateur puisse les utiliser. Quand elles sont créées dans un fichier .vsct à l’aide du modèle de projet de package Visual Studio, les commandes sont visibles et activées par défaut. Le fait de définir des indicateurs de commande, tels que `DynamicItemStart`, peut modifier le comportement par défaut. La visibilité, l’état activé et les autres propriétés d’une commande peuvent aussi être modifiés dans le code au moment de l’exécution en accédant à l’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> associé à la commande.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Emplacements du modèle de projet de package Visual Studio  
 Vous pouvez trouver le modèle de package Visual Studio dans la boîte de dialogue **Nouveau projet** sous **Visual Basic / Extensibilité**, **C# / Extensibilité**ou **Autres types de projets / Extensibilité**.  
  
## <a name="creating-a-command"></a>Création d’une commande  
 L’ensemble des commandes, groupes de commandes, menus, barres d’outils et fenêtres Outil sont définis dans le fichier .vsct. Pour plus d'informations, consultez [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Si vous créez un VSPackage à l’aide du modèle de package, sélectionnez **Commande de menu** pour créer un fichier .vsct et définir une commande de menu par défaut. Pour plus d’informations, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>Pour ajouter une commande à l’IDE  
  
1.  Ouvrez le fichier .vsct.  
  
2.  Dans la section `Symbols` , recherchez l’élément [GuidSymbol](../extensibility/guidsymbol-element.md) qui contient les groupes et les commandes.  
  
3.  Créez un élément [IDSymbol](../extensibility/idsymbol-element.md) pour chaque menu, groupe ou commande à ajouter, comme le montre l’exemple suivant.  
  
    ```xml
    <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
      <IDSymbol name="MyMenuGroup" value="0x1020" />
      <IDSymbol name="cmdidMyCommand" value="0x0100" />
    </GuidSymbol>
    ```
      
     Les attributs `name` des éléments `GuidSymbol` et `IDSymbol` fournissent la paire GUID:ID pour chaque nouveau menu, groupe ou commande. Le `guid` représente un jeu de commandes défini pour votre VSPackage. Vous pouvez définir plusieurs jeux de commandes. Chaque paire GUID:ID doit être unique.  
  
4.  Dans la section [Buttons](../extensibility/buttons-element.md) , créez un élément [Button](../extensibility/button-element.md) pour définir la commande, comme le montre l’exemple suivant.  
  
    ```xml
    <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ``` 
     
    1.  Définissez les champs `guid` et `id` de façon à les faire correspondre à la paire GUID:ID de la nouvelle commande.  
  
    2.  Définissez l’attribut `priority`.  
  
         L’attribut `priority` est utilisé par le fichier .vsct pour déterminer l’emplacement du bouton parmi les autres objets présents dans son groupe parent.  
  
         Les commandes qui ont des valeurs de priorité inférieure s’affichent au-dessus ou à gauche des commandes qui ont des valeurs de priorité plus élevées. Les valeurs de priorité en double sont autorisées, mais la position relative des commandes de même priorité est déterminée par l’ordre de traitement des VSPackages au moment de l’exécution, et cet ordre ne peut pas être prédéterminé.  
  
         Si vous omettez l’attribut `priority`, la valeur 0 lui est affectée.  
  
    3.  Définissez l’attribut `type` . Dans la plupart des cas, sa valeur est `"Button"`. Pour obtenir une description des autres types de boutons valides, consultez [Button Element](../extensibility/button-element.md).  
  
5.  Dans la définition du bouton, créez un élément [Strings](../extensibility/strings-element.md) contenant un élément [ButtonText](../extensibility/buttontext-element.md) . Celui-ci contiendra le nom du menu tel qu’il apparaîtra dans l’IDE. Créez ensuite un élément [CommandName](../extensibility/commandname-element.md) qui contiendra le nom de la commande utilisé pour accéder au menu de la fenêtre **Commande** .  
  
     Si la chaîne de texte du bouton inclut le caractère « & », l’utilisateur peut ouvrir le menu en appuyant sur ALT puis sur le caractère qui suit « & ».  
  
     L’ajout d’un élément `Tooltip` fait apparaître le texte qu’il contient quand un utilisateur place le pointeur sur le bouton.  
  
6.  Ajoutez un élément [Icon](../extensibility/icon-element.md) pour spécifier l’icône éventuelle à afficher avec la commande. Si les icônes sont obligatoires pour les boutons des barres d’outils, elles ne le sont pas pour les éléments de menu. Le `guid` et l’ `id` de l’élément `Icon` doivent correspondre à ceux d’un élément [Bitmap](../extensibility/bitmap-element.md) défini dans la section `Bitmaps` .  
  
7.  Ajoutez des indicateurs de commande, si nécessaire, pour modifier l’apparence et le comportement du bouton. Pour ce faire, ajoutez un élément [CommandFlag](../extensibility/command-flag-element.md) dans la définition du menu.  
  
8.  Définissez le groupe parent de la commande. Le groupe parent peut être un groupe que vous créez, un groupe d’un autre package ou un groupe de l’IDE. Par exemple, pour ajouter votre commande à la barre d’outils d’édition de Visual Studio, à côté des boutons **Commentaire** et **Supprimer le commentaire** , attribuez au parent la valeur guidStdEditor:IDG_VS_EDITTOOLBAR_COMMENT. Si le parent est un groupe défini par l’utilisateur, il doit être l’enfant d’un menu, d’une barre d’outils ou d’une fenêtre Outil qui apparaît dans l’IDE.  
  
     Pour cela, vous pouvez procéder de deux manières différentes, qui dépendent de votre conception :  
  
    -   Dans l’élément `Button` , créez un élément [Parent](../extensibility/parent-element.md) et attribuez à ses champs `guid` et `id` la valeur de Guid et d’ID du groupe appelé à héberger la commande, aussi appelé *groupe parent principal*.  
  
         L’exemple suivant définit une commande destinée à figurer dans un menu défini par l’utilisateur.  
  
        ```xml
        <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
          <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
          <Icon guid="guidImages" id="bmpPic1" />
          <Strings>
            <CommandName>cmdidTestCommand</CommandName>
            <ButtonText>Test Command</ButtonText>
              </Strings>
        </Button>
        ```
      
    -   Vous pouvez omettre l’élément `Parent` si la commande doit être positionnée en utilisant le placement de commande. Créez un élément [CommandPlacements](../extensibility/commandplacements-element.md) avant la section `Symbols` , puis ajoutez un élément [CommandPlacement](../extensibility/commandplacement-element.md) ayant le `guid` et l’ `id` de la commande, une priorité ( `priority`) et un parent, comme l’illustre l’exemple suivant.  
  
    ```xml
    <CommandPlacements>
      <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
        <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
      </CommandPlacement>
    </CommandPlacements>
    ```
      
         Creating multiple command placements that have the same GUID:ID and have different parents causes a menu to appear in multiple locations. For more information, see [CommandPlacements](../extensibility/commandplacements-element.md) element.  
  
     Pour plus d’informations sur les groupes de commandes et le parentage, consultez [création de groupes réutilisable de boutons](../extensibility/creating-reusable-groups-of-buttons.md).  
  
 À ce stade, la commande est visible dans l’IDE, mais elle n’a aucune fonctionnalité. Si la commande a été créée par le modèle de package, par défaut, elle a un gestionnaire de clics qui affiche un message.  
  
## <a name="handling-the-new-command"></a>Gestion de la nouvelle commande  
 La plupart des commandes présentes dans du code managé peuvent être gérées par MPF (Managed Package Framework) en les associant à un objet <xref:System.ComponentModel.Design.MenuCommand> ou <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> et en implémentant leurs gestionnaires d’événements.  
  
 Pour le code qui utilise directement l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour la gestion des commandes, vous devez implémenter l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> et ses méthodes. Les deux méthodes les plus importants sont <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>.  
  
1.  Obtenez l’instance de <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> , comme le montre l’exemple suivant.  
  
     [!code-csharp[ButtonGroup#21](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#21)]  
  
2.  Créez un objet <xref:System.ComponentModel.Design.CommandID> ayant pour paramètres le GUID et l’ID de la commande à gérer, comme le montre l’exemple suivant.  
  
     [!code-csharp[ButtonGroup#22](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#22)]  
  
     Le modèle de package Visual Studio fournit deux collections, `GuidList` et `PkgCmdIDList`, pour conserver les GUID et ID de commandes. Ceux-ci sont remplis automatiquement pour les commandes ajoutées par le modèle. En revanche, pour les commandes que vous ajoutez manuellement, vous devez aussi ajouter l’entrée d’ID à la classe `PkgCmdIdList` .  
  
     Une autre solution consiste à remplir l’objet <xref:System.ComponentModel.Design.CommandID> en utilisant la valeur de chaîne brute du GUID et la valeur entière de l’ID.  
  
3.  Instanciez un objet <xref:System.ComponentModel.Design.MenuCommand> ou <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> qui spécifie la méthode chargée de gérer la commande en même temps que le <xref:System.ComponentModel.Design.CommandID>, comme l’illustre l’exemple suivant.  
  
     [!code-csharp[ButtonGroup#23](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#23)]  
  
     L’objet <xref:System.ComponentModel.Design.MenuCommand> est tout indiqué pour les commandes statiques. L’affichage des éléments de menu dynamique nécessite des gestionnaires d’événements QueryStatus. L’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ajoute l’événement <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> , qui se produit quand le menu hôte de la commande est ouvert, ainsi que d’autres propriétés, telles que <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Les commandes créées par le modèle de package sont passés par défaut à un objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> dans la méthode `Initialize()` de la classe de package.  
  
4.  L’objet <xref:System.ComponentModel.Design.MenuCommand> est tout indiqué pour les commandes statiques. L’affichage des éléments de menu dynamique nécessite des gestionnaires d’événements QueryStatus. L’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ajoute l’événement <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> , qui se produit quand le menu hôte de la commande est ouvert, ainsi que d’autres propriétés, telles que <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A>.  
  
     Les commandes créées par le modèle de package sont passés par défaut à un objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> dans la méthode `Initialize()` de la classe de package. L’Assistant de Visual Studio implémente la méthode `Initialize` en utilisant `MenuCommand`. Pour l’affichage des éléments de menu dynamique, vous devez remplacer ce dernier par `OleMenuCommand`, comme indiqué dans l’étape suivante. De plus, pour modifier le texte d’un élément de menu, vous devez ajouter un indicateur de commande TextChanges au bouton de commande de menu dans le fichier .vsct, comme le montre l’exemple suivant.  
  
    ```xml
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
      
5.  Passez la nouvelle commande de menu à la méthode <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> de l’interface <xref:System.ComponentModel.Design.IMenuCommandService> . Cette tâche s’exécute par défaut pour les commandes créées par le modèle de package, comme l’illustre l’exemple suivant.  
  
     [!code-csharp[ButtonGroup#24](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#24)]  
  
6.  Implémentez la méthode qui gère la commande.  
  
#### <a name="to-implement-querystatus"></a>Pour implémenter QueryStatus  
  
1.  L’événement QueryStatus se produit avant l’affichage d’une commande. Les propriétés de cette commande peuvent ainsi être définies dans le gestionnaire d’événements avant d’atteindre l’utilisateur. Seules les commandes ajoutées en tant qu’objets <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> peuvent accéder à cette méthode.  
  
     Ajoutez un objet `EventHandler` à l’événement <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> de l’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> qui est créé pour gérer la commande, comme le montre l’exemple suivant (`menuItem` est l’instance de <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ).  
  
     [!code-csharp[MenuText#14](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#14)]
     [!code-vb[MenuText#14](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#14)]  
  
     L’objet `EventHandler` se voit attribuer le nom d’une méthode qui est appelée quand l’état de la commande de menu est demandé.  
  
2.  Implémentez la méthode de gestionnaire de demande d’état pour la commande. Le paramètre `object` `sender` peut faire l’objet d’une conversion de type (transtypage) et être converti en objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> , qui sert à définir les différents attributs de la commande de menu, y compris le texte. Le tableau suivant présente les propriétés de la classe <xref:System.ComponentModel.Design.MenuCommand> (dont est dérivée la classe MPF <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> ) qui correspondent aux indicateurs <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> .  
  
    |Propriété MenuCommand|Indicateur OLECMDF|  
    |--------------------------|------------------|  
    |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
    |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
     Pour modifier le texte d’une commande de menu, utilisez la propriété <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> de l’objet <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> , comme l’illustre l’exemple suivant.  
  
     [!code-csharp[MenuText#11](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#11)]
     [!code-vb[MenuText#11](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#11)]  
  
 MPF gère automatiquement le cas des groupes non pris en charge ou inconnus. À moins qu’une commande ait été ajoutée à <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> à l’aide de la méthode <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> , la commande n’est pas prise en charge.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>Gestion des commandes à l’aide de l’interface IOleCommandTarget  
 Pour le code qui utilise directement l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , le VSPackage doit implémenter les méthodes <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> de l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> . Si le VSPackage implémente une hiérarchie de projet, les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> doivent être implémentées à leur place.  
  
 Les méthodes <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> ont toutes deux été conçues pour recevoir un seul `GUID` de jeu de commandes et un tableau d’ID de commandes en entrée. Il est préférable que les VSPackages prennent entièrement en charge ce concept d’ID multiples dans un même appel. Cependant, tant qu’un VSPackage n’est pas appelé à partir d’autres packages VS, vous pouvez considérer que le tableau de commandes ne contient qu’un seul ID de commande, car les méthodes <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> et <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> sont exécutées dans un ordre bien défini. Pour plus d’informations sur le routage, consultez [routage des commandes dans VSPackages](../extensibility/internals/command-routing-in-vspackages.md).  
  
 Pour le code qui utilise directement l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour la gestion des commandes, vous devez implémenter la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> dans le VSPackage comme indiqué ci-dessous pour gérer les commandes.  
  
##### <a name="to-implement-the-querystatus-method"></a>Pour implémenter la méthode QueryStatus  
  
1.  Retournez <xref:Microsoft.VisualStudio.VSConstants.S_OK> pour les commandes valides.  
  
2.  Définissez l’élément `cmdf` du paramètre `prgCmds`.  
  
     La valeur de l’élément `cmdf` est l’union logique des valeurs de l’énumération <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> , combinées à l’aide de l’opérateur logique OR (`|`).  
  
     Utilisez l’énumération appropriée, en fonction de l’état de la commande :  
  
    -   Si la commande est prise en charge :  
  
         `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
    -   Si la commande doit être invisible pour le moment :  
  
         `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
    -   Si la commande est activée et que l’utilisateur a cliqué dessus :  
  
         `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
         Dans le cas du traitement de commandes hébergées dans un menu de type `MenuControllerLatched`, la première commande à être marquée par l’indicateur `OLECMDF_LATCHED` est la commande par défaut que le menu affiche au démarrage. Pour plus d’informations sur les `MenuController` types de menus, consultez [Menu Element](../extensibility/menu-element.md).  
  
    -   Si la commande est actuellement activée :  
  
         `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
    -   Si la commande fait partie d’un menu contextuel et est masquée par défaut :  
  
         `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
    -   Si la commande utilise l’indicateur `TEXTCHANGES`, affectez à l’élément `rgwz` du paramètre `pCmdText` le nouveau texte de la commande et affectez à l’élément `cwActual` du paramètre `pCmdText` la taille de la chaîne de commande.  
  
     Pour les conditions d’erreur, la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> doit gérer les cas d’erreur suivants :  
  
    -   Si le GUID est inconnu ou non pris en charge, retournez `OLECMDERR_E_UNKNOWNGROUP`.  
  
    -   Si le GUID est connu, mais que l’ID de commande est inconnu ou non pris en charge, retournez `OLECMDERR_E_NOTSUPPORTED`.  
  
 L’implémentation VSPackage de la méthode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> doit aussi retourner des codes d’erreur spécifiques, selon que la commande est prise en charge et qu’elle a été gérée correctement.  
  
##### <a name="to-implement-the-exec-method"></a>Pour implémenter la méthode Exec  
  
-   Si la commande `GUID` est inconnue, retournez `OLECMDERR_E_UNKNOWNGROUP`.  
  
-   Si le `GUID` est connu, mais que l’ID de commande est inconnu, retournez `OLECMDERR_E_NOTSUPPORTED`.  
  
-   Si le `GUID` et l’ID de commande correspond à la paire GUID:ID utilisée par la commande dans le fichier .vsct, exécutez le code associé à la commande et retournez <xref:Microsoft.VisualStudio.VSConstants.S_OK>.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence du schéma XML VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)