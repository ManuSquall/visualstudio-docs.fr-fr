---
title: "Cr&#233;ation de groupes de boutons r&#233;utilisables | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "groupes, de création de packages VS"
  - "VSPackages, création de groupes de bouton réutilisables"
  - "boutons, création de groupes réutilisables"
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 44
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 44
---
# Cr&#233;ation de groupes de boutons r&#233;utilisables
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un groupe de commandes est une collection de commandes toujours apparaissent ensemble dans un menu ou une barre d'outils. N'importe quel groupe de commandes nouveau utilisable en l'assignant à menus parents différents dans la section CommandPlacements du fichier .vsct.  
  
 Groupes de commandes contiennent généralement des boutons, mais elles peuvent également contenir des autres menus ou les zones de liste déroulante.  
  
### Pour créer un groupe de boutons réutilisable  
  
1.  Créez un projet VSIX nommé `ReusableButtons`. Pour plus d'informations, consultez [Création d'une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Lorsque le projet s'ouvre, ajoutez un modèle d'élément commande personnalisée nommé **ReusableCommand**. Dans le **l'Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Dans le **Ajouter un nouvel élément** boîte de dialogue, accédez à **Visual C\# \/ extensibilité** et sélectionnez **personnalisée**. Dans le **nom** en bas de la fenêtre, modifiez le nom du fichier de commandes **ReusableCommand.cs**.  
  
3.  Dans le fichier .vsct, consultez la section de symboles et recherchez l'élément GuidSymbol qui contient les groupes et les commandes pour le projet. Il doit être nommé guidReusableCommandPackageCmdSet.  
  
4.  Ajouter un IDSymbol pour chaque bouton que vous ajouterez au groupe, comme dans l'exemple suivant.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}"> <IDSymbol name="MyMenuGroup" value="0x1020" /> <IDSymbol name="ReusableCommandId" value="0x0100" /> <IDSymbol name="SecondReusableCommandId" value="0x0200" /> </GuidSymbol>  
    ```  
  
     Par défaut, le modèle d'élément commande crée un groupe nommé **MyGroup** et un bouton qui porte le nom que vous avez fournies, avec une entrée IDSymbol pour chacun.  
  
5.  Dans la section groupes, créez un élément de groupe qui a les mêmes attributs GUID et l'ID que ceux de la section de symboles. Vous pouvez également utiliser un groupe existant, ou utiliser l'entrée fournie par le modèle de commande, comme dans l'exemple suivant. Ce groupe apparaît sur le **outils** menu  
  
    ```xml  
    <Groups> <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/> </Group> </Groups>  
    ```  
  
### Pour créer un groupe de boutons pour une réutilisation  
  
1.  Vous pouvez placer une commande ou un menu dans un groupe en utilisant le groupe parent dans la définition de la commande ou le menu, soit en plaçant le menu ou la commande dans le groupe à l'aide de la section CommandPlacements.  
  
     Dans la section boutons définir un bouton qui a votre groupe parent, ou utilisez le bouton qui est fourni par le modèle de package, comme illustré dans l'exemple suivant.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> <Icon guid="guidImages" id="bmpPic1" /> <Strings> <ButtonText>Invoke ReusableCommand</ButtonText> </Strings> </Button>  
    ```  
  
2.  Si un bouton doit apparaître dans plusieurs groupes, créez une entrée dans la section CommandPlacements, qui doit être placée après la section commandes. Définissez les attributs GUID et l'ID de l'élément CommandPlacement pour correspondre à ceux du bouton que vous souhaitez positionner et définissez le GUID et l'ID de son élément Parent à ceux du groupe cible, comme illustré dans l'exemple suivant.  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105"> <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" /> </CommandPlacement> </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  La valeur du champ priorité détermine la position de la commande dans le nouveau groupe de commandes. Les priorités définies dans le CommandPlacement élément remplacent ceux définis dans la définition d'élément. Les commandes qui ont des valeurs de priorité inférieure sont affichées avant les commandes qui ont des valeurs de priorité plus élevées. Valeurs de priorité en double sont autorisés, mais la position relative des commandes qui ont la même valeur de priorité ne peut pas être garantie, car l'ordre dans lequel les **devenv \/setup** commande crée la dernière interface à partir du Registre ne soient pas cohérente.  
  
### Pour placer un groupe de boutons réutilisable dans un menu  
  
1.  Créer une entrée dans la `CommandPlacements` section. Définissez le GUID et l'ID de la `CommandPlacement` élément à ceux de votre groupe et définir le parent GUID et l'ID à ceux de l'emplacement cible.  
  
     La section CommandPlacements doit être placée juste après la section commandes :  
  
    ```xml  
    <CommandTable> ... <Commands>... </Commands> <CommandPlacements>... </CommandPlacements> ... </CommandTable>  
    ```  
  
     Un groupe de commandes peut être inclus dans plus d'un menu. Le menu parent peut être une que vous avez créé, qui est fournie par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(comme décrit dans ShellCmdDef.vsct ou SharedCmdDef.vsct\), ou qui est défini dans un autre package VS. Le nombre de couches de parenté est illimité, tant que le menu parent est finalement connecté à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou à un menu contextuel affiché par un VSPackage.  
  
     L'exemple suivant place le groupe le **l'Explorateur de solutions** barre d'outils, à droite des autres boutons.  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/> </CommandPlacement> </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements> <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup" priority="0x605"> <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" /> </CommandPlacement> </CommandPlacements>  
  
    ```