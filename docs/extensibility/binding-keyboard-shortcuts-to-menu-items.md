---
title: Raccourcis clavier de la liaison aux éléments de Menu | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db02cf763ee4bf171d862129c88687accab00cc4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103355"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Raccourcis clavier de liaison aux éléments de Menu
Pour lier un raccourci clavier à une commande de menu personnalisés, ajoutez simplement une entrée dans le fichier .vsct pour le package. Cette rubrique explique comment mapper un raccourci clavier pour un bouton personnalisé, un élément de menu ou une commande de barre d’outils et comment appliquer le mappage du clavier dans l’éditeur par défaut ou de limiter à un éditeur personnalisé.  
  
 Pour affecter des raccourcis clavier pour les éléments de menu Visual Studio existants, consultez [identification et personnalisation des raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Choix d’une combinaison de touches  
 De nombreux raccourcis clavier sont déjà utilisés dans Visual Studio. Vous ne devez pas attribuer le même raccourci à plusieurs commandes, car les liaisons en double sont difficiles à détecter et peuvent également provoquer des résultats imprévisibles. Par conséquent, il est judicieux de vérifier la disponibilité d’un raccourci avant de l’affecter.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Pour vérifier la disponibilité d’un raccourci clavier  
  
1.  Dans le **Outils / Options / environnement** fenêtre, sélectionnez **clavier**.  
  
2.  Assurez-vous que **utiliser un nouveau raccourci dans** a la valeur **Global**.  
  
3.  Dans le **appuyez sur les touches de raccourci** , tapez le raccourci clavier que vous souhaitez utiliser.  
  
     Si le raccourci est déjà utilisé dans Visual Studio, le **raccourci actuellement utilisé par** zone affiche la commande de raccourci appelle actuellement.  
  
4.  Essayez différentes combinaisons de touches jusqu'à ce que vous trouviez un qui n’est pas mappé.  
  
    > [!NOTE]
    >  Raccourcis clavier que vous utilisent ALT peuvent ouvrir un menu et d’exécuter une commande pas directement. Par conséquent, le **raccourci actuellement utilisé par** zone peut être vide lorsque vous tapez un raccourci qui inclut ALT. Vous pouvez vérifier que le raccourci ne s’ouvre pas un menu en fermant le **Options** boîte de dialogue et en appuyant sur les clés.  
  
 La procédure suivante suppose que vous disposez d’un VSPackage existant avec une commande de menu. Si vous avez besoin d’aide pour y parvenir, examinons [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Pour affecter un raccourci clavier à une commande  
  
1.  Ouvrez le fichier .vsct pour votre package.  
  
2.  Créer un vide `<KeyBindings>` section après le `<Commands>` si elle n’est pas déjà présent.  
  
    > [!WARNING]
    >  Pour plus d’informations sur les combinaisons de touches, consultez [Keybinding](../extensibility/keybinding-element.md).  
  
     Dans le `<KeyBindings>` en créant un `<KeyBinding>` entrée.  
  
     Définir le `guid` et `id` des attributs à celles de la commande que vous souhaitez appeler.  
  
     Définir le `mod1` attribut **contrôle**, **Alt**, ou **MAJ**.  
  
     La section des combinaisons de touches doit ressembler à ceci :  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 Si votre raccourci clavier requiert plus de deux touches, définir le `mod2` et `key2` attributs.  
  
 Dans la plupart des cas, **MAJ** ne doit pas être utilisé sans un modificateur deuxième car en appuyant sur déjà entraîne la plupart des touches alphanumériques permettant de taper une lettre majuscule ou un symbole.  
  
 Les codes de touche virtuelle vous permettent d’accéder à des touches spéciales qui n’ont pas un caractère associé, par exemple, les touches de fonction et la **RET** clé. Pour plus d’informations, consultez [Virtual-Key Codes](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Pour rendre la commande disponible dans Visual Studio éditeur, définissez la `editor` attribut `guidVSStd97`.  
  
 Pour rendre la commande disponible uniquement dans un éditeur personnalisé, définissez la `editor` nom à l’attribut de l’éditeur personnalisé qui a été généré par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modèle de Package lorsque vous avez créé le package Visual Studio qui inclut l’éditeur personnalisé. Pour rechercher la valeur de nom, recherchez dans le `<Symbols>` section pour un `<GuidSymbol>` nœud dont `name` attribut se termine par «`editorfactory`. » Il s’agit du nom de l’éditeur personnalisé.  
  
## <a name="example"></a>Exemple  
 Cet exemple lie le raccourci clavier CTRL + ALT + C à une commande nommée `cmdidMyCommand` dans un package appelé `MyPackage`.  
  
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
 Cet exemple lie le raccourci clavier CTRL + B à une commande nommée `cmdidBold` dans un projet nommé `TestEditor`. La commande est disponible uniquement dans l’éditeur personnalisé et pas d’autres éditeurs.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)