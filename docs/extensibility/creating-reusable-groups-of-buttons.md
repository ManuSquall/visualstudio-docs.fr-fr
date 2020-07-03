---
title: Création de groupes de boutons réutilisables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 477014ed77b60821ad191ba6842999be6f528fee
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903643"
---
# <a name="create-reusable-groups-of-buttons"></a>Créer des groupes de boutons réutilisables
Un groupe de commandes est une collection de commandes qui s’affichent toujours ensemble sur un menu ou une barre d’outils. Tout groupe de commandes peut être réutilisé en l’affectant à différents menus parents dans la section CommandPlacements du fichier *. vsct* .

 Les groupes de commandes contiennent généralement des boutons, mais ils peuvent également contenir d’autres menus ou zones de liste modifiable.

## <a name="to-create-a-reusable-group-of-buttons"></a>Pour créer un groupe de boutons réutilisable

1. Créez un projet VSIX nommé `ReusableButtons` . Pour plus d’informations, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé nommé **ReusableCommand**. Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >  **un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément** , accédez à extensibilité **Visual C#**  >  **Extensibility** et sélectionnez **commande personnalisée**. Dans le champ **nom** en bas de la fenêtre, remplacez le nom du fichier de commandes par *ReusableCommand.cs*.

3. Dans le fichier *. vsct* , accédez à la section symboles et recherchez l’élément GuidSymbol qui contient des groupes et des commandes pour le projet. Il doit être nommé guidReusableCommandPackageCmdSet.

4. Ajoutez un IDSymbol pour chaque bouton que vous ajouterez au groupe, comme dans l’exemple suivant.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Par défaut, le modèle d’élément de commande crée un groupe nommé **MyMenuGroup** et un bouton qui porte le nom que vous avez fourni, ainsi qu’une entrée IDSymbol pour chacun d’entre eux.

5. Dans la section groupes, créez un élément de groupe avec les mêmes attributs GUID et ID que ceux fournis dans la section Symbols. Vous pouvez également utiliser un groupe existant ou l’entrée fournie par le modèle de commande, comme dans l’exemple suivant. Ce groupe apparaît dans le menu **Outils** .

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Pour créer un groupe de boutons à réutiliser

1. Vous pouvez placer une commande ou un menu dans un groupe soit en utilisant le groupe en tant que parent dans la définition de la commande ou du menu, soit en plaçant la commande ou le menu dans le groupe à l’aide de la section CommandPlacements.

     Dans la section boutons, définissez un bouton qui a votre groupe comme parent, ou utilisez le bouton fourni par le modèle de package, comme indiqué dans l’exemple suivant.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Si un bouton doit apparaître dans plusieurs groupes, créez une entrée pour celui-ci dans la section CommandPlacements, qui doit être placée après la section Commands. Définissez les attributs GUID et ID de l’élément Commandplacement ayant pour qu’ils correspondent à ceux du bouton que vous souhaitez positionner, puis définissez le GUID et l’ID de son élément parent sur ceux du groupe cible, comme indiqué dans l’exemple suivant.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > La valeur du champ Priority détermine la position de la commande dans le nouveau groupe de commandes. Les priorités définies dans l’élément Commandplacement ayant remplacent celles définies dans la définition de l’élément. Les commandes qui ont des valeurs de priorité inférieure sont affichées avant les commandes qui ont des valeurs de priorité plus élevée. Les valeurs de priorité en double sont autorisées, mais la position relative des commandes qui ont la même valeur de priorité ne peut pas être garantie, car l’ordre dans lequel la commande **devenv/setup** crée l’interface finale à partir du Registre peut ne pas être cohérent.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Pour placer un groupe de boutons réutilisable dans un menu

1. Créez une entrée dans la `CommandPlacements` section. Définissez le GUID et l’ID de l' `CommandPlacement` élément sur ceux de votre groupe, puis définissez le GUID et l’ID parents sur ceux de l’emplacement cible.

    La section CommandPlacements doit être placée juste après la section commands :

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Un groupe de commandes peut être inclus dans plusieurs menus. Le menu parent peut être celui que vous avez créé, qui est fourni par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (comme décrit dans *ShellCmdDef. vsct* ou *SharedCmdDef. vsct*), ou qui est défini dans un autre VSPackage. Le nombre de couches de parent est illimité tant que le menu parent est finalement connecté à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un menu contextuel qui est affiché par un VSPackage.

    L’exemple suivant place le groupe dans la barre d’outils **Explorateur de solutions** , à droite des autres boutons.

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```
