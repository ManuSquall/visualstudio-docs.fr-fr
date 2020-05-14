---
title: Sévérité et suppression des règles d’analyseur
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67fd157ad4db24acbc1676ea0a9a1d79e9eb34f9
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431408"
---
# <a name="use-code-analyzers"></a>Utiliser des analyseurs de code

Les analyseurs de code .NET Compiler Platform ("Roslyn") analysent votre code de base visuel ou C ou Visual Basic au fur et à mesure que vous tapez. Chaque *diagnostic* ou règle a un état de gravité et de suppression par défaut qui peut être écrasé pour votre projet. Cet article couvre la sévérité des règles de fixation, l’utilisation d’ensembles de règles et la suppression des violations.

## <a name="analyzers-in-solution-explorer"></a>Analyseurs dans Solution Explorer

Vous pouvez faire une grande partie de la personnalisation des diagnostics d’analyseur de **Solution Explorer**. Si vous [installez des analyseurs](../code-quality/install-roslyn-analyzers.md) comme un paquet NuGet, un nœud **Analyseur** apparaît sous le nœud **Références** ou **Dépendances** dans **Solution Explorer**. Si vous élargissez **Les analyseurs,** puis élargissez l’un des assemblages d’analyseurs, vous voyez tous les diagnostics dans l’assemblage.

![Analyseurs noeud dans Solution Explorer](media/analyzers-expanded-in-solution-explorer.png)

Vous pouvez afficher les propriétés d’un diagnostic, y compris sa description et la gravité par défaut, dans la fenêtre **Propriétés.** Pour afficher les propriétés, cliquez à droite sur la règle et sélectionnez **les propriétés,** ou sélectionnez la règle, puis appuyez sur **Alt**+**Enter**.

![Propriétés diagnostiques dans la fenêtre de propriétés](media/analyzer-diagnostic-properties.png)

Pour voir la documentation en ligne pour un diagnostic, cliquez à droite sur le diagnostic et sélectionnez **View Help**.

Les icônes à côté de chaque diagnostic dans **Solution Explorer** correspondent aux icônes que vous voyez dans l’ensemble de règles lorsque vous l’ouvrez dans l’éditeur :

- le "x" dans un cercle indique une [gravité](#rule-severity) de **l’erreur**
- le "!" dans un triangle indique une [sévérité](#rule-severity) de **l’avertissement**
- le "i" dans un cercle indique une [sévérité](#rule-severity) de **Info**
- le "i" dans un cercle sur un fond de couleur claire indique une [sévérité](#rule-severity) de **Hidden**
- la flèche pointant vers le bas dans un cercle indique que le diagnostic est supprimé

![Icônes de diagnostic dans Solution Explorer](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>Gravité des règles

::: moniker range=">=vs-2019"

Vous pouvez configurer la sévérité des règles de l’analyseur, ou *des diagnostics,* si vous [installez les analyseurs](../code-quality/install-roslyn-analyzers.md) comme un paquet NuGet. À partir de Visual Studio 2019 version 16.3, vous pouvez configurer la sévérité d’une règle [dans un fichier EditorConfig](#set-rule-severity-in-an-editorconfig-file). Vous pouvez également modifier la sévérité d’une règle [de Solution Explorer](#set-rule-severity-from-solution-explorer) ou dans un fichier défini par les [règles](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

::: moniker range="vs-2017"

Vous pouvez configurer la sévérité des règles de l’analyseur, ou *des diagnostics,* si vous [installez les analyseurs](../code-quality/install-roslyn-analyzers.md) comme un paquet NuGet. Vous pouvez modifier la sévérité d’une règle [à partir de Solution Explorer](#set-rule-severity-from-solution-explorer) ou dans un fichier défini par les [règles](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

Le tableau suivant montre les différentes options de gravité :

| Sévérité (Solution Explorer) | Sévérité (Fichier EditorConfig) | Comportement à temps de construction | Comportement de l’éditeur |
|-|-|-|
| Error | `error` | Les violations apparaissent comme *des erreurs* dans la liste d’erreurs et dans la sortie de construction de la ligne de commande, et causent des builds à l’échec.| Le code incriminé est souligné par un gribouillis rouge et marqué par une petite boîte rouge dans la barre de défilement. |
| Avertissement | `warning` | Les violations apparaissent comme *des avertissements* dans la liste d’erreurs et dans la sortie de construction de ligne de commande, mais ne causent pas des builds pour échouer. | Le code incriminé est souligné par un gribouillis vert et marqué par une petite boîte verte dans la barre de défilement. |
| Info | `suggestion` | Les violations apparaissent sous le titre *messages* dans la liste d’erreurs, et pas du tout dans la sortie de construction de la ligne de commande. | Le code incriminé est souligné par un gribouillis gris et marqué par une petite boîte grise dans la barre de défilement. |
| Hidden | `silent` | Non visible pour l’utilisateur. | Non visible pour l’utilisateur. Le diagnostic est rapporté au moteur de diagnostic d’IDE, cependant. |
| None | `none` | Supprimé complètement. | Supprimé complètement. |
| Default | `default` | Correspond à la sévérité par défaut de la règle. Pour déterminer quelle est la valeur par défaut d’une règle, regardez dans la fenêtre Propriétés. | Correspond à la sévérité par défaut de la règle. |

La capture d’écran suivante de l’éditeur de code montre trois violations différentes avec des sévérités différentes. Remarquez la couleur du gribouillis et le petit carré coloré dans la barre de défilement sur la droite.

![Erreur, avertissement et violation d’informations dans l’éditeur de code](media/diagnostics-severity-colors.png)

La capture d’écran suivante montre les trois mêmes violations qu’elles apparaissent dans la liste d’erreurs :

![Erreur, avertissement et violation d’informations dans la liste d’erreurs](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Définir la sévérité des règles dans un fichier EditorConfig

(Visual Studio 2019 version 16.3 et plus tard)

Vous pouvez définir la sévérité des avertissements de compilateur ou des règles d’analyseur dans un fichier EditorConfig avec la syntaxe suivante :

`dotnet_diagnostic.<rule ID>.severity = <severity>`

L’établissement de la sévérité d’une règle dans un fichier EditorConfig prime sur toute gravité définie dans un ensemble de règles ou dans Solution Explorer. Vous pouvez configurer [manuellement](#manually-configure-rule-severity) la gravité dans un fichier EditorConfig ou [automatiquement](#automatically-configure-rule-severity) à travers l’ampoule qui apparaît à côté d’une violation.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Définir la sévérité des règles relatives à plusieurs analyseurs à la fois dans un fichier EditorConfig

(Visual Studio 2019 version 16.5 et plus tard)

Vous pouvez définir la sévérité d’une catégorie spécifique de règles d’analyseur ou pour toutes les règles d’analyseur avec une seule entrée dans un fichier EditorConfig.

- Définir la sévérité des règles pour une catégorie de règles d’analyseur :

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Définir la sévérité des règles pour toutes les règles de l’analyseur :

`dotnet_analyzer_diagnostic.severity = <severity>`

Si vous avez plusieurs entrées qui s’appliquent à une pièce d’identité de règle spécifique, ce qui suit est l’ordre de préséance pour choisir l’entrée applicable :

- L’entrée de sévérité d’une règle individuelle par pièce d’identité a préséance sur l’entrée de gravité pour une catégorie.
- L’entrée de sévérité pour une catégorie a préséance sur l’entrée de sévérité pour toutes les règles d’analyseur.

Prenons l’exemple suivant de EditorConfig, où [CA1822](https://docs.microsoft.com/visualstudio/code-quality/ca1822) a la catégorie « Performance » :

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Dans l’exemple précédent, les trois entrées s’appliquent à CA1822. Toutefois, en utilisant les règles de préséance spécifiées, la première règle basée sur l’ID saisie de gravité gagne sur les entrées suivantes. Dans cet exemple, CA1822 aura une sévérité efficace de «erreur». Toutes les règles restantes avec la catégorie «Performance» auront la sévérité «avertissement». Toutes les règles d’analyseur restantes, qui n’ont pas la catégorie «Performance», auront la sévérité «suggestion».

#### <a name="manually-configure-rule-severity"></a>Configurer manuellement la sévérité des règles

1. Si vous n’avez pas déjà de fichier EditorConfig pour votre projet, [ajoutez-en un](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Ajoutez une entrée pour chaque règle que vous souhaitez configurer sous l’extension de fichier correspondante. Par exemple, pour définir la gravité des `error` [fichiers CA1822](ca1822.md) pour les fichiers CMD, l’entrée semble la suivante :

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Pour les analyseurs de code IDE, vous pouvez également les configurer dans un `dotnet_style_qualification_for_field = false:suggestion`fichier EditorConfig à l’aide d’une syntaxe différente, par exemple. Cependant, si vous définissez `dotnet_diagnostic` une sévérité à l’aide de la syntaxe, elle prime. Pour plus d’informations, voir [Conventions linguistiques pour EditorConfig](../ide/editorconfig-language-conventions.md).

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Convertir un fichier Ruleset existant en fichier EditorConfig

À partir de Visual Studio 2019 version 16.5, les fichiers de règles sont dépréciés en faveur du fichier EditorConfig pour la configuration des analyseurs pour le code géré. La plupart de l’outillage Visual Studio pour la configuration de la gravité des règles d’analyseur a été mis à jour pour travailler sur les fichiers EditorConfig au lieu de fichiers de règles. Les fichiers EditorConfig vous permettent de configurer à la fois les séparations de règles d’analyseur et les options d’analyseur, y compris les options de style de code Visual Studio IDE. Il est fortement recommandé de convertir votre fichier de règles existant en fichier EditorConfig. Il est également recommandé d’enregistrer le fichier EditorConfig à la racine de votre pension ou dans le dossier de solution. En utilisant la racine de votre dossier de pension ou de solution, vous vous assurez que les paramètres de gravité de ce fichier sont automatiquement appliqués à l’ensemble de la pension ou de la solution, respectivement.

Il existe quelques façons de convertir un fichier de règles existants en un fichier EditorConfig :

- De l’éditeur Ruleset en visual Studio (nécessite Visual Studio 2019 16.5 ou plus tard). Si votre projet utilise déjà un `CodeAnalysisRuleSet`fichier de règles spécifique comme son , vous pouvez le convertir en un fichier EditorConfig équivalent de Ruleset Editor au sein de Visual Studio.

    1. Double-cliquez sur le fichier de règles dans Solution Explorer.

       Le fichier Ruleset devrait être ouvert dans l’éditeur Ruleset. Vous devriez voir une **barre d’information** cliquable en haut de l’éditeur de l’éditeur de règles.

       ![Convertir Ruleset en editorConfig dans Ruleset Editor](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **Cliquez sur** le lien infobar.

       Cela devrait ouvrir un dialogue **Save As** qui vous permet de sélectionner l’annuaire où vous souhaitez générer le fichier EditorConfig.

    3. **Cliquez** sur le bouton **Enregistrer** pour générer le fichier EditorConfig.

       Le EditorConfig généré devrait s’ouvrir dans l’éditeur. En outre, la propriété `CodeAnalysisRuleSet` MSBuild est mise à jour dans le fichier du projet de sorte qu’il ne fait plus référence au fichier d’origine de l’établissement de règles.

- Depuis la ligne de commande :

    1. Installer le paquet NuGet [Microsoft.CodeAnalysis.RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Exécutez `RulesetToEditorconfigConverter.exe` à partir du paquet installé, avec des chemins pour le fichier de jeu de règles et le fichier EditorConfig comme arguments de ligne de commande.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Voici un fichier de règles pour convertir :

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

Voici le fichier EditorConfig converti :

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```

#### <a name="automatically-configure-rule-severity"></a>Configurer automatiquement la sévérité des règles

##### <a name="configure-from-light-bulb-menu"></a>Configurer à partir du menu ampoule

Visual Studio offre un moyen pratique de configurer la sévérité d’une règle à partir du menu [d’ampoules Quick Actions.](../ide/quick-actions.md)

1. Après une violation se produit, planer sur la violation squiggle dans l’éditeur et ouvrir le menu ampoule. Ou, mettez votre curseur sur la ligne et appuyez sur **Ctrl**+**.** (point).

2. Dans le menu de l’ampoule, **sélectionnez Configurer ou supprimer les problèmes** > **Configurer \<l’ID de règle> la sévérité**.

   ![Configurer la sévérité des règles à partir du menu de l’ampoule dans Visual Studio](media/configure-rule-severity.png)

3. À partir de là, sélectionnez l’une des options de gravité.

   ![Configurer la sévérité des règles en tant que suggestion](media/configure-rule-severity-suggestion.png)

   Visual Studio ajoute une entrée au fichier EditorConfig pour configurer la règle au niveau demandé, comme indiqué dans la boîte de prévisualisation.

   > [!TIP]
   > Si vous n’avez pas déjà de fichier EditorConfig dans le projet, Visual Studio en crée un pour vous.

##### <a name="configure-from-error-list"></a>Configurer à partir de la liste d’erreurs

Visual Studio fournit également un moyen pratique de configurer la gravité d’une règle à partir du menu contextuelle de la liste d’erreurs.

1. Après une violation se produit, cliquez à droite sur l’entrée de diagnostic dans la liste d’erreurs.

2. Dans le menu contextuelle, sélectionnez **La sévérité De l’ensemble.**

   ![Configurer la sévérité des règles à partir de la liste d’erreurs dans Visual Studio](media/configure-rule-severity-error-list.png)

3. À partir de là, sélectionnez l’une des options de gravité.

   Visual Studio ajoute une entrée au fichier EditorConfig pour configurer la règle au niveau demandé.

   > [!TIP]
   > Si vous n’avez pas déjà de fichier EditorConfig dans le projet, Visual Studio en crée un pour vous.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Définir la sévérité des règles de Solution Explorer

1. Dans Solution Explorer, étendre**les analyseurs de** **références** > (ou **analyseurs de dépendances** > pour**les** projets de base .NET).

2. Élargissez l’assemblage qui contient la règle pour laquelle vous souhaitez définir la sévérité.

::: moniker range=">=vs-2019"
3. Cliquez à droite sur la règle et sélectionnez **la sévérité de l’ensemble**. Dans le menu contexte, sélectionnez l’une des options de gravité.

   Visual Studio ajoute une entrée au fichier EditorConfig pour configurer la règle au niveau demandé. Si votre projet utilise un fichier de règles au lieu d’un fichier EditorConfig, l’entrée de gravité est ajoutée au fichier de l’ensemble des règles.

   > [!TIP]
   > Si vous n’avez pas déjà de fichier EditorConfig ou d’un fichier de règles dans le projet, Visual Studio crée un nouveau fichier EditorConfig pour vous.
::: moniker-end

::: moniker range="vs-2017"
3. Cliquez à droite sur la règle et sélectionnez **La sévérité de l’ensemble des règles**. Dans le menu contexte, sélectionnez l’une des options de gravité.

   La sévérité de la règle est enregistrée dans le fichier de l’ensemble des règles actives.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Définir la sévérité des règles dans le fichier établi par les règles

![Fichier réglé de règle dans Solution Explorer](media/ruleset-in-solution-explorer.png)

1. Ouvrez le fichier de la règle active en le cliquant en double dans **Solution Explorer**, en sélectionnant Open Active **Rule Set** sur le menu à clic droit du nœud**d’analyse des** **références,** > ou en sélectionnant **Open** sur la page de propriété **d’analyse de code** pour le projet.

   Si c’est la première fois que vous modifiez l’ensemble de règles, Visual Studio fait une copie du fichier défini par défaut, le nomme * \<nom de projet>.ruleset*, et l’ajoute à votre projet. Cet ensemble de règles personnalisées devient également la règle active définie pour votre projet.

   > [!NOTE]
   > .NET Core et .NET Standard projets ne prennent pas en charge les commandes de menu pour les ensembles de règles dans **Solution Explorer**, par exemple, Open Active **Rule Set**. Pour spécifier une règle de non-défaut définie pour un projet .NET Core ou .NET Standard, ajoutez manuellement [la propriété **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) au fichier du projet. Vous pouvez toujours configurer les règles dans la règle définie dans l’interface utilisateur de l’éditeur de l’éditeur Visual Studio.

1. Naviguez jusqu’à la règle en élargissant son assemblage contenant.

1. Dans la colonne **Action,** sélectionnez la valeur pour ouvrir une liste d’abandon et sélectionnez la sévérité souhaitée dans la liste.

   ![Fichier réglé de règle ouvert dans l’éditeur](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Supprimer les violations

Il existe de multiples façons de supprimer les violations des règles :

::: moniker range=">=vs-2019"

- Dans un **fichier EditorConfig**

  Définir la `none`sévérité à , par exemple, `dotnet_diagnostic.CA1822.severity = none`.

- Du menu **Analyze**

  Sélectionnez **Analysez** > **et supprimez les problèmes actifs** sur la barre du menu pour supprimer toutes les violations actuelles. C’est ce qu’on appelle parfois le « baslining ».

::: moniker-end

::: moniker range="vs-2017"

- Du menu **Analyze**

  Sélectionnez **Analyse de** > **code d’exécution et supprimez les problèmes actifs** sur la barre du menu pour supprimer toutes les violations actuelles. C’est ce qu’on appelle parfois le « baslining ».

::: moniker-end

- De **Solution Explorer**

  Définissez la sévérité de la règle à **Aucun**.

- De **l’éditeur de l’ensemble de règles**

  Décochez la boîte à côté de son nom ou **définissez Action** to **None**.

- De **l’éditeur** de code

  Placez le curseur dans la ligne de code avec la violation et appuyez sur **Ctrl**+**Period (.)** pour ouvrir le menu **Actions rapides.** Sélectionnez **Supprimer CAXXXX** > **dans le fichier Source/in Suppression**.

  ![Supprimer le diagnostic à partir d’un menu d’actions rapides](media/suppress-diagnostic-from-editor.png)

- De la **liste d’erreurs**

  Sélectionnez les règles que vous souhaitez supprimer, puis cliquez à droite et **sélectionnez Supprimer** > **dans le fichier Source/In Suppression**.

  - Si vous supprimez **In Source**, le dialogue **Preview Changes** s’ouvre et affiche un aperçu de l’avertissement de [#pragma](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) ou de la directive [d’avertissement visual](/dotnet/visual-basic/language-reference/directives/directives) basic #Disable qui est ajouté au code source.

    ![Aperçu de l’ajout d'#pragma avertissement dans le fichier de code](media/pragma-warning-preview.png)

  - Si vous sélectionnez **Dans le fichier de suppression**, le dialogue Preview **Changes** s’ouvre et affiche un aperçu de l’attribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> qui est ajouté au fichier global de suppressions.

    ![Aperçu de l’ajout de l’attribut SuppressMessage au fichier de suppression](media/preview-changes-in-suppression-file.png)

  Dans le dialogue **de modifications d’aperçu,** **sélectionnez Appliquer**.

  > [!NOTE]
  > Si vous ne voyez pas l’option de menu **Suppress** dans **Solution Explorer**, la violation est susceptible de venir de la construction et non pas l’analyse en direct. La **liste d’erreurs** affiche les diagnostics, ou violations des règles, à partir de l’analyse et de la construction de code en direct. Depuis les diagnostics de construction peut être obsolète, par exemple, si vous avez modifié le code pour corriger la violation, mais n’ont pas reconstruit, vous ne pouvez pas supprimer ces diagnostics de la **liste d’erreurs**. Les diagnostics de l’analyse en direct, ou IntelliSense, sont toujours à jour avec les sources actuelles et peuvent être supprimés de la **liste d’erreurs**. Pour exclure *les* diagnostics de construction de votre sélection, passez le filtre source **de la liste d’erreurs** de **Build - IntelliSense** à **IntelliSense uniquement**. Ensuite, sélectionnez les diagnostics que vous voulez supprimer et procéder comme décrit précédemment.
  >
  > ![Filtre source Error List dans Visual Studio](media/error-list-filter.png)

## <a name="command-line-usage"></a>Utilisation de la ligne de commandement

Lorsque vous construisez votre projet à la ligne de commande, des violations des règles apparaissent dans la sortie de construction si les conditions suivantes sont remplies :

- Les analyseurs sont installés comme un paquet NuGet et non pas comme une extension VSIX.

- Une ou plusieurs règles sont violées dans le code du projet.

- La [sévérité](#rule-severity) d’une règle violée est réglée soit à **l’avertissement**, dans lequel les violations de cas ne causent pas la construction à l’échec, ou **l’erreur**, dans quel cas les violations causent la construction à l’échec.

La verbosité de la production de construction n’affecte pas si des violations des règles sont montrées. Même avec la verbosité **tranquille,** des violations des règles apparaissent dans la sortie de construction.

> [!TIP]
> Si vous êtes habitué à exécuter l’analyse de l’héritage de la ligne de commande, soit avec *FxCopCmd.exe* ou par msbuild avec le drapeau **RunCodeAnalysis,** voici comment le faire avec les analyseurs de code.

Pour voir les violations de l’analyseur à la ligne de commande lorsque vous construisez votre projet à l’aide de msbuild, exécutez une commande comme celle-ci :

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

L’image suivante montre la sortie de construction de la ligne de commande de la construction d’un projet qui contient une violation de règle d’analyseur :

![Sortie MSBuild avec violation de règle](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Projets dépendants

Dans un projet .NET Core, si vous ajoutez une référence à un projet qui a des analyseurs NuGet, ces analyseurs sont automatiquement ajoutés au projet dépendant aussi. Pour désactiver ce comportement, par exemple si le projet dépendant est un projet de test unitaire, marquez le paquet NuGet comme privé dans le fichier *.csproj* ou *.vbproj* du projet référencé en définissant l’attribut **PrivateAssets** :

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Voir aussi

- [Aperçu des analyseurs de code dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Soumettre un bogue d’analyseur de code](https://github.com/dotnet/roslyn-analyzers/issues)
- [Utiliser des ensembles de règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Supprimer les avertissements d’analyse de code](../code-quality/in-source-suppression-overview.md)
