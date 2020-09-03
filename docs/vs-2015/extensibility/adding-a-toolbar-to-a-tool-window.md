---
title: Ajout d’une barre d’outils à une fenêtre outil | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 49
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c5df1ce1721c63b5c5cfc3c5b94929da088660f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184877"
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Ajout d’une barre d’outils à une fenêtre d’outil
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas montre comment ajouter une barre d’outils à une fenêtre outil.  
  
 Une barre d’outils est une bande horizontale ou verticale qui contient des boutons liés à des commandes. La longueur d’une barre d’outils dans une fenêtre outil est toujours la même que la largeur ou la hauteur de la fenêtre outil, selon l’emplacement où la barre d’outils est ancrée.  
  
 Contrairement aux barres d’outils de l’IDE, une barre d’outils dans une fenêtre outil doit être ancrée et ne peut pas être déplacée ou personnalisée. Si le VSPackage est écrit en code umanaged, la barre d’outils peut être ancrée sur n’importe quel bord.  
  
 Pour plus d’informations sur l’ajout d’une barre d’outils, consultez [Ajout d’une barre d’outils](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Création d’une barre d’outils pour une fenêtre outil  
  
1. Créez un projet VSIX nommé `TWToolbar` qui a à la fois une commande de menu nommée **TWTestCommand** et une fenêtre outil nommée **TestToolWindow**. Pour plus d’informations, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md) et [création d’une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md). Vous devez ajouter le modèle d’élément de commande avant d’ajouter le modèle de fenêtre outil.  
  
2. Dans TWTestCommandPackage. vsct, recherchez la section Symbols. Dans le nœud GuidSymbol nommé guidTWTestCommandPackageCmdSet, déclarez une barre d’outils et un groupe de barres d’outils, comme suit.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3. En haut de la `Commands` section, créez une `Menus` section. Ajoutez un `Menu` élément pour définir la barre d’outils.  
  
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
  
     Les barres d’outils ne peuvent pas être imbriquées comme des sous-menus. Par conséquent, il n’est pas nécessaire d’assigner un parent. En outre, il n’est pas nécessaire de définir une priorité, car l’utilisateur peut déplacer des barres d’outils. En général, le placement initial d’une barre d’outils est défini par programme, mais les modifications ultérieures de l’utilisateur sont conservées.  
  
4. Dans la section groupes, définissez un groupe qui contiendra les commandes de la barre d’outils.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5. Dans la section Buttons, remplacez le parent de l’élément Button existant par le groupe Toolbar afin que la barre d’outils s’affiche.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Par défaut, si une barre d’outils n’a pas de commande, elle n’apparaît pas.  
  
     Étant donné que la nouvelle barre d’outils n’est pas automatiquement ajoutée à la fenêtre outil, la barre d’outils doit être ajoutée explicitement. Cette situation est présentée dans la section suivante.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Ajout de la barre d’outils à la fenêtre outil  
  
1. Dans TWTestCommandPackageGuids.cs, ajoutez les lignes suivantes.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2. Dans TestToolWindow.cs, ajoutez l’instruction using suivante.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3. Dans le constructeur TestToolWindow, ajoutez la ligne suivante.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>Test de la barre d’outils dans la fenêtre outil  
  
1. Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio doit apparaître.  
  
2. Dans le menu **affichage/autres fenêtres** , cliquez sur **test ToolWindow** pour afficher la fenêtre outil.  
  
     Vous devez voir une barre d’outils (elle ressemble à l’icône par défaut) en haut à gauche de la fenêtre outil, juste en dessous du titre.  
  
3. Dans la barre d’outils, cliquez sur l’icône pour afficher le message **TWTestCommandPackage dans TWToolbar. TWTestCommand. MenuItemCallback ()**.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’une barre d’outils](../extensibility/adding-a-toolbar.md)
