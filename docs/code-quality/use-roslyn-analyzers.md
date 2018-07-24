---
title: Utiliser et configurez des analyseurs de Roslyn dans Visual Studio
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
ms.openlocfilehash: 6668b3727e5df17c3d436e37f2edd78a67a79eba
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204152"
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>Configurer et utiliser des règles de l’analyseur Roslyn

Règles de l’analyseur .NET compiler Platform (« Roslyn »), ou *diagnostics*, analyser votre code c# ou Visual Basic en cours de frappe. Chacun des diagnostics a un état de gravité et la suppression par défaut qui peut être remplacé pour votre projet. Cet article décrit la gravité de règle de paramètre, à l’aide des ensembles de règles et suppression des violations.

## <a name="analyzers-in-solution-explorer"></a>Analyseurs dans l’Explorateur de solutions

Vous pouvez effectuer une grande partie de la personnalisation des diagnostics analyzer à partir de **l’Explorateur de solutions**. Si vous [installer analyseurs](../code-quality/install-roslyn-analyzers.md) sous forme de package NuGet, un **analyseurs** nœud apparaît sous la **références** ou **dépendances** nœud  **L’Explorateur de solutions**. Si vous développez **analyseurs**et développez un des assemblys de l’analyseur, vous voyez tous les diagnostics dans l’assembly.

![Nœud d’analyseurs dans l’Explorateur de solutions](media/analyzers-expanded-in-solution-explorer.png)

Vous pouvez afficher les propriétés d’un diagnostic, y compris sa description et la gravité par défaut, dans le **propriétés** fenêtre. Pour afficher les propriétés, cliquez sur la règle et sélectionnez **propriétés**, ou sélectionnez la règle et appuyez sur **Alt**+**entrée**.

![Propriétés de diagnostic dans la fenêtre Propriétés](media/analyzer-diagnostic-properties.png)

Pour afficher la documentation en ligne pour un diagnostic, avec le bouton droit sur le diagnostic et sélectionnez **afficher l’aide**.

Les icônes en regard de chaque diagnostic dans **l’Explorateur de solutions** correspondent aux icônes que vous voyez dans l’ensemble lorsque vous l’ouvrez dans l’éditeur de règles :

- le « i » dans un cercle indique un [gravité](#rule-severity) de **Infos**
- le « ! » dans un triangle indique un [gravité](#rule-severity) de **avertissement**
- le « x » dans un cercle indique un [gravité](#rule-severity) de **erreur**
- le « i » dans un cercle sur fond de couleur claire indique un [gravité](#rule-severity) de **Hidden**
- la flèche pointant vers le bas dans un cercle indique que le diagnostic est supprimé.

![Icônes de diagnostics dans l’Explorateur de solutions](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Ensembles de règles

Un [ensemble de règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) est un fichier XML qui stocke l’état de gravité et de suppression pour les diagnostics individuels. Ensembles de règles s’appliquent à un seul projet, et un projet peut avoir plusieurs ensembles de règles. Pour afficher l’ensemble dans l’éditeur de règles active, cliquez sur le **analyseurs** nœud **l’Explorateur de solutions** et sélectionnez **Open ensemble de règles Active**. Si c’est la première fois que vous accédez à la règle définie, un fichier nommé  *\<nom_projet > .ruleset* est ajouté au projet et apparaît dans **l’Explorateur de solutions**.

> [!NOTE]
> Ensembles de règles incluent l’analyse statique du code (binaire) et règles de l’analyseur Roslyn.

Vous pouvez modifier la règle active définie pour un projet sur le **analyse du Code** onglet de propriétés d’un projet. Sélectionnez l’ensemble de règles dans le **exécuter cet ensemble de règles** liste déroulante. Vous pouvez également ouvrir l’ensemble de règles la **analyse du Code** page de propriétés en sélectionnant **ouvrir**.

## <a name="rule-severity"></a>Gravité de la règle

Vous pouvez configurer la gravité de règles de l’analyseur, ou *diagnostics*, si vous [installer les analyseurs](../code-quality/install-roslyn-analyzers.md) sous forme de package NuGet. Le tableau suivant présente les options de gravité pour les diagnostics :

|Gravité|Comportement au moment de la build|Comportement de l’éditeur|
|-|-|-|
|Error|Violations apparaissent sous la forme *erreurs* dans le **liste d’erreurs** dans la ligne de commande Générer la sortie et provoquer l’échec des builds.|Incriminé code est souligné d’une croix rouge ondulée et marquée par une petite zone rouge dans la barre de défilement.|
|Warning|Violations apparaissent sous la forme *avertissements* dans le **liste d’erreurs** et dans la ligne de commande Générer la sortie, mais ne provoquent pas l’échec des builds.|Incriminé code est souligné avec une verte ondulée et marquée par une petite zone verte dans la barre de défilement.|
|Info|Violations apparaissent sous la forme *Messages* dans le **liste d’erreurs**et pas du tout dans la sortie de génération de ligne de commande.|Incriminé code est souligné avec un gris ondulé et marqué par une petite zone grise dans la barre de défilement.|
|Hidden|Non visibles à l’utilisateur.|Non visibles à l’utilisateur. Le diagnostic est signalé pour le moteur de diagnostic de l’IDE, toutefois.|
|Aucun.|Supprimé complètement.|Supprimé complètement.|

En outre, vous pouvez « réinitialiser » niveau de gravité d’une règle en lui affectant **par défaut**. Chacun des diagnostics a une gravité par défaut qui peut être consultée dans le **propriétés** fenêtre.

La capture d’écran suivante montre trois différentes violations de diagnostics dans l’éditeur de code, avec trois différents niveaux de gravité. Notez que la couleur de la ligne ondulée, ainsi que la petite case dans la barre de défilement sur la droite.

![Violation d’erreur, avertissement et informations dans l’éditeur de code](media/diagnostics-severity-colors.png)

La capture d’écran suivante montre les violations de trois mêmes tels qu’ils apparaissent dans le **liste d’erreurs**:

![Violation d’erreur, avertissement et informations dans la liste d’erreurs](media/diagnostics-severities-in-error-list.png)

Vous pouvez modifier le niveau de gravité d’une règle à partir de **l’Explorateur de solutions**, ou à l’intérieur du  *\<nom_projet > .ruleset* fichier est ajouté à la solution une fois que vous modifiez la gravité d’une règle dans  **L’Explorateur de solutions**.

![Fichier d’ensemble de règles dans l’Explorateur de solutions](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>Définir la gravité de règle à partir de l’Explorateur de solutions

1. Dans **l’Explorateur de solutions**, développez **références** > **analyseurs** (**dépendances**  >  **Analyseurs** pour les projets .NET Core).

1. Développez l’assembly qui contient la règle que vous souhaitez définir la gravité pour.

1. Avec le bouton droit sur la règle, puis sélectionnez **gravité de définir l’ensemble règle**. Dans le menu contextuel, sélectionnez une des options de niveau de gravité.

   La gravité de la règle est enregistrée dans le fichier d’ensemble de règles actif.

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>Pour définir la règle de gravité dans la règle de définie le fichier

1. Ouvrez l’ensemble de règles fichier en double-cliquant dessus dans **l’Explorateur de solutions**, en sélectionnant **Open ensemble de règles Active** dans le menu contextuel de la **analyseurs** nœud, ou en sélectionnant **Open** sur le **analyse du Code** page de propriétés pour le projet.

1. Accédez à la règle en développant son assembly conteneur.

1. Dans le **Action** colonne, sélectionnez la valeur pour ouvrir la liste déroulante, sélectionnez le niveau de gravité souhaité dans la liste.

   ![Ensemble de règles fichier ouvert dans l’éditeur](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Supprimer les violations

Il existe plusieurs moyens de supprimer les violations de règle :

- Pour supprimer toutes les violations actuelles, sélectionnez **analyser** > **exécuter l’analyse du Code et supprimer les problèmes actifs** sur la barre de menus. Cela est parfois appelé « planification ».

- Pour supprimer un diagnostic à partir de **l’Explorateur de solutions**, définir son niveau de gravité **aucun**.

- Pour supprimer un diagnostic à partir de l’éditeur d’ensemble de règles, décochez la case en regard de son nom ou la valeur **Action** à **aucun**.

- Pour supprimer un diagnostic à partir de l’éditeur de code, placez le curseur dans la ligne de code avec la violation et appuyez sur **Ctrl**+**.** Pour ouvrir le **Actions rapides** menu. Sélectionnez **supprimer CAxxxx** > **dans la Source** ou **supprimer CAxxxx** > **dans le fichier de Suppression**.

   ![Supprimer le diagnostic à partir du menu actions rapides](media/suppress-diagnostic-from-editor.png)

- Pour supprimer un diagnostic à partir de la **liste d’erreurs**, consultez [supprimer les violations de la liste d’erreurs](#suppress-violations-from-the-error-list).

### <a name="suppress-violations-from-the-error-list"></a>Supprimer les violations de la liste d’erreurs

Vous pouvez supprimer un ou plusieurs diagnostics à partir de la **liste d’erreurs** en sélectionnant celles que vous souhaitez supprimer, puis en cliquant et en sélectionnant **supprimer** > **dans la Source**  ou **supprimer** > **dans le fichier de Suppression**.

   - Si vous sélectionnez **dans la Source**, le **aperçu des modifications** boîte de dialogue s’ouvre et affiche un aperçu du langage c# [#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) ou Visual Basic [#Disable warning](/dotnet/visual-basic/language-reference/directives/directives) directive qui est ajoutée au code source.

      ![Aperçu de l’ajout de #pragma warning dans le fichier de code](media/pragma-warning-preview.png)

   - Si vous sélectionnez **dans le fichier de Suppression**, le **aperçu des modifications** boîte de dialogue s’ouvre et affiche un aperçu de la <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribut qui est ajouté au fichier suppressions globales.

      ![Aperçu de l’ajout de l’attribut SuppressMessage pour le fichier de suppression](media/preview-changes-in-suppression-file.png)

   Dans le **aperçu des modifications** boîte de dialogue, sélectionnez **appliquer**.

Le **liste d’erreurs** affiche des diagnostics, ou la règle violations, à la fois en direct de l’analyse du code et génèrent. Étant donné que les diagnostics de build peuvent être obsolètes, par exemple, si vous avez modifié le code pour corriger la violation mais que vous n’avez pas reconstruit, vous ne peut pas supprimer ces diagnostics à partir de la **liste d’erreurs**. Toutefois, les diagnostics d’analyse en temps réel ou IntelliSense, sont toujours à jour avec des sources en cours et peut être supprimées à partir de la **liste d’erreurs**. Si l’option de suppression est désactivée dans le menu contextuel, ou un contexte, il est probable, car vous en avez un ou plusieurs diagnostics dans votre sélection de build. Pour exclure les diagnostics de build de votre sélection, basculer le **liste d’erreurs** filtre source à partir de **Build + IntelliSense** à **Intellisense uniquement**. Ensuite, sélectionnez les tests de diagnostic que vous souhaitez supprimer et procéder comme indiqué précédemment.

![Filtre de liste d’erreur source dans Visual Studio](media/error-list-filter.png)

> [!NOTE]
> Dans un projet .NET Core, si vous ajoutez une référence à un projet qui a les analyseurs NuGet, ces analyseurs sont automatiquement ajoutés au projet dépendant trop. Pour désactiver ce comportement, par exemple si le projet dépendant est un projet de test unitaire, marquez le package NuGet comme privée dans le *.csproj* ou *.vbproj* fichier du projet référencé :
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de Roslyn dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Envoyer un bogue d’analyseur Roslyn](https://github.com/dotnet/roslyn-analyzers/issues)
- [Utiliser des ensembles de règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Supprimer les avertissements d’analyse du code](../code-quality/in-source-suppression-overview.md)