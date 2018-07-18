---
title: Ajout d’un Menu à la barre de menus de Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a391da85c38176d79a1c77ce8836ce510e8d27e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103082"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Ajout d’un Menu à la barre de menus de Visual Studio
Cette procédure pas à pas montre comment ajouter un menu dans la barre de menus de l’environnement de développement intégré (IDE) Visual Studio. La barre de menus IDE contient les catégories de menu comme **fichier**, **modifier**, **vue**, **fenêtre**, et **aide** .  
  
 Avant d’ajouter un nouveau menu à la barre de menus de Visual Studio, considérez si vos commandes doivent être placés dans un menu existant. Pour plus d’informations sur le placement de commande, consultez [Menus et commandes de Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Les menus sont déclarés dans le fichier .vsct du projet. Pour plus d’informations sur les menus et les fichiers .vsct, consultez [commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 À la fin de cette procédure pas à pas, vous pouvez créer un menu nommé **TestMenu** qui contient une seule commande.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Création d’un projet VSIX qui a un modèle d’élément de commande personnalisée  
  
1.  Créez un projet VSIX nommé `TopLevelMenu`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual C#** / **extensibilité**.  Pour plus d’informations, consultez [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Lorsque le projet s’ouvre, ajouter un modèle d’élément de commande personnalisée nommé **TestCommand**. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, accédez à **Visual c# / extensibilité** et sélectionnez **commande personnalisée**. Dans le **nom** au bas de la fenêtre, modifiez le nom de fichier de commande pour **TestCommand.cs**.  
  
## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Création d’un Menu dans la barre de menus IDE  
  
#### <a name="to-create-a-menu"></a>Pour créer un menu  
  
1.  Dans **l’Explorateur de solutions**, ouvrez TestCommandPackage.vsct.  
  
     À la fin du fichier, il existe un \<symboles > nœud qui contient plusieurs \<GuidSymbol > nœuds. Dans le nœud nommé guidTestCommandPackageCmdSet, ajoutez un nouveau symbole, comme suit :  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Créer un vide \<Menus > nœud dans le \<commandes > nœud, juste avant \<groupes >. Dans le \<Menus > nœud, ajoutez un \<Menu > nœud, comme suit :  
  
    ```xml  
    <Menus>  
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">  
            <Parent guid="guidSHLMainMenu"  
                    id="IDG_VS_MM_TOOLSADDINS" />  
            <Strings>  
              <ButtonText>TestMenu</ButtonText>  
              <CommandName>TestMenu</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Le `guid` et `id` valeurs du menu spécifient le jeu de commandes et utilisez le menu spécifique dans le jeu de commandes.  
  
     Le `guid` et `id` valeurs du parent positionnement le menu dans la section de la barre de menus de Visual Studio qui contient des menus Outils et compléments.  
  
     La valeur de la `CommandName` chaîne spécifie que le texte doit apparaître dans l’élément de menu.  
  
3.  Dans le \<groupes > section, recherchez la \<groupe > et modifier le \<Parent > élément pointe vers le menu que nous venons d’ajouter :  
  
    ```csharp  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     Cela rend la partie du groupe du nouveau menu.  
  
4.  Rechercher les `Buttons` section. Notez que la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de Package a généré un `Button` élément qui a son parent définie sur `MyMenuGroup`. Par conséquent, cette commande s’affiche dans votre menu.  
  
## <a name="building-and-testing-the-extension"></a>Génération et test de l’Extension  
  
1.  Générez le projet et commencez le débogage. Une instance de l’instance expérimentale doit apparaître.  
  
2.  La barre de menus dans l’instance expérimentale doit contenir un **TestMenu** menu.  
  
3.  Sur le **TestMenu** menu, cliquez sur **appeler une commande de Test**.  
  
     Une boîte de message doit apparaître et afficher le message « TestCommand Package à l’intérieur de TopLevelMenu.TestCommand.MenuItemCallback() ». Cela indique que la nouvelle commande fonctionne.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)