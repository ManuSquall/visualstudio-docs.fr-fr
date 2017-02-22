---
title: "Ajout d&#39;un Menu &#224; la barre de menus de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menus, création de niveau supérieur"
  - "menus de niveau supérieur"
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 51
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 51
---
# Ajout d&#39;un Menu &#224; la barre de menus de Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure pas à pas montre comment ajouter un menu dans la barre de menus de l’environnement de développement intégré \(IDE\) Visual Studio. La barre de menus IDE contient des catégories de menu comme **fichier**, **Modifier**, **mode**, **fenêtre**, et **aide**.  
  
 Avant d’ajouter un nouveau menu de la barre de menus de Visual Studio, considérez si vos commandes doivent être placées dans un menu existant. Pour plus d’informations sur le placement de la commande, consultez la page [Menus et commandes de Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).  
  
 Menus sont déclarés dans le fichier .vsct du projet. Pour plus d’informations sur les menus et les fichiers .vsct, consultez la page [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 À la fin de cette procédure pas à pas, vous pouvez créer un menu nommé **TestMenu** qui contient une seule commande.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Création d’un projet VSIX qui a un modèle d’élément commande personnalisée  
  
1.  Créez un projet VSIX nommé `TopLevelMenu`. Vous pouvez trouver le modèle de projet VSIX dans le **Nouveau projet** boîte de dialogue sous **Visual C\#** \/ **extensibilité**.  Pour plus d'informations, consultez [Création d'une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Lorsque le projet s’ouvre, ajoutez un modèle d’élément commande personnalisée nommé **TestCommand**. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Dans le **Ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C\# \/ extensibilité** et sélectionnez **personnalisée**. Dans le **nom** en bas de la fenêtre, modifiez le nom du fichier de commandes **TestCommand.cs**.  
  
## Création d’un Menu dans la barre de menus IDE  
  
#### Pour créer un menu  
  
1.  Dans **l’Explorateur de solutions**, ouvrez TestCommandPackage.vsct.  
  
     À la fin du fichier, il existe un nœud \< symboles \> qui contient plusieurs nœuds \< GuidSymbol \>. Dans le nœud nommé guidTestCommandPackageCmdSet, ajoutez un nouveau symbole, comme suit :  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  Créer un nœud \< Menus \> vide dans le nœud \< commandes \>, juste avant \< groupes \>. Dans le nœud \< Menus \>, ajoutez un nœud \< Menu \>, comme suit :  
  
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
  
     Le `guid` et `id` les valeurs du parent positionnement le menu dans la section de la barre de menus de Visual Studio qui contient des menus Outils et compléments.  
  
     La valeur de la `CommandName` chaîne indique que le texte doit apparaître dans l’élément de menu.  
  
3.  Dans la section \< groupes \>, \< groupe \> et modifiez l’élément \< Parent \> pour pointer vers le menu, que nous avons ajouté :  
  
    ```c#  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     Cela rend la partie du groupe du nouveau menu.  
  
4.  Rechercher les `Buttons` section. Notez que la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de Package a généré un `Button` élément avec son parent, la valeur `MyMenuGroup`. Par conséquent, cette commande apparaîtra dans le menu.  
  
## Création et test de l’Extension  
  
1.  Générez le projet et commencez le débogage. Une instance de l’instance expérimentale doit apparaître.  
  
2.  La barre de menus dans l’instance expérimentale doit contenir un **TestMenu** menu.  
  
3.  Sur le **TestMenu** menu, cliquez sur **appeler une commande de Test**.  
  
     Une boîte de message doit apparaître et afficher le message « TestCommand Package à l’intérieur de TopLevelMenu.TestCommand.MenuItemCallback\(\) ». Cela indique que la nouvelle commande fonctionne.  
  
## Voir aussi  
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)