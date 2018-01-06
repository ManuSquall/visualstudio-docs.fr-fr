---
title: "Ajout d’une barre d’outils à une fenêtre outil | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: "48"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 07b5eea4fe6d5f58ec4b05563af253aeef0c5f6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Ajout d’une barre d’outils à une fenêtre outil
Cette procédure pas à pas montre comment ajouter une barre d’outils à une fenêtre outil.  
  
 Une barre d’outils est une barre horizontale ou verticale qui contient les boutons liés à des commandes. La longueur d’une barre d’outils dans une fenêtre outil est toujours identique à la largeur ou hauteur de la fenêtre outil, selon l’endroit où la barre d’outils est ancrée.  
  
 Contrairement aux barres d’outils dans l’IDE, une barre d’outils dans une fenêtre outil doit être ancré et ne peut pas être déplacé ou personnalisé. Si le VSPackage est écrit dans le code umanaged, la barre d’outils peut être ancrée sur le bord.  
  
 Pour plus d’informations sur l’ajout d’une barre d’outils, consultez [Ajout d’une barre d’outils](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Création d’une barre d’outils pour une fenêtre outil  
  
1.  Créez un projet VSIX nommé `TWToolbar` qui possède à la fois une commande de menu nommée **TWTestCommand** et une fenêtre Outil nommée **TestToolWindow**. Pour plus d’informations, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md) et [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md). Vous devez ajouter le modèle d’élément de commande avant d’ajouter le modèle de fenêtre outil.  
  
2.  Dans TWTestCommandPackage.vsct, recherchez la section de symboles. Dans le nœud GuidSymbol nommé guidTWTestCommandPackageCmdSet déclarer une barre d’outils et d’un groupe de la barre d’outils, comme suit.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  En haut de la `Commands` en créant un `Menus` section. Ajouter un `Menu` élément pour définir la barre d’outils.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Barres d’outils ne peuvent pas être imbriqués comme des sous-menus. Par conséquent, vous n’avez pas à affecter un parent. En outre, il est inutile définir une priorité, car l’utilisateur peut déplacer des barres d’outils. En règle générale, la sélection élective initiale d’une barre d’outils est définie par programme, mais les modifications ultérieures apportées par l’utilisateur sont conservées.  
  
4.  Dans la section groupes, définir un groupe pour contenir les commandes de la barre d’outils.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  Dans la section de boutons, changer le parent de l’élément bouton existant au groupe de barre d’outils afin que la barre d’outils s’affiche.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Par défaut, si une barre d’outils n’a aucune commande, il n’apparaît pas.  
  
     Étant donné que la nouvelle barre d’outils n’est pas automatiquement ajouté à la fenêtre outil, la barre d’outils doit être ajouté explicitement. Cette situation est présentée dans la section suivante.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Ajout de la barre d’outils à la fenêtre outil  
  
1.  Dans TWTestCommandPackageGuids.cs, ajoutez les lignes suivantes.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  Dans TestToolWindow.cs, ajoutez le code suivant à l’aide d’instruction.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  Dans le constructeur TestToolWindow, ajoutez la ligne suivante.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>La barre d’outils de test dans la fenêtre outil  
  
1.  Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio doit apparaître.  
  
2.  Sur le **affichage / autres fenêtres** menu, cliquez sur **Test ToolWindow** pour afficher la fenêtre outil.  
  
     Vous devez voir une barre d’outils (il ressemble à l’icône par défaut) en haut à gauche de la fenêtre outil, juste en dessous du titre.  
  
3.  Dans la barre d’outils, cliquez sur l’icône pour afficher le message **TWTestCommandPackage dans TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’une barre d’outils](../extensibility/adding-a-toolbar.md)