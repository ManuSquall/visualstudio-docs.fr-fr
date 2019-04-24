---
title: 'Procédure : Ajouter une commande au Menu contextuel | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: cd550399-05fc-4dbf-be4c-f5094bb752ce
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7692e418c3e01b89a8dcf775350c062600351ac3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093044"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Procédure : Ajouter une commande au menu contextuel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez ajouter des commandes de menu à votre langage spécifique à un domaine (DSL, Domain-Specific Language) pour que vos utilisateurs puissent effectuer des tâches spécifiques à votre solution DSL. Les commandes apparaissent dans le menu contextuel quand les utilisateurs cliquent avec le bouton droit sur le diagramme. Vous pouvez définir une commande pour qu'elle apparaisse dans le menu uniquement dans des circonstances spécifiques. Par exemple, vous pouvez rendre la commande visible uniquement quand l'utilisateur clique sur des types d'éléments spécifiques ou sur des éléments qui sont dans des états spécifiques.  
  
 En résumé, les étapes sont effectuées dans le projet DslPackage comme suit :  
  
1. [Déclarer la commande dans Commands.VSCT.](#VSCT)  
  
2. [Mettre à jour le numéro de version de package dans Package.tt](#version). Vous devez effectuer cette opération chaque fois que vous modifiez Commands.vsct.  
  
3. [Écrire des méthodes dans la classe CommandSet](#CommandSet) pour rendre la commande visible et pour définir ce que vous voulez la commande à exécuter.  
  
   Pour obtenir des exemples, consultez le [site Web Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).  
  
> [!NOTE]
>  Vous pouvez aussi modifier le comportement de certaines commandes existantes telles que Couper, Coller, Sélectionner tout et Imprimer en substituant des méthodes dans CommandSet.cs. Pour plus d'informations, voir [Procédure : Modifier une commande de Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="defining-a-command-using-mef"></a>Définition d'une commande à l'aide de l'infrastructure MEF  
 L'infrastructure MEF (Managed Extension Framework) fournit une alternative pour la définition de commandes de menu dans le menu de diagramme. Son objectif principal est de faire en sorte qu'une solution DSL puisse être étendue par vous-même ou par d'autres parties. Les utilisateurs peuvent choisir d'installer uniquement la solution DSL ou d'installer à la fois la solution DSL et les extensions. Cependant, l'infrastructure MEF réduit également la charge de travail liée à la définition des commandes de menu contextuel, après le travail initial d'activation de l'infrastructure MEF sur la solution DSL.  
  
 Appliquez la méthode décrite dans cette rubrique dans les cas suivants :  
  
1. Vous souhaitez définir des commandes de menu dans des menus autres que le menu contextuel accessible par un clic droit.  
  
2. Vous souhaitez définir des regroupements spécifiques de commandes dans le menu.  
  
3. Vous ne souhaitez pas que d'autres personnes puissent étendre la solution DSL avec leurs propres commandes.  
  
4. Vous ne souhaitez définir qu'une seule commande.  
  
   Autrement, vous pouvez utiliser la méthode MEF pour définir des commandes. Pour plus d’informations, consultez [étendre votre DSL à l’aide de MEF](../modeling/extend-your-dsl-by-using-mef.md).  
  
## <a name="VSCT"></a> Déclarer la commande dans Commands.VSCT.  
 La déclaration des commandes de menu s'effectue dans DslPackage\Commands.vsct. Ces définitions spécifient les étiquettes des éléments de menu et l'emplacement où est elles apparaissent dans les menus.  
  
 Le fichier que vous modifiez, Commands.vsct, importe les définitions à partir de plusieurs fichiers .h, qui sont trouvent dans le répertoire *chemin d’installation de Visual Studio SDK*\VisualStudioIntegration\Common\Inc. Il comprend également GeneratedVsct.vsct, qui est généré à partir de votre définition DSL.  
  
 Pour plus d’informations sur les fichiers .vsct, consultez [Visual Studio Command Table (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
#### <a name="to-add-the-command"></a>Pour ajouter la commande  
  
1. Dans **l’Explorateur de solutions**, sous le **DslPackage** de projet, ouvrez Commands.vsct.  
  
2. Dans l'élément `Commands`, définissez un ou plusieurs boutons et un groupe. Un *bouton* est un élément dans le menu. Un *groupe* est une section dans le menu. Pour définir ces éléments, ajoutez les éléments suivants :  
  
    ```  
    <!-- Define a group - a section in the menu -->  
    <Groups>  
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">  
        <!-- These symbols are defined in GeneratedVSCT.vsct -->  
        <Parent guid="guidCmdSet" id="menuidContext" />  
      </Group>  
    </Groups>  
    <!-- Define a button - a menu item - inside the Group -->  
    <Buttons>  
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"  
        priority="0x0100" type="Button">  
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>  
        <!-- If you do not want to place the command in your own Group,   
             use Parent guid="guidCmdSet" id="grpidContextMain".  
             These symbols are defined in GeneratedVSCT.vsct -->  
        <CommandFlag>DynamicVisibility</CommandFlag>  
        <Strings>  
          <ButtonText>My Context Menu Command</ButtonText>  
        </Strings>  
      </Button>  
    </Buttons>  
    ```  
  
    > [!NOTE]
    >  Chaque bouton ou groupe est identifié par un GUID et un ID entier. Vous pouvez créer plusieurs groupes et boutons avec le même GUID. Cependant, ils doivent avoir des ID différents. Les noms des GUID et ID sont traduits en GUID réelle et les ID numériques dans le `<Symbols>` nœud.  
  
3. Ajoutez une contrainte de visibilité pour la commande pour qu'elle soit chargée uniquement dans le contexte de votre langage spécifique à un domaine. Pour plus d’informations, consultez [VisibilityConstraints élément](../extensibility/visibilityconstraints-element.md).  
  
     Pour cela, ajoutez les éléments suivants à l'élément `CommandTable` après l'élément `Commands`.  
  
    ```  
    <VisibilityConstraints>  
      <!-- Ensures the command is only loaded for this DSL -->  
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"  
        context="guidEditor"/>  
    </VisibilityConstraints>  
    ```  
  
4. Définissez les noms que vous avez utilisés pour les GUID et les ID. Pour cela, ajoutez un élément `Symbols` dans l'élément `CommandTable` après l'élément `Commands`.  
  
    ```  
    <Symbols>  
      <!-- Substitute a unique GUID for the placeholder: -->  
      <GuidSymbol name="guidCustomMenuCmdSet"  
        value="{00000000-0000-0000-0000-000000000000}" >  
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>  
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>  
      </GuidSymbol>  
    </Symbols>  
    ```  
  
5. Remplacez `{000...000}` par un GUID qui identifie vos groupes et éléments de menu. Pour obtenir un nouveau GUID, utilisez la **créer un GUID** outil sur le **outils** menu.  
  
    > [!NOTE]
    >  Si vous ajoutez d'autres groupes ou éléments de menu, vous pouvez utiliser le même GUID. Cependant, vous devez utiliser de nouvelles valeurs pour `IDSymbols`.  
  
6. Dans le code que vous avez copié à partir de cette procédure, remplacez chaque occurrence des chaînes suivantes par vos propres chaînes :  
  
    - `grpidMyMenuGroup`  
  
    - `cmdidMyContextMenuCommand`  
  
    - `guidCustomMenuCmdSet`  
  
    - `My Context Menu Command`  
  
## <a name="version"></a> Mise à jour la Version du Package dans Package.tt  
 Chaque fois que vous ajoutez ou modifiez une commande, mettez à jour le paramètre `version` de l'objet <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> qui est appliqué à la classe de package avant de publier la nouvelle version de votre langage spécifique à un domaine.  
  
 La classe de package étant définie dans un fichier généré, vous devez mettre à jour l'attribut dans le fichier de modèle de texte qui génère le fichier Package.cs.  
  
#### <a name="to-update-the-packagett-file"></a>Pour mettre à jour le fichier Package.tt  
  
1. Dans **l’Explorateur de solutions**, dans le **DslPackage** de projet, dans le **GeneratedCode** dossier, ouvrez le fichier Package.tt.  
  
2. Recherchez l'attribut `ProvideMenuResource`.  
  
3. Incrémentez le paramètre `version` de l'attribut, qui est le second paramètre. Si vous le souhaitez, vous pouvez écrire le nom du paramètre de manière explicite, pour vous rappeler sa fonction Exemple :  
  
     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`  
  
## <a name="CommandSet"></a> Définir le comportement de la commande  
 Votre solution DSL possède déjà certaines commandes qui sont implémentées dans une classe partielle déclarée dans DslPackage\GeneratedCode\CommandSet.cs. Pour ajouter de nouvelles commandes, vous devez étendre cette classe en créant un fichier qui contient une déclaration partielle de la même classe. Le nom de la classe est généralement  *\<Nom_de_votre_solution_dsl >*`CommandSet`. Il est utile de commencer par vérifier le nom de la classe et inspecter son contenu.  
  
 La classe de jeu de commandes est dérivée de <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.  
  
#### <a name="to-extend-the-commandset-class"></a>Pour étendre la classe CommandSet  
  
1. Dans l'Explorateur de solutions, dans le projet DslPackage, ouvrez le dossier GeneratedCode, puis regardez sous CommandSet.tt et ouvrez son fichier généré CommandSet.cs. Notez l'espace de noms et le nom de la première classe qui y est définie. Par exemple, vous pouvez voir :  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2. Dans **DslPackage**, créez un dossier nommé **Code personnalisé**. Dans ce dossier, créez un nouveau fichier de classe nommé `CommandSet.cs`.  
  
3. Dans le nouveau fichier, écrivez une déclaration partielle dont l'espace de noms et le nom sont les mêmes que ceux de la classe partielle générée. Exemple :  
  
     `namespace Company.Language1 /* Make sure this is correct */`  
  
     `{ internal partial class Language1CommandSet { ...`  
  
     **Remarque** si vous avez utilisé le modèle de classe pour créer le fichier, vous devez corriger l’espace de noms et le nom de classe.  
  
### <a name="extend-the-command-set-class"></a>Étendre la classe de jeu de commandes  
 Votre code de jeu de commandes devra généralement importer les espaces de noms suivants :  
  
```  
using System;  
using System.Collections.Generic;  
using System.ComponentModel.Design;   
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Shell;  
```  
  
 Ajustez l'espace de noms et le nom de la classe pour qu'ils correspondent à ceux mentionnés dans le fichier CommandSet.cs généré :  
  
```  
namespace Company.Language1 /* Make sure this is correct */  
{  
  // Same class as the generated class.  
  internal partial class Language1CommandSet   
  {  
```  
  
 Vous devez définir deux méthodes, une pour déterminer quand la commande sera visible dans le menu contextuel et l'autre pour exécuter la commande. Ces méthodes ne sont pas des substitutions ; au lieu de cela, vous les inscrivez dans une liste de commandes.  
  
### <a name="define-when-the-command-will-be-visible"></a>Définir quand la commande sera visible  
 Pour chaque commande, définissez une méthode `OnStatus...` qui détermine si la commande apparaîtra dans le menu et si elle sera activée ou grisée. Définissez les propriétés `Visible` et `Enabled` de `MenuCommand`, comme illustré dans l'exemple suivant. Cette méthode est appelée pour construire le menu contextuel chaque fois que l'utilisateur clique avec le bouton droit sur le diagramme. Elle doit donc fonctionner rapidement.  
  
 Dans cet exemple, la commande est visible uniquement quand l'utilisateur a sélectionné un type de forme spécifique et elle est activée uniquement quand au moins l'un des éléments sélectionnés est dans un état particulier. L'exemple est basé sur le modèle DSL de diagramme de classe et ClassShape et ModelClass sont des types qui sont définis dans la solution DSL :  
  
```  
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)  
{  
  MenuCommand command = sender as MenuCommand;  
  command.Visible = command.Enabled = false;  
  foreach (object selectedObject in this.CurrentSelection)  
  {  
    ClassShape shape = selectedObject as ClassShape;  
    if (shape != null)  
    {  
      // Visibility depends on what is selected.  
      command.Visible = true;  
      ModelClass element = shape.ModelElement as ModelClass;  
      // Enabled depends on state of selection.  
      if (element != null && element.Comments.Count == 0)  
      {  
        command.Enabled = true;  
        return; // seen enough  
} } } }  
```  
  
 Les fragments suivants sont souvent utiles dans les méthodes OnStatus :  
  
- `this.CurrentSelection`. La forme sur laquelle l'utilisateur a cliqué avec le bouton droit est toujours incluse dans cette liste. Si l'utilisateur clique sur une partie vierge du diagramme, ce dernier est le seul membre de la liste.  
  
- `this.IsDiagramSelected()` - `true` Si l’utilisateur a cliqué sur une partie vide du diagramme.  
  
- `this.IsCurrentDiagramEmpty()`  
  
- `this.IsSingleSelection()` - l'utilisateur n'a pas sélectionné plusieurs objets.  
  
- `this.SingleSelection` - forme ou diagramme sur lequel l'utilisateur a cliqué avec le bouton droit.  
  
- `shape.ModelElement as MyLanguageElement` - élément de modèle représenté par une forme.  
  
  En règle générale, vous devez faire en sorte que la propriété `Visible` dépende de ce qui est sélectionné et que la propriété `Enabled` dépende de l'état des éléments sélectionnés.  
  
  Une méthode OnStatus ne doit pas modifier l'état du magasin.  
  
### <a name="define-what-the-command-does"></a>Définir ce que fait la commande  
 Pour chaque commande, définissez une méthode `OnMenu...` qui exécute l'action requise quand l'utilisateur clique sur la commande de menu.  
  
 Si vous modifiez des éléments de modèle, vous devez le faire dans une transaction. Pour plus d'informations, voir [Procédure : Modifier une commande de Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
 Dans cet exemple, `ClassShape`, `ModelClass` et `Comment` sont des types définis dans la solution DSL, qui est dérivée du modèle DSL de diagramme de classe.  
  
```  
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)  
{  
  MenuCommand command = sender as MenuCommand;  
  Store store = this.CurrentDocData.Store;  
  // Changes to elements and shapes must be performed in a Transaction.  
  using (Transaction transaction =  
       store.TransactionManager.BeginTransaction("My command"))  
  {  
    foreach (object selectedObject in this.CurrentSelection)  
    {  
      // ClassShape is defined in my DSL.  
      ClassShape shape = selectedObject as ClassShape;  
      if (shape != null)  
      {  
        // ModelClass is defined in my DSL.  
        ModelClass element = shape.ModelElement as ModelClass;  
        if (element != null)  
        {  
          // Do required action here - for example:  
  
          // Create a new element. Comment is defined in my DSL.  
          Comment newComment = new Comment(element.Partition);  
          // Every element must be the target of an embedding link.  
          element.ModelRoot.Comments.Add(newComment);  
          // Set properties of new element.  
          newComment.Text = "This is a comment";  
          // Create a reference link to existing object.  
          element.Comments.Add(newComment);  
        }  
      }  
    }  
    transaction.Commit(); // Don't forget this!  
  }  
}  
```  
  
 Pour plus d’informations sur la façon de naviguer d’un objet à l’objet dans le modèle et sur la création des objets et des liens, consultez [Comment : Modifier une commande de Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
### <a name="register-the-command"></a>Inscrire la commande  
 Répétez en C# les déclarations des valeurs de GUID et d'ID que vous avez effectuées dans la section Symbols de CommandSet.vsct :  
  
```  
private Guid guidCustomMenuCmdSet =   
    new Guid("00000000-0000-0000-0000-000000000000");  
private const int grpidMyMenuGroup = 0x01001;  
private const int cmdidMyContextMenuCommand = 1;  
```  
  
 Utilisez la même valeur GUID que vous avez inséré dans **Commands.vsct**.  
  
> [!NOTE]
>  Si vous modifiez la section Symbols du fichier VSCT, vous devez aussi modifier ces déclarations pour qu'elles correspondent. Vous devez également incrémenter le numéro de version dans Package.tt.  
  
 Inscrivez vos commandes de menu dans le cadre de ce jeu de commandes. `GetMenuCommands()` est appelée une fois le diagramme initialisé :  
  
```  
protected override IList<MenuCommand> GetMenuCommands()  
{  
  // Get the list of generated commands.  
  IList<MenuCommand> commands = base.GetMenuCommands();  
  // Add a custom command:  
  DynamicStatusMenuCommand myContextMenuCommand =  
    new DynamicStatusMenuCommand(  
      new EventHandler(OnStatusMyContextMenuCommand),  
      new EventHandler(OnMenuMyContextMenuCommand),  
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));  
  commands.Add(myContextMenuCommand);  
  // Add more commands here.  
  return commands;  
}   
```  
  
## <a name="test-the-command"></a>Tester la commande  
 Générez et exécutez la solution DSL dans une instance expérimentale de Visual Studio. La commande doit apparaître dans le menu contextuel dans les situations que vous avez spécifiées.  
  
#### <a name="to-exercise-the-command"></a>Pour exercer la commande  
  
1. Sur le **l’Explorateur de solutions** barre d’outils, cliquez sur **transformer tous les modèles**.  
  
2. Appuyez sur **F5** pour régénérer la solution et démarrer le débogage de la langue spécifique à un domaine dans la build expérimentale.  
  
3. Dans la build expérimentale, ouvrez un exemple de diagramme.  
  
4. Cliquez avec le bouton droit sur différents éléments du diagramme pour vérifier que la commande est activée ou désactivée correctement et affichée ou masquée de manière appropriée, en fonction de l'élément sélectionné.  
  
## <a name="troubleshooting"></a>Résolution des problèmes  
 **Commande n’apparaît pas dans le menu :**  
  
- La commande apparaît uniquement dans les instances de débogage de Visual Studio jusqu'à ce que vous installiez le package DSL. Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).  
  
- Assurez-vous que votre exemple expérimental a l'extension de nom de fichier correcte pour cette solution DSL. Pour vérifier l'extension de nom de fichier, ouvrez DslDefinition.dsl dans l'instance principale de Visual Studio. Ensuite, dans l'Explorateur DSL, cliquez avec le bouton droit sur le nœud Éditeur, puis cliquez sur Propriétés. Dans la fenêtre Propriétés, examinez la propriété FileExtension.  
  
- Avez-vous [incrémenter le numéro de version de package](#version)?  
  
- Définissez un point d'arrêt au début de votre méthode OnStatus. Elle doit s'arrêter quand vous cliquez avec le bouton droit sur une partie quelconque du diagramme.  
  
   **Méthode OnStatus n’est pas appelée**:  
  
  - Assurez-vous que les GUID et les ID dans votre code CommandSet correspondent à ceux de la section Symbols de Commands.vsct.  
  
  - Dans Commands.vsct, assurez-vous que le GUID et l'ID dans chaque nœud Parent identifient le groupe parent correct.  
  
  - Dans une invite de commandes Visual Studio, tapez devenv /rootsuffix exp /setup. Ensuite, redémarrez l'instance de débogage de Visual Studio.  
  
- Parcourez la méthode OnStatus pour vérifier que command.Visible et command.Enabled ont la valeur True.  
  
  **Menu incorrect apparaît ou la commande apparaît au mauvais endroit**:  
  
- Assurez-vous que la combinaison de GUID et ID est unique à cette commande.  
  
- Assurez-vous d'avoir désinstallé les versions antérieures du package.  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Guide pratique pour Modifier une commande de Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)   
 [Déploiement de Solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md)   
 [Exemple de code : Diagrammes de circuit](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
