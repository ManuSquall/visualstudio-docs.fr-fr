---
title: Liaison de raccourcis clavier à des éléments de menu | Microsoft Docs
description: Découvrez comment mapper un raccourci clavier dans Visual Studio à un bouton personnalisé, à un élément de menu ou à une commande de barre d’outils pour l’éditeur par défaut ou un éditeur personnalisé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a9591a7412b0bcaf506483a16a6660790df5f40
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900432"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Lier des raccourcis clavier à des éléments de menu
Pour lier un raccourci clavier à une commande de menu personnalisée, ajoutez simplement une entrée au fichier *. vsct* pour le package. Cette rubrique explique comment mapper un raccourci clavier à un bouton personnalisé, à un élément de menu ou à une commande de barre d’outils, et comment appliquer le mappage du clavier dans l’éditeur par défaut ou le limiter à un éditeur personnalisé.

 Pour affecter des raccourcis clavier à des éléments de menu Visual Studio existants, consultez [identifier et personnaliser les raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="choose-a-key-combination"></a>Choisir une combinaison de touches
 De nombreux raccourcis clavier sont déjà utilisés dans Visual Studio. Vous ne devez pas attribuer le même raccourci à plusieurs commandes, car les liaisons dupliquées sont difficiles à détecter et peuvent également entraîner des résultats imprévisibles. Par conséquent, il est judicieux de vérifier la disponibilité d’un raccourci avant de l’affecter.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Pour vérifier la disponibilité d’un raccourci clavier

1. Dans la fenêtre **Outils**  >  **options** d'  >  **environnement** , sélectionnez **clavier**.

2. Assurez-vous que **utiliser le nouveau raccourci dans** a la valeur **Global**.

3. Dans la zone **appuyer sur les touches de raccourci** , tapez le raccourci clavier que vous souhaitez utiliser.

    Si le raccourci est déjà utilisé dans Visual Studio, le **raccourci actuellement utilisé par** la zone affiche la commande que le raccourci appelle actuellement.

4. Essayez différentes combinaisons de clés jusqu’à ce que vous en trouviez une qui n’est pas mappée.

   > [!NOTE]
   > Les raccourcis clavier qui utilisent **ALT** peuvent ouvrir un menu et ne pas exécuter directement une commande. Par conséquent, la zone **raccourci actuellement utilisé par** peut être vide quand vous tapez un raccourci qui comprend **ALT**. Vous pouvez vérifier que le raccourci n’ouvre pas un menu en fermant la boîte de dialogue **options** , puis en appuyant sur les touches.

   La procédure suivante suppose que vous disposez d’un VSPackage existant avec une commande de menu. Si vous avez besoin d’aide, jetez un coup d’œil à la rubrique [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Pour affecter un raccourci clavier à une commande

1. Ouvrez le fichier *. vsct* pour votre package.

2. Crée une `<KeyBindings>` section vide après `<Commands>` si elle n’est pas déjà présente.

   > [!WARNING]
   > Pour plus d’informations sur les combinaisons de touches, consultez [KeyBinding](../extensibility/keybinding-element.md).

    Dans la `<KeyBindings>` section, créez une `<KeyBinding>` entrée.

    Affectez `guid`  les  `id` attributs et à ceux de la commande que vous souhaitez appeler.

    Affectez `mod1` à l’attribut la valeur **Control**, **ALT** ou **Shift**.

    La section KeyBindings doit ressembler à ceci :

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Si votre raccourci clavier nécessite plus de deux clés, définissez les `mod2` `key2` attributs et.

   Dans la plupart des cas, la **touche Maj** ne doit pas être utilisée sans un deuxième modificateur, car l’appui sur celle-ci amène déjà la plupart des touches alphanumériques à taper une lettre majuscule ou un symbole.

   Les codes de clé virtuelle vous permettent d’accéder à des clés spéciales qui n’ont pas de caractère associé, par exemple des touches de fonction et la touche **retour arrière** . Pour plus d’informations, consultez [codes de clé virtuelle](/windows/desktop/inputdev/virtual-key-codes).

   Pour rendre la commande disponible dans l’éditeur Visual Studio, affectez `editor` à l’attribut la valeur `guidVSStd97` .

   Pour que la commande soit disponible uniquement dans un éditeur personnalisé, affectez `editor` à l’attribut le nom de l’éditeur personnalisé qui a été généré par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de package lors de la création du VSPackage qui comprend l’éditeur personnalisé. Pour rechercher la valeur de nom, recherchez dans la `<Symbols>` section un `<GuidSymbol>` nœud dont l' `name` attribut se termine par « `editorfactory` . » Il s’agit du nom de l’éditeur personnalisé.

## <a name="example-1"></a>Exemple 1
 Cet exemple lie le raccourci clavier **CTRL** + **ALT** + **C** à une commande nommée `cmdidMyCommand` dans un package nommé `MyPackage` .

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

## <a name="example-2"></a>Exemple 2
 Cet exemple lie le raccourci clavier **CTRL** + **B** à une commande nommée `cmdidBold` dans un projet nommé `TestEditor` . La commande est disponible uniquement dans l’éditeur personnalisé et non dans d’autres éditeurs.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Voir aussi
- [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)
