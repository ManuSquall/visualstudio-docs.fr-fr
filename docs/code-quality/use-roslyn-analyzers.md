---
title: Configuration des analyseurs
ms.date: 05/10/2021
description: Découvrez comment personnaliser les règles de l’analyseur Roslyn. Découvrez comment ajuster les gravités de l’analyseur, supprimer les violations et désigner les fichiers comme du code généré.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 36a9f1651a4aef7742b6bf52f8691f6ae8f9c616
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973380"
---
# <a name="overview"></a>Vue d’ensemble

Chaque *outil de diagnostic* ou de règle de l’analyseur Roslyn a un état de gravité et de suppression par défaut qui peut être remplacé et personnalisé pour votre projet. Cet article traite de la définition des gravités de l’analyseur et de la suppression des violations de l’analyseur.

## <a name="configure-severity-levels"></a>Configurer les niveaux de gravité

::: moniker range=">=vs-2019"

À compter de Visual Studio 2019 version 16,3, vous pouvez configurer le niveau de gravité des règles de l’analyseur ou des *Diagnostics* dans un [fichier EditorConfig](#set-rule-severity-in-an-editorconfig-file), à partir du [menu ampoule](#set-rule-severity-from-the-light-bulb-menu), puis dans la liste d’erreurs.

::: moniker-end

::: moniker range="vs-2017"

Vous pouvez configurer la gravité des règles de l’analyseur, ou *Diagnostics*, si vous [Installez les analyseurs](../code-quality/install-roslyn-analyzers.md) en tant que package NuGet. Vous pouvez modifier la gravité d’une règle [à partir Explorateur de solutions](#set-rule-severity-from-solution-explorer) ou [dans un fichier d’ensemble de règles](#set-rule-severity-in-the-rule-set-file).

::: moniker-end

Le tableau suivant présente les différentes options de gravité :

| Gravité (Explorateur de solutions) | Gravité (fichier EditorConfig) | Comportement au moment de la génération | Comportement de l’éditeur |
|-|-|-|
| Erreur | `error` | Les violations apparaissent comme des *Erreurs* dans les liste d’erreurs et dans la sortie de la génération en ligne de commande, et entraînent l’échec des builds.| Le code incriminé est souligné d’un tilde rouge et marqué d’une petite zone rouge dans la barre de défilement. |
| Avertissement | `warning` | Les violations apparaissent en tant qu' *avertissements* dans le liste d’erreurs et dans la sortie de la génération en ligne de commande, mais ne provoquent pas l’échec des builds. | Le code incriminé est souligné d’un tilde vert et est marqué d’un petit cadre vert dans la barre de défilement. |
| Informations | `suggestion` | Les violations apparaissent sous la forme de *messages* dans le liste d’erreurs, et pas du tout dans la sortie de la génération de la ligne de commande. | Le code incriminé est souligné d’un tilde gris et marqué d’une petite zone grise dans la barre de défilement. |
| Hidden | `silent` | Non visible par l’utilisateur. | Non visible par l’utilisateur. Toutefois, le diagnostic est signalé au moteur de diagnostic IDE. |
| Aucun | `none` | Entièrement supprimée. | Entièrement supprimée. |
| Default | `default` | Correspond à la gravité par défaut de la règle. Pour déterminer la valeur par défaut d’une règle, recherchez dans la Fenêtre Propriétés. | Correspond à la gravité par défaut de la règle. |

Si des violations de règle sont détectées par un analyseur, elles sont signalées dans l’éditeur de code (sous forme de *tilde* sous le code incriminé) et dans la fenêtre de liste d’erreurs.

Les violations de l’analyseur signalées dans la liste d’erreurs correspondent au [paramètre de niveau de gravité](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) de la règle. Les violations de l’analyseur s’affichent également dans l’éditeur de code sous forme de tildes sous le code incriminé. L’illustration suivante montre trois violations d' &mdash; une erreur (tilde rouge), un avertissement (tilde vert) et une suggestion (trois points gris) :

![Tildes dans l’éditeur de code dans Visual Studio](media/diagnostics-severity-colors.png)

La capture d’écran suivante montre les trois mêmes violations qui apparaissent dans le Liste d’erreurs :

![Erreur, avertissement et violation d’informations dans Liste d’erreurs](media/diagnostics-severities-in-error-list.png)

De nombreuses règles de l’analyseur, ou *Diagnostics*, ont une ou plusieurs *corrections de code* associées que vous pouvez appliquer pour corriger la violation de règle. Les correctifs de code sont affichés dans l’icône du menu Ampoule, avec d’autres types d’[Actions rapides](../ide/quick-actions.md). Pour plus d’informations sur ces correctifs de code, consultez [Actions rapides courantes](../ide/quick-actions.md).

![Violation d’analyseur et correctif de code par action rapide](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>Gravité « masqué » par rapport à la gravité « aucun »

`Hidden` les règles de gravité qui sont activées par défaut sont différentes des règles de gravité ou de désactivation `None` de deux façons.

- Si un correctif de code a été enregistré pour une `Hidden` règle de gravité, le correctif est proposé en tant qu’action de refactorisation du code de l’ampoule légère dans Visual Studio, même si le diagnostic masqué n’est pas visible pour l’utilisateur. Ce n’est pas le cas pour les règles de gravité désactivée `None` .
- `Hidden` les règles de gravité peuvent être configurées en bloc par des entrées qui [définissent une gravité de règle pour plusieurs règles d’analyseur à la fois dans un fichier EditorConfig](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file). `None` les règles de gravité ne peuvent pas être configurées de cette manière. Au lieu de cela, ils doivent être configurés via des entrées qui [définissent la gravité de la règle dans un fichier EditorConfig pour chaque ID de règle](#set-rule-severity-in-an-editorconfig-file).

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>Définir la gravité de la règle dans un fichier baEditorConfig

(Visual Studio 2019 version 16,3 et versions ultérieures)

Vous pouvez définir la gravité des avertissements du compilateur ou des règles de l’analyseur dans un fichier EditorConfig à l’aide de la syntaxe suivante :

`dotnet_diagnostic.<rule ID>.severity = <severity>`

La définition de la gravité d’une règle dans un fichier baEditorConfig est prioritaire sur toute gravité définie dans un ensemble de règles ou dans Explorateur de solutions. Vous pouvez configurer [manuellement](#manually-configure-rule-severity-in-an-editorconfig-file) la gravité dans un fichier baEditorConfig ou [automatiquement](#set-rule-severity-from-the-light-bulb-menu) par le biais de l’ampoule qui s’affiche en regard d’une violation.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>Définir une gravité de règle pour plusieurs règles d’analyseur à la fois dans un fichier EditorConfig

(Visual Studio 2019 version 16,5 et versions ultérieures)

Vous pouvez définir la gravité d’une catégorie spécifique de règles de l’analyseur ou de toutes les règles de l’analyseur à l’aide d’une seule entrée dans un fichier EditorConfig.

- Définir la gravité de la règle pour une catégorie de règles de l’analyseur :

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- Définir la gravité de la règle pour toutes les règles de l’analyseur :

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> Les entrées permettant de configurer plusieurs règles de l’analyseur à la fois s’appliquent uniquement aux règles qui sont *activées par défaut*. Les règles de l’analyseur marquées comme désactivées par défaut dans le package de l’analyseur doivent être activées via des entrées explicites `dotnet_diagnostic.<rule ID>.severity = <severity>` .

Si vous avez plusieurs entrées applicables à un ID de règle spécifique, voici l’ordre de priorité pour choisir l’entrée applicable :

- L’entrée de gravité pour une règle individuelle par ID est prioritaire sur l’entrée de gravité pour une catégorie.
- L’entrée de gravité pour une catégorie est prioritaire sur l’entrée de gravité pour toutes les règles de l’analyseur.

Prenons l’exemple de EditorConfig suivant, où [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) a la catégorie « performance » :

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

Dans l’exemple précédent, les trois entrées s’appliquent à CA1822. Toutefois, à l’aide des règles de précédence spécifiées, la première entrée de gravité basée sur l’ID de la règle gagne sur les entrées suivantes. Dans cet exemple, CA1822 aura une gravité effective de « Error ». Toutes les règles restantes avec la catégorie « performance » ont une gravité « Avertissement ». Toutes les règles d’analyse restantes, qui n’ont pas la catégorie « performance », auront une « suggestion » de gravité.

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>Configurer manuellement la gravité de la règle dans un fichier baEditorConfig

1. Si vous n’avez pas encore de fichier EditorConfig pour votre projet, ajoutez-en [un](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Ajoutez une entrée pour chaque règle que vous souhaitez configurer sous l’extension de fichier correspondante. Par exemple, pour définir la gravité de [CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) sur `error` pour les fichiers C#, l’entrée ressemble à ce qui suit :

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> Pour les analyseurs de style de code IDE, vous pouvez également les configurer dans un fichier EditorConfig à l’aide d’une syntaxe différente, par exemple, `dotnet_style_qualification_for_field = false:suggestion` . Toutefois, si vous définissez une gravité à l’aide de la `dotnet_diagnostic` syntaxe, elle est prioritaire. Pour plus d’informations, consultez [conventions de langage pour EditorConfig](/dotnet/fundamentals/code-analysis/style-rules/language-rules).

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>Définir la gravité de la règle à partir du menu ampoule

Visual Studio offre un moyen pratique de configurer le niveau de gravité d’une règle à partir du menu de l’ampoule [actions rapides](../ide/quick-actions.md) .

1. Une fois qu’une violation se produit, placez le curseur sur le tilde de violation dans l’éditeur et ouvrez le menu ampoule. Ou placez votre curseur sur la ligne et appuyez sur **CTRL** + **.** (point).

2. Dans le menu ampoule, sélectionnez **configurer ou supprimer les problèmes** > **configurer la \<rule ID> gravité**.

   ![Configurer la gravité de la règle à partir du menu ampoule dans Visual Studio](media/configure-rule-severity.png)

3. À partir de là, choisissez l’une des options de gravité.

   ![Configurer la gravité de la règle comme suggestion](media/configure-rule-severity-suggestion.png)

   Visual Studio ajoute une entrée au fichier EditorConfig pour configurer la règle au niveau demandé, comme indiqué dans la zone Aperçu.

   > [!TIP]
   > Si vous n’avez pas encore de fichier EditorConfig dans le projet, Visual Studio en crée un pour vous.

### <a name="set-rule-severity-from-the-error-list-window"></a>Définir la gravité de la règle à partir de la fenêtre Liste d’erreurs

Visual Studio offre également un moyen pratique de configurer la gravité d’une règle à partir du menu contextuel de la liste d’erreurs.

1. Une fois la violation effectuée, cliquez avec le bouton droit sur l’entrée de diagnostic dans la liste d’erreurs.

2. Dans le menu contextuel, sélectionnez **définir la gravité**.

   ![Configurer la gravité de la règle à partir d’une liste d’erreurs dans Visual Studio](media/configure-rule-severity-error-list.png)

3. À partir de là, choisissez l’une des options de gravité.

   Visual Studio ajoute une entrée au fichier EditorConfig pour configurer la règle au niveau demandé.

   > [!TIP]
   > Si vous n’avez pas encore de fichier EditorConfig dans le projet, Visual Studio en crée un pour vous.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Définir la gravité de la règle à partir d’Explorateur de solutions

Vous pouvez effectuer une grande partie de la personnalisation des diagnostics de l’analyseur à partir de **Explorateur de solutions**. Si vous [Installez des analyseurs](../code-quality/install-roslyn-analyzers.md) en tant que package NuGet, un nœud **analyseurs** apparaît sous le nœud **références** ou **dépendances** dans **Explorateur de solutions**. Si vous développez des **analyseurs**, puis que vous développez l’un des assemblys de l’analyseur, vous voyez tous les diagnostics dans l’assembly.

![Nœud analyseurs dans Explorateur de solutions](media/analyzers-expanded-in-solution-explorer.png)

Vous pouvez afficher les propriétés d’un diagnostic, notamment sa description et sa gravité par défaut, dans la fenêtre **Propriétés** . Pour afficher les propriétés, cliquez avec le bouton droit sur la règle et sélectionnez **Propriétés**, ou sélectionnez la règle et appuyez sur **ALT** + **entrée**.

![Propriétés de diagnostic dans Fenêtre Propriétés](media/analyzer-diagnostic-properties.png)

Pour afficher la documentation en ligne d’un diagnostic, cliquez avec le bouton droit sur le diagnostic, puis sélectionnez **afficher l’aide**.

Les icônes en regard de chaque diagnostic dans **Explorateur de solutions** correspondent aux icônes que vous voyez dans l’ensemble de règles lorsque vous l’ouvrez dans l’éditeur :

- le « x » d’un cercle indique une [gravité](#configure-severity-levels) d' **erreur**
- le «  ! » dans un triangle indique une [gravité](#configure-severity-levels) d' **Avertissement**
- le « i » d’un cercle indique une [gravité](#configure-severity-levels) d' **information**
- le « i » dans un cercle sur un arrière-plan de couleur claire indique un niveau de [gravité](#configure-severity-levels) **masqué**
- la flèche pointant vers le bas dans un cercle indique que le diagnostic est supprimé

![Icônes de diagnostics dans Explorateur de solutions](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>Convertir un fichier RuleSet existant en fichier EditorConfig

À compter de Visual Studio 2019 version 16,5, les fichiers RuleSet sont dépréciés en faveur du fichier EditorConfig pour la configuration de l’analyseur pour le code managé. La plupart des outils Visual Studio pour la configuration de gravité de la règle de l’analyseur ont été mis à jour pour fonctionner sur des fichiers EditorConfig au lieu de fichiers RuleSet. Les fichiers EditorConfig vous permettent de configurer les gravités et les options de l’analyseur de règle de l’analyseur, y compris les options de style de code de l’IDE Visual Studio. Il est fortement recommandé de convertir votre fichier RuleSet existant en fichier baEditorConfig. Il est également recommandé d’enregistrer le fichier EditorConfig à la racine de votre référentiel ou dans le dossier de la solution. En utilisant la racine de votre dossier de référentiel ou de solution, vous vous assurez que les paramètres de gravité de ce fichier sont appliqués automatiquement à la totalité du référentiel ou de la solution, respectivement.

Il existe deux façons de convertir un fichier RuleSet existant en fichier EditorConfig :

- À partir de l’éditeur de RuleSet dans Visual Studio (requiert Visual Studio 2019 16,5 ou version ultérieure). Si votre projet utilise déjà un fichier RuleSet spécifique en tant que `CodeAnalysisRuleSet` , vous pouvez le convertir en un fichier EditorConfig équivalent à partir de l’éditeur RuleSet dans Visual Studio.

    1. Double-cliquez sur le fichier ruleset dans Explorateur de solutions.

       Le fichier RuleSet doit s’ouvrir dans l’éditeur RuleSet. Vous devez voir une barre d' **informations** cliquable en haut de l’éditeur de RuleSet.

       ![Convertir un ensemble de règles en fichier baEditorConfig dans l’éditeur RuleSet](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. Sélectionnez le lien de la **barre d’informations** .

       Une boîte de dialogue **Enregistrer sous** s’ouvre et vous permet de sélectionner le répertoire dans lequel vous souhaitez générer le fichier EditorConfig.

    3. Sélectionnez le bouton **Enregistrer** pour générer le fichier EditorConfig.

       Le EditorConfig généré doit s’ouvrir dans l’éditeur. En outre, la propriété MSBuild `CodeAnalysisRuleSet` est mise à jour dans le fichier projet afin qu’elle ne référence plus le fichier RuleSet d’origine.

- Depuis la ligne de commande :

    1. Installez le package NuGet [Microsoft. CodeAnalysis. RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. Exécutez `RulesetToEditorconfigConverter.exe` à partir du package installé, avec les chemins d’accès au fichier RuleSet et au fichier EditorConfig en tant qu’arguments de ligne de commande.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

Voici un exemple de fichier RuleSet à convertir :

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

Voici le fichier EditorConfig converti :

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
::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>Définir la gravité de la règle à partir d’Explorateur de solutions

1. Dans Explorateur de solutions, développez **références**  >  **analyseurs** (ou   >  **analyseurs** de dépendances pour les projets .net Core).

2. Développez l’assembly qui contient la règle pour laquelle vous souhaitez définir la gravité.

::: moniker range=">=vs-2019"
3. Cliquez avec le bouton droit sur la règle et sélectionnez **définir la gravité**. Dans le menu contextuel, choisissez l’une des options de gravité.

   Visual Studio ajoute une entrée au fichier EditorConfig pour configurer la règle au niveau demandé. Si votre projet utilise un fichier RuleSet au lieu d’un fichier EditorConfig, l’entrée de gravité est ajoutée au fichier RuleSet.

   > [!TIP]
   > Si vous ne disposez pas déjà d’un fichier EditorConfig ou d’un fichier ruleset dans le projet, Visual Studio crée un nouveau fichier EditorConfig pour vous.
::: moniker-end

::: moniker range="vs-2017"
3. Cliquez avec le bouton droit sur la règle et sélectionnez définir la gravité de l' **ensemble de règles**. Dans le menu contextuel, choisissez l’une des options de gravité.

   La gravité de la règle est enregistrée dans le fichier de l’ensemble de règles actif.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>Définir la gravité de la règle dans le fichier d’ensemble de règles

![Fichier d’ensemble de règles dans Explorateur de solutions](media/ruleset-in-solution-explorer.png)

1. Ouvrez le fichier de l’ensemble de règles actif de l’une des manières suivantes :

- Dans **Explorateur de solutions**, double-cliquez sur le fichier, cliquez avec le bouton droit sur le  >  nœud **analyseurs** de références, puis sélectionnez **ouvrir l’ensemble de règles actif**.
- Sur la page de propriétés **analyse du code** du projet, sélectionnez **ouvrir** .

  Si c’est la première fois que vous modifiez l’ensemble de règles, Visual Studio effectue une copie du fichier de l’ensemble de règles par défaut, le nomme *\<projectname> . RuleSet* et l’ajoute à votre projet. Cet ensemble de règles personnalisé devient également l’ensemble de règles actif pour votre projet.

   > [!NOTE]
   > Les projets .NET Core et .NET Standard ne prennent pas en charge les commandes de menu pour les ensembles de règles dans **Explorateur de solutions**, par exemple, **ouvrir l’ensemble de règles actif**. Pour spécifier un ensemble de règles non défini par défaut pour un projet .NET Core ou .NET Standard, [Ajoutez manuellement la propriété **CodeAnalysisRuleSet**](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) au fichier projet. Vous pouvez toujours configurer les règles dans l’ensemble de règles dans l’interface utilisateur de l’éditeur d’ensembles de règles de Visual Studio.

1. Accédez à la règle en développant son assembly conteneur.

1. Dans la colonne **action** , sélectionnez la valeur pour ouvrir une liste déroulante, puis choisissez la gravité souhaitée dans la liste.

   ![Fichier d’ensemble de règles ouvert dans l’éditeur](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>Configurer le code généré

Les analyseurs s’exécutent sur tous les fichiers sources d’un projet et signalent des violations sur ceux-ci. Toutefois, ces violations ne sont pas utiles sur les fichiers de code générés, tels que les fichiers de code générés par le concepteur, les fichiers sources temporaires générés par le système de génération, etc. Les utilisateurs ne peuvent pas modifier manuellement ces fichiers et/ou ne sont pas concernés par la correction de violations dans ces types de fichiers générés par les outils.

Par défaut, le pilote de l’analyseur exécutant des analyseurs traite les fichiers avec un nom, une extension de fichier ou un en-tête de fichier généré automatiquement en tant que fichiers de code générés. Par exemple, un nom de fichier se terminant par `.designer.cs` ou `.generated.cs` est considéré comme du code généré. Toutefois, ces heuristiques peuvent ne pas être en mesure d’identifier tous les fichiers de code générés personnalisés dans le code source de l’utilisateur.

À compter de Visual Studio 2019 16,5, les utilisateurs finaux peuvent configurer des fichiers et/ou des dossiers spécifiques à traiter comme du code généré dans un [fichier baEditorConfig](https://editorconfig.org/). Suivez les étapes ci-dessous pour ajouter une telle configuration :

1. Si vous n’avez pas encore de fichier EditorConfig pour votre projet, ajoutez-en [un](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

2. Ajoutez l' `generated_code = true | false` entrée pour des fichiers et/ou des dossiers spécifiques. Par exemple, pour traiter tous les fichiers dont le nom se termine par `.MyGenerated.cs` comme code généré, l’entrée est la suivante :

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>Supprimer les violations

Vous pouvez supprimer les violations de règle à l’aide de différentes méthodes. Pour plus d’informations, consultez [Supprimer les violations d’analyse du code](../code-quality/in-source-suppression-overview.md).

## <a name="command-line-usage"></a>Utilisation de la ligne de commande

Lorsque vous générez votre projet sur la ligne de commande, des violations de règle apparaissent dans la sortie de la génération si les conditions suivantes sont remplies :

- Les analyseurs sont installés avec le kit de développement logiciel (SDK) .NET ou en tant que package NuGet, et non en tant qu’extension VSIX.

  Pour les analyseurs installés à l’aide du kit de développement logiciel (SDK) .NET, vous devrez peut-être [activer les analyseurs](../code-quality/install-net-analyzers.md). Pour les styles de code, vous pouvez également [appliquer des styles de code sur la build](/dotnet/fundamentals/code-analysis/overview#code-style-analysis) en définissant une propriété MSBuild.

- Une ou plusieurs règles sont enfreintes dans le code du projet.

- La [gravité](#configure-severity-levels) d’une règle non respectée est définie sur **Avertissement**. dans ce cas, les violations ne provoquent pas l’échec de la génération, ou une **erreur**, auquel cas les violations provoquent l’échec de la génération.

Le niveau de détail de la sortie de la génération n’a aucune incidence sur l’affichage des violations de règle. Même avec un niveau de détail **silencieux** , les violations de règle apparaissent dans la sortie de la génération.

> [!TIP]
> Si vous êtes habitué à exécuter des analyses héritées à partir de la ligne de commande, avec *FxCopCmd.exe* ou via MSBuild avec l’indicateur **RunCodeAnalysis** , procédez comme suit avec des analyseurs de code.

Pour voir les violations de l’analyseur sur la ligne de commande lorsque vous générez votre projet à l’aide de MSBuild, exécutez une commande comme celle-ci :

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

L’illustration suivante montre la sortie de la génération en ligne de commande de la génération d’un projet qui contient une violation de règle de l’analyseur :

![Sortie MSBuild avec violation de règle](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>Projets dépendants

Dans un projet .NET Core, si vous ajoutez une référence à un projet qui a des analyseurs NuGet, ces analyseurs sont automatiquement ajoutés au projet dépendant. Pour désactiver ce comportement, par exemple si le projet dépendant est un projet de test unitaire, marquez le package NuGet comme privé dans le fichier *. csproj* ou *. vbproj* du projet référencé en définissant l’attribut **PrivateAssets** :

```xml
<PackageReference Include="Microsoft.CodeAnalysis.NetAnalyzers" Version="5.0.0" PrivateAssets="all" />
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des analyseurs de code dans Visual Studio](../code-quality/roslyn-analyzers-overview.md)
- [Soumettre un bogue de l’analyseur de code](https://github.com/dotnet/roslyn-analyzers/issues)
- [Utiliser des ensembles de règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [Supprimer les avertissements d’analyse du code](../code-quality/in-source-suppression-overview.md)
- [Options de configuration pour l’analyse du code (.NET)](/dotnet/fundamentals/code-analysis/configuration-options)
