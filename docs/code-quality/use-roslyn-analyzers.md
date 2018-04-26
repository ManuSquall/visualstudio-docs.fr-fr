---
title: Utiliser et configurer des analyseurs de Roslyn dans Visual Studio
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2e99a98f5ea4cca5891d416bdc13656b3173a40f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Configurer et utiliser des règles de l’analyseur Roslyn

Règles de l’analyseur plateforme des compilateurs .NET (« Roslyn »), ou *diagnostics*, analyser votre code c# ou Visual Basic en cours de frappe. Chacun des diagnostics dont un état de gravité et la suppression par défaut qui peut être remplacé pour votre projet. Cet article décrit la gravité de règle de paramètre, à l’aide des ensembles de règles et suppression des violations.

## <a name="analyzers-in-solution-explorer"></a>Analyseurs dans l’Explorateur de solutions

Vous pouvez effectuer une grande partie de la personnalisation de diagnostics analyzer à partir de **l’Explorateur de solutions**. Si vous [installer des analyseurs de](../code-quality/install-roslyn-analyzers.md) sous forme de package NuGet, une **analyseurs** nœud apparaît sous la **références** ou **dépendances** nœud  **L’Explorateur de solutions**. Si vous développez **analyseurs**et développez un des assemblys de l’analyseur, vous voyez tous les diagnostics dans l’assembly.

![Nœud analyseurs dans l’Explorateur de solutions](media/analyzers-expanded-in-solution-explorer.png)

Vous pouvez afficher les propriétés d’un diagnostic, y compris sa description et la gravité par défaut, dans le **propriétés** fenêtre. Pour afficher les propriétés, cliquez sur la règle et sélectionnez **propriétés**, ou sélectionnez la règle, puis appuyez sur **Alt**+**entrée**.

![Propriétés de diagnostic dans la fenêtre Propriétés](media/analyzer-diagnostic-properties.png)

Pour voir la documentation en ligne pour un diagnostic, avec le bouton droit sur le diagnostic et sélectionnez **afficher l’aide**.

Les icônes en regard de chaque diagnostic dans **l’Explorateur de solutions** correspondent aux icônes que vous voyez dans l’ensemble lorsque vous l’ouvrez dans l’éditeur de règles :

- le « i » dans un cercle indique un [gravité](#rule-severity) de **Infos**
- le « ! » dans un triangle indique un [gravité](#rule-severity) de **avertissement**
- le « x » dans un cercle indique un [gravité](#rule-severity) de **erreur**
- le « i » dans un cercle sur fond de couleur claire indique un [gravité](#rule-severity) de **masqué**
- la flèche pointant vers le bas dans un cercle indique que le diagnostic est supprimé.

![Icônes de diagnostics dans l’Explorateur de solutions](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Ensembles de règles

A [ensemble de règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) est un fichier XML qui stocke l’état de gravité et la suppression de diagnostics individuels. Ensembles de règles s’appliquent à un projet unique, et un projet peut avoir plusieurs ensembles de règles. Pour afficher l’ensemble dans l’éditeur de règles active, cliquez sur le **analyseurs** nœud **l’Explorateur de solutions** et sélectionnez **ouvrir ensemble de règles actif**. Si c’est la première fois que vous accédez à la règle définie, un fichier nommé  *\<projectname > .ruleset* est ajouté au projet et apparaît dans **l’Explorateur de solutions**.

> [!NOTE]
> Ensembles de règles sont l’analyse statique du code (binaire) et règles de l’analyseur Roslyn.

Vous pouvez modifier la règle active définie pour un projet sur le **l’analyse du Code** onglet de propriétés d’un projet. Sélectionnez l’ensemble de règles dans le **exécuter cet ensemble de règles** liste déroulante. Vous pouvez également ouvrir l’ensemble de règles la **l’analyse du Code** page de propriétés en sélectionnant **ouvrir**.

## <a name="rule-severity"></a>Gravité de la règle

Vous pouvez configurer la gravité de règles de l’analyseur, ou *diagnostics*, si vous [installer les analyseurs](../code-quality/install-roslyn-analyzers.md) sous forme de package NuGet. Le tableau suivant présente les options de gravité pour les diagnostics :

|Gravité|Comportement au moment de la build|Comportement de l’éditeur|
|-|-|-|
|Error|Les violations apparaissent sous la forme *erreurs* dans les **liste d’erreurs** dans la ligne de commande la sortie de build et provoquer l’échec des builds.|Incriminée code est soulignée d’une croix rouge sinueux et marquée d’un petit carré rouge dans la barre de défilement.|
|Warning|Les violations apparaissent sous la forme *avertissements* dans les **liste d’erreurs** et dans la ligne de commande la sortie de build, mais ne provoquent pas l’échec des builds.|Incriminée code est soulignée avec un vert ondulé et marqué par une petite zone verte dans la barre de défilement.|
|Info|Les violations apparaissent sous la forme *Messages* dans les **liste d’erreurs**et pas dans la sortie de génération de ligne de commande.|Incriminée code est soulignée avec un gris ondulé et marqué par une petite zone grise dans la barre de défilement.|
|Hidden|Non visibles à l’utilisateur.|Non visibles à l’utilisateur. Le diagnostic est signalé pour le moteur de diagnostic de l’IDE, toutefois.|
|Aucun|Supprimé complètement.|Supprimé complètement.|

En outre, vous pouvez « réinitialiser « niveau de gravité d’une règle en lui affectant **par défaut**. Chacun des diagnostics a un niveau de gravité par défaut qui peut être consulté dans le **propriétés** fenêtre.

La capture d’écran suivante montre trois différentes violations de diagnostic dans l’éditeur de code, avec trois différents niveaux de gravité. Notez que la couleur de l’ondulées, ainsi que la petite case dans la barre de défilement à droite.

![Violation d’erreur, avertissement et informations dans l’éditeur de code](media/diagnostics-severity-colors.png)

La capture d’écran suivante affiche les violations de trois mêmes telles qu’elles apparaissent dans le **liste d’erreurs**:

![Violation d’erreur, d’avertissement et d’informations dans la liste d’erreurs](media/diagnostics-severities-in-error-list.png)

Vous pouvez modifier le niveau de gravité d’une règle à partir de **l’Explorateur de solutions**, ou dans le  *\<projectname > .ruleset* fichier est ajouté à la solution une fois que vous modifiez la gravité d’une règle dans  **L’Explorateur de solutions**.

![Fichier ruleset dans l’Explorateur de solutions](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>Pour définir la gravité de la règle à partir de l’Explorateur de solutions

1. Dans **l’Explorateur de solutions**, développez **références** > **analyseurs** (**dépendances**  >  **Analyseurs** pour les projets .NET Core).

1. Développez l’assembly qui contient la règle que vous souhaitez définir la gravité pour.

1. Avec le bouton droit sur la règle, puis sélectionnez **définir une gravité de définir de règle**. Dans le menu contextuel, sélectionnez une des options de niveau de gravité.

   La gravité de la règle est enregistrée dans le fichier d’ensemble de règles actif.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Pour définir la règle de fichier d’ensemble de la gravité de la règle

1. Ouvrir l’ensemble de règles fichier en double-cliquant dessus dans **l’Explorateur de solutions**, en sélectionnant **ensemble de règles actif ouvert** dans le menu contextuel de la **analyseurs** nœud, ou en sélectionnant **Ouvrir** sur la **l’analyse du Code** page de propriétés pour le projet.

1. Accédez à la règle en développant son assembly conteneur.

1. Dans le **Action** colonne, sélectionnez la valeur pour ouvrir une liste déroulante et sélectionnez le niveau de gravité souhaité dans la liste.

   ![Fichier ruleset ouvert dans l’éditeur](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Supprimer les violations

Il existe plusieurs manières de supprimer des violations de règles :

- Pour supprimer toutes les violations actuelles, sélectionnez **analyser** > **exécuter l’analyse du Code et supprimer les problèmes actifs** sur la barre de menus. Cela est parfois appelée « ligne de base ».

- Pour supprimer un diagnostic de **l’Explorateur de solutions**, sa gravité la valeur **aucun**.

- Pour supprimer un diagnostic de l’éditeur d’ensemble de règles, désactivez la case en regard de son nom ou la valeur **Action** à **aucun**.

- Pour supprimer un diagnostic de l’éditeur de code, placez le curseur dans la ligne de code avec la violation et appuyez sur **Ctrl**+**.** Pour ouvrir la **Actions rapides** menu. Sélectionnez **supprimer CAxxxx** > **dans la Source** ou **supprimer CAxxxx** > **dans le fichier de Suppression**.

   ![Supprimer de diagnostic à partir du menu des actions rapides](media/suppress-diagnostic-from-editor.png)

- Pour supprimer un diagnostic de la **liste d’erreurs**, avec le bouton droit sur le message d’erreur, avertissement ou, puis sélectionnez **supprimer** > **dans la Source** ou **Supprimer** > **dans le fichier de Suppression**.

   - Si vous sélectionnez **dans la Source**, le **aperçu des modifications** boîte de dialogue s’ouvre et affiche un aperçu du langage c# [#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) ou Visual Basic [#Disable warning](/dotnet/visual-basic/language-reference/directives/directives) directive qui est ajoutée au code source.

      ![Aperçu de l’ajout de #pragma warning dans le fichier de code](media/pragma-warning-preview.png)

   - Si vous sélectionnez **dans le fichier de Suppression**, le **aperçu des modifications** boîte de dialogue s’ouvre et affiche un aperçu de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut qui est ajouté au fichier suppressions globales.

      ![Aperçu de l’ajout de l’attribut SuppressMessage pour le fichier de suppression](media/preview-changes-in-suppression-file.png)

   Dans le **aperçu des modifications** boîte de dialogue, sélectionnez **appliquer**.

> [!NOTE]
> Dans un projet .NET Core, si vous ajoutez une référence à un projet qui a des analyseurs de NuGet, ces analyseurs sont automatiquement ajoutés au projet dépendant trop. Pour désactiver ce comportement, par exemple, si le projet dépendant est un projet de test unitaire, marquez le package NuGet comme privée dans le *.csproj* ou *.vbproj* fichier du projet référencé :
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de Roslyn dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Envoyer un bogue d’analyseur Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Utiliser des ensembles de règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Supprimer les avertissements d’analyse du code](../code-quality/in-source-suppression-overview.md)