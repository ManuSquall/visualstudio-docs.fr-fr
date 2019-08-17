---
title: Gravité et suppression de la règle de l’analyseur
ms.date: 03/26/2019
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
ms.openlocfilehash: 6362d3f14065aaf9661e85266753642e4201ca48
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548039"
---
# <a name="use-code-analyzers"></a>Utiliser des analyseurs de code

Les analyseurs de code .NET Compiler Platform («Roslyn») C# analysent votre code ou Visual Basic au fur et à mesure que vous tapez. Chaque *diagnostic* ou règle a un état de gravité et de suppression par défaut qui peut être remplacé pour votre projet. Cet article traite de la définition de la gravité d’une règle, de l’utilisation d’ensembles de règles et de la suppression des violations.

## <a name="analyzers-in-solution-explorer"></a>Analyseurs en Explorateur de solutions

Vous pouvez effectuer une grande partie de la personnalisation des diagnostics de l’analyseur à partir de **Explorateur de solutions**. Si vous [Installez](../code-quality/install-roslyn-analyzers.md) des analyseurs en tant que package NuGet , un nœud analyseurs apparaît sous le nœud **références** ou **dépendances** dans **Explorateur de solutions**. Si vous développez des **analyseurs**, puis que vous développez l’un des assemblys de l’analyseur, vous voyez tous les diagnostics dans l’assembly.

![Nœud analyseurs dans Explorateur de solutions](media/analyzers-expanded-in-solution-explorer.png)

Vous pouvez afficher les propriétés d’un diagnostic, notamment sa description et sa gravité par défaut, dans la fenêtre **Propriétés** . Pour afficher les propriétés, cliquez avec le bouton droit sur la règle et sélectionnez **Propriétés**, ou sélectionnez la règle et appuyez sur **ALT**+**entrée**.

![Propriétés de diagnostic dans Fenêtre Propriétés](media/analyzer-diagnostic-properties.png)

Pour afficher la documentation en ligne d’un diagnostic, cliquez avec le bouton droit sur le diagnostic, puis sélectionnez **afficher l’aide**.

Les icônes en regard de chaque diagnostic dans **Explorateur de solutions** correspondent aux icônes que vous voyez dans l’ensemble de règles lorsque vous l’ouvrez dans l’éditeur:

- le «i» d’un cercle indique une [gravité](#rule-severity) d' **information**
- le «!» dans un triangle indique une [gravité](#rule-severity) d' **Avertissement**
- le «x» d’un cercle indique une [gravité](#rule-severity) d' **erreur**
- le «i» dans un cercle sur un arrière-plan de couleur claire indique un niveau de [gravité](#rule-severity) **masqué**
- la flèche pointant vers le bas dans un cercle indique que le diagnostic est supprimé

![Icônes de diagnostics dans Explorateur de solutions](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>Ensembles de règles

Un [ensemble de règles](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) est un fichier XML qui stocke l’état de gravité et de suppression pour les diagnostics individuels.

> [!NOTE]
> Les ensembles de règles peuvent inclure des règles provenant à la fois des analyses héritées et des analyseurs de code.

Pour modifier l’ensemble de règles actif dans l’éditeur d’ensembles de règles, cliquez avec le bouton droit sur le nœud analyseurs de **références** > dans **Explorateur de solutions** et sélectionnez **ouvrir l’ensemble de règles actif**. Si c’est la première fois que vous modifiez l’ensemble de règles, Visual Studio effectue une copie du fichier de l’ensemble de règles par défaut, le nomme  *\<ProjectName >. RuleSet*et l’ajoute à votre projet. Cet ensemble de règles personnalisé devient également l’ensemble de règles actif pour votre projet.

Pour modifier l’ensemble de règles actif pour un projet, accédez à l’onglet **analyse du code** des propriétés d’un projet. Sélectionnez l’ensemble de règles dans la liste sous **exécuter cet ensemble de règles**. Pour ouvrir l’ensemble de règles, sélectionnez **ouvrir**.

> [!NOTE]
> Les projets .NET Core et .NET Standard ne prennent pas en charge les commandes de menu pour les ensembles de règles dans **Explorateur de solutions**, par exemple, **ouvrir l’ensemble de règles actif**. Pour spécifier un ensemble de règles non défini par défaut pour un projet .NET Core ou .NET Standard, [Ajoutez manuellement la propriété **CodeAnalysisRuleSet** ](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) au fichier projet. Vous pouvez toujours configurer les règles dans l’ensemble de règles dans l’interface utilisateur de l’éditeur d’ensembles de règles de Visual Studio.

## <a name="rule-severity"></a>Gravité des règles

Vous pouvez configurer la gravité des règles de l’analyseur, ou Diagnostics, si vous [Installez les analyseurs](../code-quality/install-roslyn-analyzers.md) en tant que package NuGet. Le tableau suivant présente les options de gravité pour les Diagnostics:

|Gravité|Comportement au moment de la génération|Comportement de l’éditeur|
|-|-|-|
|Error|Les violations apparaissent comme des *Erreurs* dans les **liste d’erreurs** et dans la sortie de la génération en ligne de commande, et entraînent l’échec des builds.|Le code incriminé est souligné d’un trait ondulé rouge et marqué d’une petite zone rouge dans la barre de défilement.|
|Warning|Les violations apparaissent en tant qu' *avertissements* dans le **liste d’erreurs** et dans la sortie de la génération en ligne de commande, mais ne provoquent pas l’échec des builds.|Le code incriminé est souligné d’un trait ondulé vert et marqué d’une petite zone verte dans la barre de défilement.|
|Info|Les violations apparaissent sous la forme de *messages* dans le **liste d’erreurs**, et pas du tout dans la sortie de la génération de la ligne de commande.|Le code incriminé est souligné d’un trait ondulé gris, et marqué d’une petite zone grise dans la barre de défilement.|
|Hidden|Non visible par l’utilisateur.|Non visible par l’utilisateur. Toutefois, le diagnostic est signalé au moteur de diagnostic IDE.|
|Aucun.|Entièrement supprimée.|Entièrement supprimée.|

En outre, vous pouvez «réinitialiser» la gravité d’une règle en lui affectant la **valeur par défaut**. Chaque diagnostic a une gravité par défaut qui peut être affichée dans la fenêtre **Propriétés** .

La capture d’écran suivante montre trois violations de diagnostics différentes dans l’éditeur de code, avec trois gravités différentes. Notez la couleur du trait ondulé, ainsi que la petite zone de la barre de défilement à droite.

![Erreur, avertissement et violation d’informations dans l’éditeur de code](media/diagnostics-severity-colors.png)

La capture d’écran suivante montre les trois mêmes violations qui apparaissent dans le **liste d’erreurs**:

![Erreur, avertissement et violation d’informations dans Liste d’erreurs](media/diagnostics-severities-in-error-list.png)

Vous pouvez modifier la gravité d’une règle à partir d' **Explorateur de solutions**, ou dans le  *\<fichier nom_projet >. RuleSet* ajouté à la solution après avoir modifié la gravité d’une règle dans **Explorateur de solutions**.

![Fichier d’ensemble de règles dans Explorateur de solutions](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>Définir la gravité de la règle à partir d’Explorateur de solutions

1. Dans **Explorateur de solutions**, développez **références** > **Analysis** (**analyseurs** de**dépendances** > pour les projets .net Core).

1. Développez l’assembly qui contient la règle pour laquelle vous souhaitez définir la gravité.

1. Cliquez avec le bouton droit sur la règle et sélectionnez définir la gravité de l' **ensemble de règles**. Dans le menu volant, sélectionnez l’une des options de gravité.

   La gravité de la règle est enregistrée dans le fichier de l’ensemble de règles actif.

### <a name="set-rule-severity-in-the-rule-set-file"></a>Définir la gravité de la règle dans le fichier d’ensemble de règles

1. Ouvrez le fichier d' [ensemble de règles](analyzer-rule-sets.md) en double-cliquant dessus dans **Explorateur de solutions**, en sélectionnant Ouvrir l' **ensemble de règles actif** dans le menu contextuel du nœud analyseurs, ou en sélectionnant **ouvrir** sur la page de propriétés **analyse du code** pour projet.

1. Accédez à la règle en développant son assembly conteneur.

1. Dans la colonne **action** , sélectionnez la valeur pour ouvrir une liste déroulante, puis sélectionnez la gravité souhaitée dans la liste.

   ![Fichier d’ensemble de règles ouvert dans l’éditeur](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>Supprimer les violations

Il existe plusieurs façons de supprimer des violations de règle:

- Dans le menu **analyser**

  Sélectionnez **analyser** > **exécuter l’analyse du code et supprimer les problèmes actifs** dans la barre de menus pour supprimer toutes les violations en cours. Cette opération est parfois appelée «ligne de l’établissement».

- À partir de **Explorateur de solutions**

  Pour supprimer une violation dans **Explorateur de solutions**, définissez le niveau de gravité de la règle sur **aucun**.

- À partir de l' **éditeur d’ensembles de règles**

  Pour supprimer une violation de l’éditeur d’ensemble de règles, désactivez la case à cocher en regard de son nom, ou définissez **action** sur **aucun**.

- À partir de l' **éditeur de code**

  Pour supprimer une violation de l’éditeur de code, placez le curseur dans la ligne de code avec la violation et appuyez sur **CTRL**+ **.** pour ouvrir le menu **actions rapides** . Sélectionnez **supprimer CAXXXX** > **dans le fichier source/de suppression**.

  ![Supprimer les diagnostics du menu actions rapides](media/suppress-diagnostic-from-editor.png)

- À partir de la **liste d’erreurs**

  Vous pouvez supprimer un ou plusieurs Diagnostics de la **liste d’erreurs** en sélectionnant ceux que vous voulez supprimer, puis en cliquant avec le bouton droit et en sélectionnant **supprimer** > **dans le fichier source/de suppression**.

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

Lorsque vous générez votre projet sur la ligne de commande, des violations de règle apparaissent dans la sortie de la génération si les conditions suivantes sont remplies:

- Les analyseurs sont installés en tant que package NuGet et non pas en tant qu’extension VSIX.

- Une ou plusieurs règles sont enfreintes dans le code du projet.

- La [gravité](#rule-severity) d’une règle non respectée est définie sur **Avertissement**. dans ce cas, les violations ne provoquent pas l’échec de la génération, ou une **erreur**, auquel cas les violations provoquent l’échec de la génération.

Le niveau de détail de la sortie de la génération n’a aucune incidence sur l’affichage des violations de règle. Même avec un niveau de détail **silencieux** , les violations de règle apparaissent dans la sortie de la génération.

> [!TIP]
> Si vous êtes habitué à exécuter des analyses héritées à partir de la ligne de commande, soit avec *FxCopCmd. exe* , soit via MSBuild avec l’indicateur **RunCodeAnalysis** , voici comment procéder avec les analyseurs de code.

Pour voir les violations de l’analyseur sur la ligne de commande lorsque vous générez votre projet à l’aide de MSBuild, exécutez une commande comme celle-ci:

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

L’illustration suivante montre la sortie de la génération en ligne de commande de la génération d’un projet qui contient une violation de règle de l’analyseur:

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
