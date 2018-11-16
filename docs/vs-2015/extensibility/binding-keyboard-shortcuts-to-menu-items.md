---
title: Raccourcis clavier de la liaison aux éléments de Menu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5fd5ab9b09956c41620947ad1bcf529550db4aca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752908"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Liaison de raccourcis clavier à des éléments de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour lier un raccourci clavier à une commande de menu personnalisé, ajoutez simplement une entrée dans le fichier .vsct pour le package. Cette rubrique explique comment mapper un raccourci clavier pour un bouton personnalisé, un élément de menu ou une commande de barre d’outils et comment appliquer le mappage du clavier dans l’éditeur par défaut ou de limiter à un éditeur personnalisé.  
  
 Pour affecter des raccourcis clavier aux éléments de menu de Visual Studio existants, consultez [identification et personnalisation des raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Choix d’une combinaison de touches  
 De nombreux raccourcis clavier sont déjà utilisés dans Visual Studio. Vous ne devez pas attribuer le même raccourci à plusieurs commandes, car les liaisons en double sont difficiles à détecter et peuvent également provoquer des résultats imprévisibles. Par conséquent, il est judicieux de vérifier la disponibilité d’un raccourci avant de l’affecter.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Pour vérifier la disponibilité d’un raccourci clavier  
  
1. Dans le **Outils / Options / environnement** fenêtre, sélectionnez **clavier**.  
  
2. Assurez-vous que l’option **utiliser un nouveau raccourci dans** a la valeur **Global**.  
  
3. Dans le **appuyez sur les touches de raccourci** , tapez le raccourci clavier que vous souhaitez utiliser.  
  
    Si le raccourci est déjà utilisé dans Visual Studio, le **raccourci actuellement utilisé par** zone affiche la commande de raccourci appelle actuellement.  
  
4. Essayez différentes combinaisons de touches jusqu'à ce que vous trouvez un qui n’est pas mappé.  
  
   > [!NOTE]
   >  Raccourcis clavier que vous utilisent ALT peuvent ouvrir un menu et n’exécute pas directement une commande. Par conséquent, le **raccourci actuellement utilisé par** zone peut être vide lorsque vous tapez un raccourci qui inclut ALT. Vous pouvez vérifier que le raccourci ne s’ouvre pas un menu en fermant le **Options** boîte de dialogue et en appuyant sur les clés.  
  
   La procédure suivante suppose que vous disposez d’un VSPackage existant avec une commande de menu. Si vous avez besoin d’aide pour y parvenir, jetez un coup de œil à [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Pour affecter un raccourci clavier à une commande  
  
1. Ouvrez le fichier .vsct pour votre package.  
  
2. Créer un vide `<KeyBindings>` section après le `<Commands>` si elle n’est pas déjà présent.  
  
   > [!WARNING]
   >  Pour plus d’informations sur les combinaisons de touches, consultez [Keybinding](../extensibility/keybinding-element.md).  
  
    Dans le `<KeyBindings>` section, créez un `<KeyBinding>` entrée.  
  
    Définir le `guid` et `id` attributs à ceux de la commande que vous souhaitez appeler.  
  
    Définir le `mod1` attribut **contrôle**, **Alt**, ou **MAJ**.  
  
    La section de combinaisons de touches doit ressembler à ceci :  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Si votre raccourci clavier nécessite plus de deux clés, définissez le `mod2` et `key2` attributs.  
  
   Dans la plupart des situations, **MAJ** ne doit pas être utilisé sans un modificateur deuxième car en appuyant sur déjà entraîne la plupart des touches d’alphanumériques à taper une lettre majuscule ou un symbole.  
  
   Codes de touche virtuelle vous permettent d’accéder à des touches spéciales qui n’ont pas un caractère qui s’y rapportent, par exemple, les touches de fonction et le **retour arrière** clé. Pour plus d’informations, consultez [Codes de touche virtuelle](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
   Pour rendre la commande disponible dans Visual Studio éditeur, définissez le `editor` attribut `guidVSStd97`.  
  
   Pour rendre la commande disponible uniquement dans un éditeur personnalisé, définissez la `editor` nom à l’attribut de l’éditeur personnalisé qui a été généré par le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modèle de Package lorsque vous avez créé le package Visual Studio qui inclut l’éditeur personnalisé. La valeur du nom, cherchez dans le `<Symbols>` section pour un `<GuidSymbol>` nœud dont `name` attribut se termine par «`editorfactory`. » Il s’agit du nom de l’éditeur personnalisé.  
  
## <a name="example"></a>Exemple  
 Cet exemple lie le raccourci clavier CTRL + ALT + C à une commande nommée `cmdidMyCommand` dans un package nommé `MyPackage`.  
  
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
 Cet exemple lie le raccourci clavier CTRL + B pour une commande nommée `cmdidBold` dans un projet nommé `TestEditor`. La commande est disponible uniquement dans l’éditeur personnalisé et pas d’autres éditeurs.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)

