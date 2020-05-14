---
title: Ajout d’un menu au Visual Studio Menu Bar (fr) Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740314"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Ajoutez un menu au menu Visual Studio bar

Ce pas-là montre comment ajouter un menu à la barre de menu de l’environnement de développement intégré Visual Studio (IDE). La barre de menu IDE contient des catégories de menu telles que **File**, **Edit**, **View**, **Window**, et **Help**.

Avant d’ajouter un nouveau menu au menu Visual Studio, pensez si vos commandes doivent être placées dans un menu existant. Pour plus d’informations sur le placement de commande, voir [Menus et commandes pour Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Les menus sont déclarés dans le fichier *.vsct* du projet. Pour plus d’informations sur les menus et les fichiers *.vsct,* voir [commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md).

En complétant cette procédure pas à pas, vous pouvez créer un menu nommé **TestMenu** qui contient une commande.

> [!NOTE]
> En VS 2019, les menus de haut niveau cotis par extensions sont placés sous le menu **Extensions.**

## <a name="prerequisites"></a>Prérequis

A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Créez un projet VSIX qui a un modèle d’élément de commande personnalisé

1. Créer un projet `TopLevelMenu`VSIX nommé . Vous pouvez trouver le modèle de projet VSIX dans le dialogue **du nouveau projet** en recherchant "vsix".  Pour plus d’informations, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé nommé **TestCommand**. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** >  **un nouvel article**. Dans le dialogue **Add New Item,** rendez-vous sur **Visual C / Extensibility** et **sélectionnez Custom Command**. Dans le champ **nom** au bas de la fenêtre, changez le nom du fichier de commande pour *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Créez un menu sur la barre de menu IDE

::: moniker range="vs-2017"

1. Dans **Solution Explorer**, ouvert *TestCommandPackage.vsct*.

    À la fin du fichier, \<il y a un \<nœud de> de symboles qui contient plusieurs nœuds> GuidSymbol. Dans le nœud nommé guidTestCommandPackageCmdSet, ajoutez un nouveau symbole, comme suit :

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Créez un \<nœud de> \<de menus vide dans le \<nœud commands>, juste avant que les groupes ne>. Dans \<les menus> nœud, \<ajoutez un menu> nœud, comme suit :

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

    Les `guid` `id` valeurs et les valeurs du menu spécifient l’ensemble de commandes et le menu spécifique de l’ensemble de commandes.

    Les `guid` `id` valeurs et les valeurs de la société mère placent le menu sur la section du menu Visual Studio qui contient les menus Outils et Add-ins.

    La valeur `CommandName` de la chaîne spécifie que le texte doit apparaître dans l’élément du menu.

3. Dans \<la section Groupes>, \<trouvez le Groupe> \<et modifiez l’élément Parent> pour indiquer le menu que nous venons d’ajouter :

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Cela fait partie du groupe du nouveau menu.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans **Solution Explorer**, ouvert *TopLevelMenuPackage.vsct*.

    À la fin du fichier, \<il y a un \<nœud de> de symboles qui contient plusieurs nœuds> GuidSymbol. Dans le nœud nommé guidTopLevelMenuPackageCmdSet, ajoutez un nouveau symbole, comme suit :

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Créez un \<nœud de> \<de menus vide dans le \<nœud commands>, juste avant que les groupes ne>. Dans \<les menus> nœud, \<ajoutez un menu> nœud, comme suit :

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    Les `guid` `id` valeurs et les valeurs du menu spécifient l’ensemble de commandes et le menu spécifique de l’ensemble de commandes.

    Les `guid` `id` valeurs et les valeurs de la société mère placent le menu sur la section du menu Visual Studio qui contient les menus Outils et Add-ins.

    La valeur `CommandName` de la chaîne spécifie que le texte doit apparaître dans l’élément du menu.

3. Dans \<la section Groupes>, \<trouvez le Groupe> \<et modifiez l’élément Parent> pour indiquer le menu que nous venons d’ajouter :

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Cela fait partie du groupe du nouveau menu.

::: moniker-end

4. Recherchez la section `Buttons`. Notez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que le modèle `Button` de paquet a `MyMenuGroup`généré un élément qui a son parent fixé à . En conséquence, cette commande apparaît sur votre menu.

## <a name="build-and-test-the-extension"></a>Construire et tester l’extension

1. Générez le projet et commencez le débogage. Un exemple de l’instance expérimentale devrait apparaître.

::: moniker range="vs-2017"

2. La barre de menu dans l’instance expérimentale devrait contenir un menu **TestMenu.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Le menu **Extensions** dans l’instance expérimentale devrait contenir un menu **TestMenu.**

::: moniker-end

3. Sur le menu **TestMenu,** cliquez sur **Invoke Test Command**.

     Une boîte de message doit apparaître et afficher le message "TestCommand Package Inside TopLevelMenu.TestCommand.MenuItemCallback()".

## <a name="see-also"></a>Voir aussi

- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
