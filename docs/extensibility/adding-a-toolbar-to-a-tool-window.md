---
title: Ajout d’une barre d’outils à une fenêtre outil | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3eefb192c5e0ec660a614af8c32ecc34cc683888
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934425"
---
# <a name="add-a-toolbar-to-a-tool-window"></a>Ajouter une barre d’outils à une fenêtre outil
Cette procédure pas à pas montre comment ajouter une barre d’outils à une fenêtre outil.  
  
 Une barre d’outils est une bande horizontale ou verticale qui contient les boutons liés aux commandes. La longueur d’une barre d’outils dans une fenêtre outil est toujours identique à la largeur ou hauteur de la fenêtre outil, selon l’endroit où la barre d’outils est ancrée.  
  
 Contrairement aux barres d’outils dans l’IDE, une barre d’outils dans une fenêtre outil doit être ancré et ne peut pas être déplacé ou personnalisé. Si le VSPackage est écrit dans le code d’umanaged, la barre d’outils peut être ancré sur n’importe quel bord.  
  
 Pour plus d’informations sur l’ajout d’une barre d’outils, consultez [Ajout d’une barre d’outils](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-toolbar-for-a-tool-window"></a>Créer une barre d’outils pour une fenêtre outil  
  
1.  Créez un projet VSIX nommé `TWToolbar` qui a les deux une commande de menu nommée **TWTestCommand** et une fenêtre Outil nommée **TestToolWindow**. Pour plus d’informations, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md) et [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md). Vous devez ajouter le modèle d’élément commande avant d’ajouter le modèle de fenêtre outil.  
  
2.  Dans *TWTestCommandPackage.vsct*, recherchez la section de symboles. Dans le nœud GuidSymbol guidTWTestCommandPackageCmdSet nommé déclarer une barre d’outils et un groupe de la barre d’outils, comme suit.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  En haut de la `Commands` section, créez un `Menus` section. Ajouter un `Menu` élément pour définir la barre d’outils.  
  
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
  
     Barres d’outils ne peuvent pas être imbriquées telles que des sous-menus. Par conséquent, vous n’êtes pas obligé d’affecter un parent. En outre, il est inutile définir une priorité, car l’utilisateur peut déplacer des barres d’outils. En règle générale, un placement initial d’une barre d’outils est défini par programmation, mais les modifications ultérieures apportées par l’utilisateur sont conservées.  
  
4.  Dans la section groupes, définir un groupe pour qu’il contienne les commandes de la barre d’outils.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  Dans la section boutons, changer le parent de l’élément bouton existant pour le groupe de la barre d’outils afin que la barre d’outils s’affiche.  
  
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
  
## <a name="add-the-toolbar-to-the-tool-window"></a>Ajouter la barre d’outils à la fenêtre outil  
  
1.  Dans *TWTestCommandPackageGuids.cs* ajoutez les lignes suivantes.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  Dans *TestToolWindow.cs* ajoutez le code suivant à l’aide d’instruction.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  Dans le constructeur TestToolWindow, ajoutez la ligne suivante.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="test-the-toolbar-in-the-tool-window"></a>La barre d’outils de test dans la fenêtre outil  
  
1.  Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio doit apparaître.  
  
2.  Sur le **vue / autres Windows** menu, cliquez sur **Test ToolWindow** pour afficher la fenêtre outil.  
  
     Vous devez voir une barre d’outils (il ressemble à l’icône par défaut) en haut à gauche de la fenêtre outil, juste en dessous du titre.  
  
3.  Dans la barre d’outils, cliquez sur l’icône pour afficher le message **TWTestCommandPackage à l’intérieur de TWToolbar.TWTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter une barre d’outils](../extensibility/adding-a-toolbar.md)