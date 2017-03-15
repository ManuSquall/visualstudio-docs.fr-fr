---
title: "Raccourcis clavier de la liaison aux éléments de Menu | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 15
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
ms.openlocfilehash: e75976be74d7d0362102a2cbeb32a85d3e612c67
ms.lasthandoff: 02/22/2017

---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Raccourcis clavier de liaison aux éléments de Menu
Pour lier un raccourci clavier à une commande de menu personnalisés, ajoutez simplement une entrée dans le fichier .vsct pour le package. Cette rubrique explique comment mapper un raccourci clavier à un bouton, un élément de menu ou une commande de barre d’outils et comment appliquer le mappage du clavier dans l’éditeur par défaut ou de limiter à un éditeur personnalisé.  
  
 Pour affecter des raccourcis clavier pour les éléments de menu Visual Studio existants, consultez [identification et personnalisation des raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Choix d’une combinaison de touches  
 De nombreux raccourcis clavier sont déjà utilisés dans Visual Studio. Vous ne devez pas attribuer le même raccourci à plusieurs commandes, car les liaisons en double sont difficiles à détecter et peuvent également provoquer des résultats imprévisibles. Par conséquent, il est judicieux de vérifier la disponibilité d’un raccourci avant de l’affecter.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Pour vérifier la disponibilité d’un raccourci clavier  
  
1.  Dans le **Outils / Options / environnement** fenêtre, sélectionnez **clavier**.  
  
2.  Assurez-vous que **utiliser un nouveau raccourci dans** a **Global**.  
  
3.  Dans le **appuyez sur les touches de raccourci** , tapez le raccourci clavier que vous souhaitez utiliser.  
  
     Si le raccourci est déjà utilisé dans Visual Studio, le **raccourci actuellement utilisé par** zone affiche la commande que le raccourci appelle actuellement.  
  
4.  Essayez différentes combinaisons de touches jusqu'à ce que vous trouviez un qui n’est pas mappé.  
  
    > [!NOTE]
    >  Raccourcis clavier que vous utilisent ALT peuvent ouvrir un menu et exécute pas directement une commande. Par conséquent, le **raccourci actuellement utilisé par** zone peut être vide lorsque vous tapez un raccourci qui inclut ALT. Vous pouvez vérifier que le raccourci n’ouvre pas un menu en fermant le **Options** boîte de dialogue et en appuyant sur les touches.  
  
 La procédure suivante suppose que vous disposez d’un VSPackage existante avec une commande de menu. Si vous avez besoin d’aide pour y parvenir, examinons [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Pour affecter un raccourci clavier à une commande  
  
1.  Ouvrez le fichier .vsct pour votre package.  
  
2.  Créer un vide `<KeyBindings>` section après le `<Commands>` si elle n’est pas déjà présent.  
  
    > [!WARNING]
    >  Pour plus d’informations sur les combinaisons de touches, consultez [Keybinding](../extensibility/keybinding-element.md).  
  
     Dans le `<KeyBindings>` en créant un `<KeyBinding>` entrée.  
  
     Définir le `guid` et `id` des attributs à ceux de la commande que vous souhaitez appeler.  
  
     Définir le `mod1` attribut **contrôle**, **Alt**, ou **MAJ**.  
  
     La section thèmes doit ressembler à ceci :  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 Si votre raccourci clavier requiert plus de deux touches, définir le `mod2` et `key2` les attributs.  
  
 Dans la plupart des situations, **MAJ** ne doit pas être utilisé sans un modificateur deuxième car en appuyant sur déjà provoque la plupart des touches alphanumériques permettant de taper une lettre majuscule ou un symbole.  
  
 Les codes de touche virtuelle permettant d’accéder aux touches spéciales qui n’ont pas un caractère associé, par exemple, les touches de fonction et la **RET** clé. Pour plus d’informations, consultez [Virtual-Key Codes](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Pour rendre la commande disponible dans Visual Studio editor, définissez la `editor` l’attribut `guidVSStd97`.  
  
 Pour rendre la commande disponible uniquement dans un éditeur personnalisé, vous devez définir le `editor` d’attribut pour le nom de l’éditeur personnalisé qui a été généré par le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Package modèle lorsque vous avez créé le VSPackage qui inclut l’éditeur personnalisé. Pour trouver la valeur de nom, recherchez le `<Symbols>` section pour un `<GuidSymbol>` nœud dont `name` attribut se termine par «`editorfactory`. » Il s’agit du nom de l’éditeur personnalisé.  
  
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
 Cet exemple lie le raccourci clavier CTRL + B à une commande nommée `cmdidBold` dans un projet nommé `TestEditor`. La commande est disponible uniquement dans l’éditeur personnalisé et pas dans d’autres éditeurs.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)
