---
title: Binding keyboard Shortcuts to Menu Items (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94feafbc614be61aaa4eef9e26669c0fbe901ed5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740023"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Lier les raccourcis clavier aux éléments du menu
Pour lier un raccourci clavier à une commande de menu personnalisée, il suffit d’ajouter une entrée au fichier *.vsct* pour le paquet. Ce sujet explique comment cartographier un raccourci clavier sur un bouton personnalisé, un élément de menu ou une commande de barre d’outils, et comment appliquer la cartographie du clavier dans l’éditeur par défaut ou le limiter à un éditeur personnalisé.

 Pour attribuer des raccourcis clavier aux éléments de menu Visual Studio existants, voir [Identifiez et personnalisez les raccourcis clavier.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

## <a name="choose-a-key-combination"></a>Choisissez une combinaison clé
 De nombreux raccourcis clavier sont déjà utilisés dans Visual Studio. Vous ne devez pas attribuer le même raccourci à plus d’une commande parce que les liaisons en double sont difficiles à détecter et peuvent également causer des résultats imprévisibles. Par conséquent, il est bon de vérifier la disponibilité d’un raccourci avant de l’attribuer.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Pour vérifier la disponibilité d’un raccourci clavier

1. Dans la fenêtre **Tools** > **Options** > **Environment,** sélectionnez **Clavier**.

2. Assurez-vous que **l’utilisation de nouveaux raccourcis** est réglé sur **Global**.

3. Dans la boîte **à touches de raccourci Press,** tapez le raccourci clavier que vous souhaitez utiliser.

    Si le raccourci est déjà utilisé dans Visual Studio, le **raccourci actuellement utilisé par** boîte montrera la commande que le raccourci appelle actuellement.

4. Essayez différentes combinaisons de touches jusqu’à ce que vous trouviez une qui n’est pas cartographiée.

   > [!NOTE]
   > Les raccourcis clavier qui utilisent **Alt** peuvent ouvrir un menu et ne pas exécuter directement une commande. Par conséquent, le **raccourci actuellement utilisé par** boîte peut être vide lorsque vous tapez un raccourci qui comprend **Alt**. Vous pouvez vérifier que le raccourci n’ouvre pas un menu en fermant la boîte de dialogue **Options,** puis en appuyant sur les touches.

   La procédure suivante suppose que vous avez un VSPackage existant avec une commande de menu. Si vous avez besoin d’aide pour ce faire, jetez un oeil à [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Attribuer un raccourci clavier à une commande

1. Ouvrez le fichier *.vsct* pour votre colis.

2. Créez une `<KeyBindings>` section `<Commands>` vide après la si elle n’est pas déjà présente.

   > [!WARNING]
   > Pour plus d’informations sur les liaisons clés, voir [Keybinding](../extensibility/keybinding-element.md).

    Dans `<KeyBindings>` la section, `<KeyBinding>` créez une entrée.

    Définissez `guid` `id` les attributs et les attributs à ceux de la commande que vous souhaitez invoquer.

    Définissez `mod1` l’attribut à **Control**, **Alt**, ou **Shift**.

    La section KeyBindings devrait ressembler à ceci :

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Si votre raccourci clavier nécessite plus de `mod2` `key2` deux touches, définissez le et les attributs.

   Dans la plupart des cas, **Shift** ne doit pas être utilisé sans un deuxième modificateur parce que le pressage provoque déjà la plupart des touches alphanumériques pour taper une lettre de majuscule ou un symbole.

   Les codes à clé virtuelle vous permettent d’accéder à des touches spéciales qui n’ont pas de caractère qui leur est associée, par exemple, les touches de fonction et la clé **Backspace.** Pour plus d’informations, voir [codes clés virtuelles](/windows/desktop/inputdev/virtual-key-codes).

   Pour rendre la commande disponible dans l’éditeur Visual Studio, définissez l’attribut `editor` à `guidVSStd97`.

   Pour rendre la commande disponible uniquement dans `editor` un éditeur personnalisé, définissez l’attribut au nom de l’éditeur personnalisé qui a été généré par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de paquet lorsque vous avez créé le VSPackage qui comprend l’éditeur personnalisé. Pour trouver la valeur du `<Symbols>` nom, `<GuidSymbol>` regardez `name` dans la`editorfactory`section pour un nœud dont l’attribut se termine en "." C’est le nom de l’éditeur personnalisé.

## <a name="example"></a>Exemple
 Cet exemple lie le raccourci clavier **Ctrl**+**Alt**+**C** à une commande nommée `cmdidMyCommand` dans un paquet nommé `MyPackage`.

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example"></a>Exemple
 Cet exemple lie le raccourci clavier **Ctrl**+ `cmdidBold` **B** à une commande nommée dans un projet nommé `TestEditor`. La commande n’est disponible que dans l’éditeur personnalisé et non dans d’autres éditeurs.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Voir aussi
- [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)
