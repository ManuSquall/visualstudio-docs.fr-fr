---
title: 'Comment : ajouter une commande au menu contextuel'
description: Découvrez comment vous pouvez ajouter des commandes de menu à votre langage spécifique à un domaine (DSL) afin que vos utilisateurs puissent effectuer des tâches spécifiques à votre DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b578c949b3b5121eb90b2c034766ea15ae6d096
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386564"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Comment : ajouter une commande au menu contextuel

Vous pouvez ajouter des commandes de menu à votre langage spécifique à un domaine (DSL, Domain-Specific Language) pour que vos utilisateurs puissent effectuer des tâches spécifiques à votre solution DSL. Les commandes apparaissent dans le menu contextuel quand les utilisateurs cliquent avec le bouton droit sur le diagramme. Vous pouvez définir une commande pour qu'elle apparaisse dans le menu uniquement dans des circonstances spécifiques. Par exemple, vous pouvez rendre la commande visible uniquement quand l'utilisateur clique sur des types d'éléments spécifiques ou sur des éléments qui sont dans des états spécifiques.

En résumé, les étapes sont effectuées dans le projet DslPackage, comme suit :

1. [Déclarer la commande dans Commands.vsct.](#VSCT)

2. [Mettez à jour le numéro de version du package dans package.TT](#version). Vous devez effectuer cette opération chaque fois que vous modifiez Commands.vsct.

3. [Écrivez des méthodes dans la classe commandSet](#CommandSet) pour rendre la commande visible et pour définir ce que la commande doit faire.

> [!NOTE]
> Vous pouvez aussi modifier le comportement de certaines commandes existantes telles que Couper, Coller, Sélectionner tout et Imprimer en substituant des méthodes dans CommandSet.cs. Pour plus d’informations, consultez [Comment : modifier une commande de menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="define-a-command-using-mef"></a>Définir une commande à l’aide de MEF

L'infrastructure MEF (Managed Extension Framework) fournit une alternative pour la définition de commandes de menu dans le menu de diagramme. Son objectif principal est de faire en sorte qu'une solution DSL puisse être étendue par vous-même ou par d'autres parties. Les utilisateurs peuvent choisir d'installer uniquement la solution DSL ou d'installer à la fois la solution DSL et les extensions. Cependant, l'infrastructure MEF réduit également la charge de travail liée à la définition des commandes de menu contextuel, après le travail initial d'activation de l'infrastructure MEF sur la solution DSL.

Appliquez la méthode décrite dans cette rubrique dans les cas suivants :

1. Vous souhaitez définir des commandes de menu dans des menus autres que le menu contextuel accessible par un clic droit.

2. Vous souhaitez définir des regroupements spécifiques de commandes dans le menu.

3. Vous ne souhaitez pas que d'autres personnes puissent étendre la solution DSL avec leurs propres commandes.

4. Vous ne souhaitez définir qu'une seule commande.

   Autrement, vous pouvez utiliser la méthode MEF pour définir des commandes. Pour plus d’informations, consultez [étendre votre DSL à l’aide de MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="declare-the-command-in-commandsvsct"></a><a name="VSCT"></a> Déclarer la commande dans Commands. vsct
 La déclaration des commandes de menu s'effectue dans DslPackage\Commands.vsct. Ces définitions spécifient les étiquettes des éléments de menu et l'emplacement où est elles apparaissent dans les menus.

 Le fichier que vous modifiez, Commands. vsct, importe les définitions à partir de plusieurs fichiers. h, qui se trouvent dans le répertoire répertoire *d’installation du kit de développement logiciel (SDK) Visual Studio*\VisualStudioIntegration\Common\Inc. Il comprend également GeneratedVsct. vsct, qui est généré à partir de votre définition DSL.

 Pour plus d’informations sur les fichiers. vsct, consultez [table de commandes Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

### <a name="to-add-the-command"></a>Pour ajouter la commande

1. Dans **Explorateur de solutions**, sous le projet **DslPackage** , ouvrez Commands. vsct.

2. Dans l'élément `Commands`, définissez un ou plusieurs boutons et un groupe. Un *bouton* est un élément du menu. Un *groupe* est une section dans le menu. Pour définir ces éléments, ajoutez les éléments suivants :

    ```xml
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
    > Chaque bouton ou groupe est identifié par un GUID et un ID entier. Vous pouvez créer plusieurs groupes et boutons avec le même GUID. Cependant, ils doivent avoir des ID différents. Les noms des GUID et les noms des ID sont traduits en GUID et en ID numériques réels dans le `<Symbols>` nœud.

3. Ajoutez une contrainte de visibilité pour la commande pour qu'elle soit chargée uniquement dans le contexte de votre langage spécifique à un domaine. Pour plus d’informations, consultez [élément VisibilityConstraints](../extensibility/visibilityconstraints-element.md).

     Pour cela, ajoutez les éléments suivants à l'élément `CommandTable` après l'élément `Commands`.

    ```xml
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. Définissez les noms que vous avez utilisés pour les GUID et les ID. Pour cela, ajoutez un élément `Symbols` dans l'élément `CommandTable` après l'élément `Commands`.

    ```xml
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5. Remplacez `{000...000}` par un GUID qui identifie vos groupes et éléments de menu. Pour obtenir un nouveau GUID, utilisez l’outil **créer un GUID** dans le menu **Outils** .

    > [!NOTE]
    > Si vous ajoutez d'autres groupes ou éléments de menu, vous pouvez utiliser le même GUID. Cependant, vous devez utiliser de nouvelles valeurs pour `IDSymbols`.

6. Dans le code que vous avez copié à partir de cette procédure, remplacez chaque occurrence des chaînes suivantes par vos propres chaînes :

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="update-the-package-version-in-packagett"></a><a name="version"></a> Mettre à jour la version du package dans Package.tt
 Chaque fois que vous ajoutez ou modifiez une commande, mettez à jour le paramètre `version` de l'objet <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> qui est appliqué à la classe de package avant de publier la nouvelle version de votre langage spécifique à un domaine.

 La classe de package étant définie dans un fichier généré, vous devez mettre à jour l'attribut dans le fichier de modèle de texte qui génère le fichier Package.cs.

### <a name="to-update-the-packagett-file"></a>Pour mettre à jour le fichier Package.tt

1. Dans **Explorateur de solutions**, dans le projet **DslPackage** , dans le dossier **GeneratedCode** , ouvrez le fichier Package.TT.

2. Recherchez l'attribut `ProvideMenuResource`.

3. Incrémentez le paramètre `version` de l'attribut, qui est le second paramètre. Si vous le souhaitez, vous pouvez écrire le nom du paramètre de manière explicite, pour vous rappeler sa fonction Exemple :

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="define-the-behavior-of-the-command"></a><a name="CommandSet"></a> Définir le comportement de la commande

Votre solution DSL possède déjà certaines commandes qui sont implémentées dans une classe partielle déclarée dans DslPackage\GeneratedCode\CommandSet.cs. Pour ajouter de nouvelles commandes, vous devez étendre cette classe en créant un fichier qui contient une déclaration partielle de la même classe. Le nom de la classe est généralement *\<YourDslName>* `CommandSet` . Il est utile de commencer par vérifier le nom de la classe et d’inspecter son contenu.

La classe de jeu de commandes est dérivée de <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

### <a name="extend-the-commandset-class"></a>Étendre la classe CommandSet

1. Dans l'Explorateur de solutions, dans le projet DslPackage, ouvrez le dossier GeneratedCode, puis regardez sous CommandSet.tt et ouvrez son fichier généré CommandSet.cs. Notez l'espace de noms et le nom de la première classe qui y est définie. Par exemple, vous pouvez voir :

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. Dans **DslPackage**, créez un dossier nommé **code personnalisé**. Dans ce dossier, créez un nouveau fichier de classe nommé `CommandSet.cs` .

3. Dans le nouveau fichier, écrivez une déclaration partielle dont l'espace de noms et le nom sont les mêmes que ceux de la classe partielle générée. Exemple :

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     > [!NOTE]
     > Si vous avez utilisé le modèle de classe pour créer le nouveau fichier, vous devez corriger à la fois l’espace de noms et le nom de la classe.

Votre code de jeu de commandes devra généralement importer les espaces de noms suivants :

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

Ajustez l'espace de noms et le nom de la classe pour qu'ils correspondent à ceux mentionnés dans le fichier CommandSet.cs généré :

```csharp
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

Vous devez définir deux méthodes, une pour déterminer quand la commande sera visible dans le menu contextuel (contexte), et l’autre pour exécuter la commande. Ces méthodes ne sont pas des substitutions ; au lieu de cela, vous les inscrivez dans une liste de commandes.

### <a name="define-when-the-command-will-be-visible"></a>Définir quand la commande sera visible
 Pour chaque commande, définissez une `OnStatus...` méthode qui détermine si la commande s’affichera dans le menu et si elle sera activée ou grisée. Définissez les `Visible` `Enabled` Propriétés et de `MenuCommand` , comme indiqué dans l’exemple suivant. Cette méthode est appelée pour construire le menu contextuel chaque fois que l'utilisateur clique avec le bouton droit sur le diagramme. Elle doit donc fonctionner rapidement.

 Dans cet exemple, la commande est visible uniquement quand l'utilisateur a sélectionné un type de forme spécifique et elle est activée uniquement quand au moins l'un des éléments sélectionnés est dans un état particulier. L'exemple est basé sur le modèle DSL de diagramme de classe et ClassShape et ModelClass sont des types qui sont définis dans la solution DSL :

```csharp
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

- `this.IsSingleSelection()` -l’utilisateur n’a pas sélectionné plusieurs objets

- `this.SingleSelection` -forme ou diagramme sur lequel l’utilisateur a cliqué avec le bouton droit

- `shape.ModelElement as MyLanguageElement` : élément de modèle représenté par une forme.

En règle générale, vous devez faire en sorte que la propriété `Visible` dépende de ce qui est sélectionné et que la propriété `Enabled` dépende de l'état des éléments sélectionnés.

Une méthode OnStatus ne doit pas modifier l'état du magasin.

### <a name="define-what-the-command-does"></a>Définir ce que fait la commande
 Pour chaque commande, définissez une méthode `OnMenu...` qui exécute l'action requise quand l'utilisateur clique sur la commande de menu.

 Si vous modifiez des éléments de modèle, vous devez le faire dans une transaction. Pour plus d’informations, consultez [Comment : modifier une commande de menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 Dans cet exemple, `ClassShape`, `ModelClass` et `Comment` sont des types définis dans la solution DSL, qui est dérivée du modèle DSL de diagramme de classe.

```csharp
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

 Pour plus d’informations sur la façon de naviguer d’un objet à un autre dans le modèle et sur la façon de créer des objets et des liens, consultez [Comment : modifier une commande de menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Inscrire la commande
 Répétez en C# les déclarations des valeurs de GUID et d'ID que vous avez effectuées dans la section Symbols de CommandSet.vsct :

```csharp
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Utilisez la même valeur GUID que celle que vous avez insérée dans **Commands. vsct**.

> [!NOTE]
> Si vous modifiez la section Symbols du fichier VSCT, vous devez aussi modifier ces déclarations pour qu'elles correspondent. Vous devez également incrémenter le numéro de version dans Package.tt.

 Inscrivez vos commandes de menu dans le cadre de ce jeu de commandes. `GetMenuCommands()` est appelée une fois lorsque le diagramme est initialisé :

```csharp
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

### <a name="to-exercise-the-command"></a>Pour exercer la commande

1. Dans la barre d’outils **Explorateur de solutions** , cliquez sur **transformer tous les modèles**.

2. Appuyez sur **F5** pour régénérer la solution, puis démarrez le débogage du langage spécifique à un domaine dans la build expérimentale.

3. Dans la build expérimentale, ouvrez un exemple de diagramme.

4. Cliquez avec le bouton droit sur différents éléments du diagramme pour vérifier que la commande est activée ou désactivée correctement et affichée ou masquée de manière appropriée, en fonction de l'élément sélectionné.

## <a name="troubleshoot"></a>Dépanner

**La commande n'apparaît pas dans le menu :**

- La commande apparaît uniquement dans les instances de débogage de Visual Studio jusqu'à ce que vous installiez le package DSL. Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](msi-and-vsix-deployment-of-a-dsl.md).

- Assurez-vous que votre exemple expérimental a l'extension de nom de fichier correcte pour cette solution DSL. Pour vérifier l'extension de nom de fichier, ouvrez DslDefinition.dsl dans l'instance principale de Visual Studio. Ensuite, dans l'Explorateur DSL, cliquez avec le bouton droit sur le nœud Éditeur, puis cliquez sur Propriétés. Dans la fenêtre Propriétés, examinez la propriété FileExtension.

- Avez-vous [incrémenté le numéro de version du package](#version)?

- Définissez un point d'arrêt au début de votre méthode OnStatus. Elle doit s'arrêter quand vous cliquez avec le bouton droit sur une partie quelconque du diagramme.

La **méthode OnStatus n’est pas appelée**:

- Assurez-vous que les GUID et les ID dans votre code CommandSet correspondent à ceux de la section Symbols de Commands.vsct.

- Dans Commands.vsct, assurez-vous que le GUID et l'ID dans chaque nœud Parent identifient le groupe parent correct.

- Dans une invite de commandes Visual Studio, tapez devenv /rootsuffix exp /setup. Ensuite, redémarrez l'instance de débogage de Visual Studio.

- Parcourez la méthode OnStatus pour vérifier que command.Visible et command.Enabled ont la valeur True.

**Un texte de menu incorrect s’affiche, ou la commande ne s’affiche pas à l’endroit approprié**:

- Assurez-vous que la combinaison de GUID et ID est unique à cette commande.

- Assurez-vous d'avoir désinstallé les versions antérieures du package.

## <a name="see-also"></a>Voir aussi

- [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Comment : modifier une commande de menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Déploiement de solutions de langage spécifique à un domaine](msi-and-vsix-deployment-of-a-dsl.md)
- [Exemple de code : diagrammes de circuit](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
