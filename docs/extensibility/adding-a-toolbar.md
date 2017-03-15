---
title: "Ajout d’une barre d’outils | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e6b9b6a5ce384112464d0f768c35bf7b5c57a589
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-toolbar"></a>Ajout d’une barre d’outils
Cette procédure pas à pas montre comment ajouter une barre d’outils à l’IDE Visual Studio.  
  
 Une barre d’outils est une barre horizontale ou verticale qui contient les boutons qui sont liés aux commandes. En fonction de son implémentation, une barre d’outils dans l’IDE peut être repositionné, ancrée sur n’importe quel côté de la fenêtre principale de l’IDE ou apportée à rester devant les autres fenêtres.  
  
 En outre, les utilisateurs peuvent ajouter des commandes à une barre d’outils ou les supprimer à partir de celui-ci à l’aide de la **personnaliser** boîte de dialogue. En règle générale, les barres d’outils dans les VSPackages sont personnalisables par l’utilisateur. L’IDE gère toutes les personnalisations et le VSPackage répond aux commandes. Le VSPackage n’a pas de savoir où se trouve physiquement une commande.  
  
 Pour plus d’informations sur les menus, voir [commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-toolbar"></a>Création d’une Extension avec une barre d’outils  
 Créez un projet VSIX nommé `IDEToolbar`. Ajouter un modèle d’élément commande menu nommé **ToolbarTestCommand**. Pour plus d’informations sur la procédure à suivre, consultez [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Création d’une barre d’outils de l’IDE  
  
1.  Dans ToolbarTestCommandPackage.vsct, recherchez la section de symboles. Dans l’élément GuidSymbol nommé guidToolbarTestCommandPackageCmdSet, ajoutez des déclarations pour une barre d’outils et d’un groupe de la barre d’outils, comme suit.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  En haut de la section de commandes, créez une section de Menus. Ajoutez un élément de Menu à la section de Menus pour définir votre barre d’outils.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     Barres d’outils ne peuvent pas être imbriqués comme des sous-menus. Par conséquent, vous n’avez pas affecter un groupe parent. En outre, il est inutile définir une priorité, car l’utilisateur peut déplacer des barres d’outils. Généralement, le placement initial d’une barre d’outils est définie par programme, mais les modifications ultérieures apportées par l’utilisateur sont conservées.  
  
3.  Dans le [groupes](../extensibility/groups-element.md) section, après l’entrée de groupe existante, définissez un [groupe](../extensibility/group-element.md) élément doit contenir les commandes de la barre d’outils.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  Afficher le bouton dans la barre d’outils. Dans la section boutons, remplacez le bloc Parent dans le bouton de la barre d’outils. Le bloc de bouton résultant doit ressembler à ceci :  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Par défaut, si une barre d’outils n’a aucune commande, il n’apparaît pas.  
  
5.  Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.  
  
6.  Avec le bouton droit de la barre de menus de Visual Studio pour obtenir la liste des barres d’outils. Sélectionnez **barre d’outils de Test**.  
  
7.  Vous devez maintenant voir votre barre d’outils sous forme d’icône à droite de l’icône de recherche dans les fichiers. Lorsque vous cliquez sur l’icône, vous devez voir une boîte de message indiquant que le **ToolbarTestCommandPackage. À l’intérieur de IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
