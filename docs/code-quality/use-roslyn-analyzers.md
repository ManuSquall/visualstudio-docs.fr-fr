---
title: Gravité et suppression de la règle de l’analyseur
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1845647dc1848a7fcd99ef59c29eb163bece979d
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186003"
---
# <a name="use-code-analyzers"></a>Utiliser des analyseurs de code

Les analyseurs de code .NET Compiler Platform (« Roslyn ») C# analysent votre code ou Visual Basic au fur et à mesure que vous tapez. Chaque *diagnostic* ou règle a un état de gravité et de suppression par défaut qui peut être remplacé pour votre projet. Cet article traite de la définition de la gravité d’une règle, de l’utilisation d’ensembles de règles et de la suppression des violations.

## <a name="analyzers-in-solution-explorer"></a>Analyseurs en Explorateur de solutions

Vous pouvez effectuer une grande partie de la personnalisation des diagnostics de l’analyseur à partir de **Explorateur de solutions**. Si vous [Installez des analyseurs](../code-quality/install-roslyn-analyzers.md) en tant que package NuGet, un nœud **analyseurs** apparaît sous le nœud **références** ou **dépendances** dans **Explorateur de solutions**. Si vous développez des **analyseurs**, puis que vous développez l’un des assemblys de l’analyseur, vous voyez tous les diagnostics dans l’assembly.

![Nœud analyseurs dans Explorateur de solutions](media/analyzers-expanded-in-solution-explorer.png)

Vous pouvez afficher les propriétés d’un diagnostic, notamment sa description et sa gravité par défaut, dans la fenêtre **Propriétés** . Pour afficher les propriétés, cliquez avec le bouton droit sur la règle et sélectionnez **Propriétés**, ou sélectionnez la règle et appuyez sur **ALT**+**entrée**.

![Propriétés de diagnostic dans Fenêtre Propriétés](media/analyzer-diagnostic-properties.png)

Pour afficher la documentation en ligne d’un diagnostic, cliquez avec le bouton droit sur le diagnostic, puis sélectionnez **afficher l’aide**.

Les icônes en regard de chaque diagnostic dans **Explorateur de solutions** correspondent aux icônes que vous voyez dans l’ensemble de règles lorsque vous l’ouvrez dans l’éditeur :

- le « x » d’un cercle indique une [gravité](#rule-severity) d' **erreur**
- le «  ! » dans un triangle indique une [gravité](#rule-severity) d' **Avertissement**
- le « i » d’un cercle indique une [gravité](#rule-severity) d' **information**
- le « i » dans un cercle sur un arrière-plan de couleur claire indique un niveau de [gravité](#rule-severity) **masqué**
- la flèche pointant vers le bas dans un cercle indique que le diagnostic est supprimé

![Icônes de diagnostics dans Explorateur de solutions](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Gravité des règles

::: moniker range=">=vs-2019"

Vous pouvez configurer la gravité des règles de l’analyseur, ou *Diagnostics*, si vous [Installez les analyseurs](../code-quality/install-roslyn-analyzers.md) en tant que package NuGet. À compter de Visual Studio 2019 version 16,3, vous pouvez configurer la gravité d’une règle [dans un fichier baEditorConfig](#set-rule-severity-in-an-editorconfig-file). Vous pouvez également modifier la gravité d’une règle [à partir Explorateur de solutions](#set-rule-severity-from-solution-explorer) ou [dans un fichier d’ensemble de règles](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Vous pouvez configurer la gravité des règles de l’analyseur, ou *Diagnostics*, si vous [Installez les analyseurs](../code-quality/install-roslyn-analyzers.md) en tant que package NuGet. Vous pouvez modifier la gravité d’une règle [à partir Explorateur de solutions](#set-rule-severity-from-solution-explorer) ou [dans un fichier d’ensemble de règles](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

Le tableau suivant présente les différentes options de gravité :

| Gravité (Explorateur de solutions) | Gravité (fichier EditorConfig) | Comportement au moment de la génération | Comportement de l’éditeur |
|-|-|-|
| Error | `error` | Les violations apparaissent comme des *Erreurs* dans les liste d’erreurs et dans la sortie de la génération en ligne de commande, et entraînent l’échec des builds.| Le code incriminé est souligné d’un trait ondulé rouge et marqué d’une petite zone rouge dans la barre de défilement. |
| Warning | `warning` | Les violations apparaissent en tant qu' *avertissements* dans le liste d’erreurs et dans la sortie de la génération en ligne de commande, mais ne provoquent pas l’échec des builds. | Le code incriminé est souligné d’un trait ondulé vert et marqué d’une petite zone verte dans la barre de défilement. |
| Info | `suggestion` | Les violations apparaissent sous la forme de *messages* dans le liste d’erreurs, et pas du tout dans la sortie de la génération de la ligne de commande. | Le code incriminé est souligné d’un trait ondulé gris, et marqué d’une petite zone grise dans la barre de défilement. |
| Hidden | `silent` | Non visible par l’utilisateur. | Non visible par l’utilisateur. Toutefois, le diagnostic est signalé au moteur de diagnostic IDE. |
| Aucun. | `none` | Entièrement supprimée. | Entièrement supprimée. |
| Par défaut | `default` | Correspond à la gravité par défaut de la règle. Pour déterminer la valeur par défaut d’une règle, recherchez dans la Fenêtre Propriétés. | Correspond à la gravité par défaut de la règle. |

La capture d’écran suivante de l’éditeur de code montre trois violations différentes avec des gravités différentes. Notez la couleur du tilde et le petit carré de couleur de la barre de défilement à droite.

![Erreur, avertissement et violation d’informations dans l’éditeur de code](media/diagnostics-severity-colors.png)

La capture d’écran suivante montre les trois mêmes violations qui apparaissent dans le Liste d’erreurs :

![Erreur, avertissement et violation d’informations dans Liste d’erreurs](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Définir la gravité de la règle dans un fichier baEditorConfig

(Visual Studio 2019 version 16,3 et versions ultérieures)

La syntaxe générale pour spécifier la gravité d’une règle dans un fichier EditorConfig est la suivante :

`dotnet_diagnostic.<rule ID>.severity = <severity>`

La définition de la gravité d’une règle dans un fichier baEditorConfig est prioritaire sur toute gravité définie dans un ensemble de règles ou dans Explorateur de solutions. Vous pouvez configurer [manuellement](#manually-configure-rule-severity) la gravité dans un fichier baEditorConfig ou [automatiquement](#automatically-configure-rule-severity) par le biais de l’ampoule qui s’affiche en regard d’une violation.

#### <a name="manually-configure-rule-severity"></a>Configurer manuellement la gravité de la règle

1. Si vous n’avez pas encore de fichier EditorConfig pour votre projet, ajoutez-en [un](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Ajoutez une entrée pour chaque règle que vous souhaitez configurer sous l’extension de fichier correspondante. Par exemple, pour définir la gravité de [CA1822](ca1822-mark-members-as-static.md) sur `error` pour C# les fichiers, l’entrée ressemble à ce qui suit :

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Pour les analyseurs de style de code IDE, vous pouvez également les configurer dans un fichier EditorConfig à l’aide d’une syntaxe `dotnet_style_qualification_for_field = false:suggestion`différente, par exemple,. Toutefois, si vous définissez une gravité à l' `dotnet_diagnostic` aide de la syntaxe, elle est prioritaire. Pour plus d’informations, consultez [conventions de langage pour EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="automatically-configure-rule-severity"></a>Configurer automatiquement la gravité de la règle

Visual Studio offre un moyen pratique de configurer le niveau de gravité d’une règle à partir du menu de l’ampoule [actions rapides](../ide/quick-actions.md) .

1. Une fois qu’une violation se produit, placez le curseur sur le tilde de violation dans l’éditeur et ouvrez le menu ampoule. Ou placez votre curseur sur la ligne et appuyez sur **CTRL**+ **.** (point).

2. Dans le menu ampoule, sélectionnez **configurer ou supprimer les problèmes** > **configurer \<l’ID de règle > gravité**.

   ![Configurer la gravité de la règle à partir du menu ampoule dans Visual Studio](media/configure-rule-severity.png)

3. À partir de là, sélectionnez l’une des options de gravité.

   ![Configurer la gravité de la règle comme suggestion](media/configure-rule-severity-suggestion.png)

   Visual Studio ajoute une entrée au fichier EditorConfig pour configurer la règle au niveau demandé, comme indiqué dans la zone Aperçu.

   > [!TIP]
   > Si vous n’avez pas encore de fichier EditorConfig dans le projet, Visual Studio en crée un pour vous.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Définir la gravité de la règle à partir d’Explorateur de solutions

1. Dans **Explorateur de solutions**, développez **références** > **analyseurs** (ou**analyseurs** de **dépendances** > pour les projets .net Core).

1. Développez l’assembly qui contient la règle pour laquelle vous souhaitez définir la gravité.

1. Cliquez avec le bouton droit sur la règle et sélectionnez définir la gravité de l' **ensemble de règles**. Dans le menu volant, sélectionnez l’une des options de gravité.

   La gravité de la règle est enregistrée dans le fichier de l’ensemble de règles actif.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Définir la gravité de la règle dans le fichier d’ensemble de règles

![Fichier d’ensemble de règles dans Explorateur de solutions](media/ruleset-in-solution-explorer.png)

1. Ouvrez le fichier de l' [ensemble de règles](analyzer-rule-sets.md) actif en double-cliquant dessus dans **Explorateur de solutions**, en sélectionnant Ouvrir l' **ensemble de règles actif** dans le menu contextuel du nœud**analyseurs** de **références** > , ou en sélectionnant **ouvrir** sur page de propriétés de l' **analyse du code** du projet.

   Si c’est la première fois que vous modifiez l’ensemble de règles, Visual Studio effectue une copie du fichier de l’ensemble de règles par défaut, le nomme  *\<ProjectName >. RuleSet*et l’ajoute à votre projet. Cet ensemble de règles personnalisé devient également l’ensemble de règles actif pour votre projet.

   > [!NOTE]
   > Les projets .NET Core et .NET Standard ne prennent pas en charge les commandes de menu pour les ensembles de règles dans **Explorateur de solutions**, par exemple, **ouvrir l’ensemble de règles actif**. Pour spécifier un ensemble de règles non défini par défaut pour un projet .NET Core ou .NET Standard, [Ajoutez manuellement la propriété **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) au fichier projet. Vous pouvez toujours configurer les règles dans l’ensemble de règles dans l’interface utilisateur de l’éditeur d’ensembles de règles de Visual Studio.

1. Accédez à la règle en développant son assembly conteneur.

1. Dans la colonne **action** , sélectionnez la valeur pour ouvrir une liste déroulante, puis sélectionnez la gravité souhaitée dans la liste.

   ![Fichier d’ensemble de règles ouvert dans l’éditeur](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Supprimer les violations

Il existe plusieurs façons de supprimer des violations de règle :

::: moniker range=">=vs-2019"

- Dans un **fichier EditorConfig**

  Définissez la gravité sur `none`, par exemple, `dotnet_diagnostic.CA1822.severity = none`.

::: moniker-end

- Dans le menu **analyser**

  Sélectionnez **analyser** > **exécuter l’analyse du code et supprimer les problèmes actifs** dans la barre de menus pour supprimer toutes les violations en cours. Cette opération est parfois appelée « ligne de l’établissement ».

- À partir de **Explorateur de solutions**

  Définissez le niveau de gravité de la règle sur **aucun**.

- À partir de l' **éditeur d’ensembles de règles**

  Décochez la case en regard de son nom ou définissez **action** sur **aucun**.

- À partir de l' **éditeur de code**

  Placez le curseur dans la ligne de code avec la violation et appuyez sur **CTRL**++**point (.)** pour ouvrir le menu **actions rapides** . Sélectionnez **supprimer CAXXXX** > **dans le fichier source/de suppression**.

  ![Supprimer les diagnostics du menu actions rapides](media/suppress-diagnostic-from-editor.png)

- À partir de la **liste d’erreurs**

  Sélectionnez les règles que vous souhaitez supprimer, puis cliquez avec le bouton droit et sélectionnez **supprimer** > **dans le fichier source/de suppression**.

  - Si vous supprimez **dans la source**, la boîte de dialogue **aperçu des modifications** s’ouvre C# et affiche un aperçu de l' [Avertissement #pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) ou Visual Basic directive d' [Avertissement #Disable](/dotnet/visual-basic/language-reference/directives/directives) ajoutée au code source.

    ![Aperçu de l’ajout d' #pragma avertissement dans le fichier de code](media/pragma-warning-preview.png)

  - Si vous sélectionnez **dans le fichier de suppression**, la boîte de dialogue **aperçu des modifications** s’ouvre <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> et affiche un aperçu de l’attribut qui est ajouté au fichier de suppression globale.

    ![Aperçu de l’ajout de l’attribut SuppressMessage au fichier de suppression](media/preview-changes-in-suppression-file.png)

  Dans la boîte de dialogue **aperçu des modifications** , sélectionnez **appliquer**.

  > [!NOTE]
  > Si vous ne voyez pas l’option de menu **supprimer** dans **Explorateur de solutions**, la violation provient probablement de la génération et non de l’analyse en temps réel. Le **liste d’erreurs** affiche les diagnostics ou les violations de règle à partir de l’analyse du code en direct et de la Build. Comme les diagnostics de build peuvent être périmés, par exemple, si vous avez modifié le code pour corriger la violation mais que vous ne l’avez pas reconstruit, vous ne pouvez pas supprimer ces diagnostics du **liste d’erreurs**. Les diagnostics à partir de l’analyse en direct, ou IntelliSense, sont toujours à jour avec les sources actuelles et peuvent être supprimés du **liste d’erreurs**. Pour exclure les diagnostics de *Build* de votre sélection, basculez le filtre de source de **liste d’erreurs** de la **génération + IntelliSense** vers **IntelliSense uniquement**. Sélectionnez ensuite les diagnostics que vous souhaitez supprimer et procédez comme décrit précédemment.
  >
  > ![Filtre de source de Liste d’erreurs dans Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Utilisation de la ligne de commande

Lorsque vous générez votre projet sur la ligne de commande, des violations de règle apparaissent dans la sortie de la génération si les conditions suivantes sont remplies :

- Les analyseurs sont installés en tant que package NuGet et non pas en tant qu’extension VSIX.

- Une ou plusieurs règles sont enfreintes dans le code du projet.

- La [gravité](#rule-severity) d’une règle non respectée est définie sur **Avertissement**. dans ce cas, les violations ne provoquent pas l’échec de la génération, ou une **erreur**, auquel cas les violations provoquent l’échec de la génération.

Le niveau de détail de la sortie de la génération n’a aucune incidence sur l’affichage des violations de règle. Même avec un niveau de détail **silencieux** , les violations de règle apparaissent dans la sortie de la génération.

> [!TIP]
> Si vous êtes habitué à exécuter des analyses héritées à partir de la ligne de commande, soit avec *FxCopCmd. exe* , soit via MSBuild avec l’indicateur **RunCodeAnalysis** , voici comment procéder avec les analyseurs de code.

Pour voir les violations de l’analyseur sur la ligne de commande lorsque vous générez votre projet à l’aide de MSBuild, exécutez une commande comme celle-ci :

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

L’illustration suivante montre la sortie de la génération en ligne de commande de la génération d’un projet qui contient une violation de règle de l’analyseur :

![Sortie MSBuild avec violation de règle](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Projets dépendants

Dans un projet .NET Core, si vous ajoutez une référence à un projet qui a des analyseurs NuGet, ces analyseurs sont automatiquement ajoutés au projet dépendant. Pour désactiver ce comportement, par exemple si le projet dépendant est un projet de test unitaire, marquez le package NuGet comme privé dans le fichier *. csproj* ou *. vbproj* du projet référencé en définissant l’attribut **PrivateAssets** :

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de code dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Soumettre un bogue de l’analyseur de code](https://github.com/dotnet/roslyn-analyzers/issues)
- [Utiliser des ensembles de règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Supprimer les avertissements d’analyse du code](../code-quality/in-source-suppression-overview.md)
