---
title: Création de groupes de boutons réutilisables (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739467"
---
# <a name="create-reusable-groups-of-buttons"></a>Créer des groupes réutilisables de boutons
Un groupe de commande est une collection de commandes qui apparaissent toujours ensemble sur un menu ou une barre d’outils. N’importe quel groupe de commande peut être réutiliser en l’assignant à différents menus parentaux dans la section CommandPlacements du fichier *.vsct.*

 Les groupes de commande contiennent généralement des boutons, mais ils peuvent également contenir d’autres menus ou des boîtes combo.

## <a name="to-create-a-reusable-group-of-buttons"></a>Créer un groupe de boutons réutilisables

1. Créer un projet `ReusableButtons`VSIX nommé . Pour plus d’informations, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Lorsque le projet s’ouvre, ajoutez un modèle d’élément de commande personnalisé nommé **ReusableCommand**. Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Dans le dialogue **Add New Item,** rendez-vous sur **Visual C’Extensibility** > **Extensibility** et **sélectionnez Custom Command**. Dans le champ **nom** au bas de la fenêtre, changer le nom du fichier de commande pour *ReusableCommand.cs*.

3. Dans le fichier *.vsct,* allez à la section Symboles et trouvez l’élément GuidSymbol qui contient des groupes et des commandes pour le projet. Il doit être nommé guidReusableCommandPackageCmdSet.

4. Ajoutez un IDSymbol pour chaque bouton que vous ajouterez au groupe, comme dans l’exemple suivant.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Par défaut, le modèle d’élément de commande crée un groupe nommé **MyMenuGroup** et un bouton qui a le nom que vous avez fourni, ainsi qu’une entrée IDSymbol pour chacun.

5. Dans la section Groupes, créez un élément de groupe qui a les mêmes attributs de GUID et d’identification que ceux donnés dans la section Symboles. Vous pouvez également utiliser un groupe existant, ou utiliser l’entrée qui est fournie par le modèle de commande, comme dans l’exemple suivant. Ce groupe apparaît sur le menu **Tools**

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Créer un groupe de boutons pour la réutilisation

1. Vous pouvez mettre une commande ou un menu dans un groupe soit en utilisant le groupe comme parent dans la définition de la commande ou du menu, soit en mettant la commande ou le menu dans le groupe en utilisant la section CommandPlacements.

     Dans la section Boutons, définissez un bouton qui a votre groupe comme parent, ou utilisez le bouton fourni par le modèle de paquet, comme indiqué dans l’exemple suivant.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Si un bouton doit apparaître dans plus d’un groupe, créez une entrée pour elle dans la section CommandPlacements, qui doit être placée après la section Commandes. Définissez les attributs GUID et ID de l’élément CommandPlacement pour correspondre à ceux du bouton que vous souhaitez positionner, puis définissez le GUID et l’ID de son élément Parent à ceux du groupe cible, comme indiqué dans l’exemple suivant.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > La valeur du champ Prioritaire détermine la position du commandant dans le nouveau groupe de commandement. Les priorités définies dans l’élément CommandPlacement l’emportent sur celles définies dans la définition de l’élément. Les commandes dont les valeurs de priorité sont inférieures sont affichées avant les commandes qui ont des valeurs prioritaires plus élevées. Les valeurs prioritaires en double sont autorisées, mais la position relative des commandes qui ont la même valeur prioritaire ne peut être garantie parce que l’ordre dans lequel la commande **devenv/setup** crée l’interface finale du registre peut ne pas être cohérente.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Mettre un groupe de boutons réutilisables sur un menu

1. Créez une entrée `CommandPlacements` dans la section. Définissez le GUID `CommandPlacement` et l’ID de l’élément à ceux de votre groupe, et définissez le GUID et l’ID parent à ceux de l’emplacement cible.

    La section CommandPlacements doit être placée juste après la section Commandes :

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Un groupe de commande peut être inclus sur plus d’un menu. Le menu parent peut être celui que vous [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] avez créé, celui qui est fourni par (comme décrit dans *ShellCmdDef.vsct* ou *SharedCmdDef.vsct*), ou celui qui est défini dans un autre VSPackage. Le nombre de couches parentales est illimité tant que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] le menu parent est éventuellement connecté à ou à un menu raccourci qui est affiché par un VSPackage.

    L’exemple suivant met le groupe sur la barre d’outils **Solution Explorer,** à droite des autres boutons.

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
