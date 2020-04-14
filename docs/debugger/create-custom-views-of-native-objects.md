---
title: Créer des vues personnalisées d’objets C++
description: Utilisez le cadre Natvis pour personnaliser la façon dont Visual Studio affiche les types natifs dans le débagé
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8bdd8d26ba450b1aedd790d644c183607c44af
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224509"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Créez des vues personnalisées des objets CMD dans le débagénaire à l’aide du cadre Natvis

Le cadre Visual Studio *Natvis* personnalise la façon dont les types indigènes apparaissent dans les fenêtres variables de débbugger, telles que les **locals** et les fenêtres **watch,** et dans **DataTips**. Les visualisations Natvis peuvent aider à rendre les types que vous créez plus visibles lors du débogage.

Natvis remplace le fichier *autoexp.dat* dans les versions antérieures de Visual Studio par une syntaxe XML, de meilleurs diagnostics, version et prise en charge de fichiers multiples.

> [!NOTE]
> Les personnalisations Natvis fonctionnent avec les classes et les structs, mais pas les types.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Visualisations Natvis

Vous utilisez le cadre Natvis pour créer des règles de visualisation pour les types que vous créez, afin que les développeurs puissent les voir plus facilement lors du débogage.

Par exemple, l’illustration suivante montre une variable de type [Windows::UI:Xaml::Controls::TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) dans une fenêtre de débbugger sans aucune visualisation personnalisée appliquée.

![Visualisation TextBox par défaut](../debugger/media/dbg_natvis_textbox_default.png "Visualisation TextBox par défaut")

La ligne en surbrillance montre la propriété `Text` de la classe `TextBox` . La hiérarchie de classe complexe rend difficile la recherche de cette propriété. Le débbuggeur ne sait pas comment interpréter le type de chaîne personnalisée, de sorte que vous ne pouvez pas voir la chaîne tenue à l’intérieur de la boîte à texte.

La `TextBox` même apparence beaucoup plus simple dans la fenêtre variable lorsque les règles de visualisation personnalisée Natvis sont appliquées. Les membres importants de la classe apparaissent ensemble, et le débbuggeur montre la valeur sous-jacente de la chaîne du type de chaîne personnalisée.

![TextBox, données utilisant un visualiseur](../debugger/media/dbg_natvis_textbox_visualizer.png "TextBox, données utilisant un visualiseur")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Utilisez des fichiers .natvis dans les projets C

Natvis utilise des fichiers *.natvis* pour spécifier les règles de visualisation. Un fichier *.natvis* est un fichier XML avec une extension *.natvis.* Le schéma Natvis est défini en *%VSINSTALLDIR%-Xml-Schemas-natvis.xsd*.

La structure de base d’un fichier `Type` *.natvis* est un ou plusieurs éléments représentant les entrées de visualisation. Le nom entièrement `Type` qualifié de chaque `Name` élément est spécifié dans son attribut.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
  <Type Name="MyNamespace::CFoo">
    .
    .
  </Type>

  <Type Name="...">
    .
    .
  </Type>
</AutoVisualizer>
```

Visual Studio fournit quelques fichiers *.natvis* dans le *dossier %VSINSTALLDIR%-Common7-Packages-Debugger-Visualizers.* Ces fichiers ont des règles de visualisation pour de nombreux types communs, et peuvent servir d’exemples pour l’écriture de visualisations pour de nouveaux types.

### <a name="add-a-natvis-file-to-a-c-project"></a>Ajouter un fichier .natvis à un projet C

Vous pouvez ajouter un fichier *.natvis* à n’importe quel projet C.

**Pour ajouter un nouveau fichier *.natvis* :**

1. Sélectionnez le nœud de projet CMD dans **Solution Explorer**, et sélectionnez **Project** > **Ajouter un nouvel élément,** ou cliquer à droite sur le projet et **sélectionnez Ajouter** > **un nouvel élément**.

1. Dans le dialogue **Add New Item,** sélectionnez le fichier de visualisation **Visual CMD** > **Utility** > **Debugger (.natvis)**.

1. Nommez le fichier et sélectionnez **Ajouter**.

   Le nouveau fichier est ajouté à **Solution Explorer**, et s’ouvre dans le volet de document Visual Studio.

Le Visual Studio débagé de fichiers *.natvis* dans les projets Cmd automatiquement, et par défaut, les inclut également dans le fichier *.pdb* lorsque le projet est construit. Si vous déboisez l’application construite, le débbuggeur charge le fichier *.natvis* à partir du fichier *.pdb,* même si vous n’avez pas le projet ouvert. Si vous ne voulez pas le fichier *.natvis* inclus dans le *.pdb*, vous pouvez l’exclure du fichier *.pdb* construit.

**Pour exclure un fichier *.natvis* d’un *.pdb*:**

1. Sélectionnez le fichier *.natvis* dans **Solution Explorer**, et sélectionnez l’icône **Propriétés,** ou cliquez à droite sur le fichier et sélectionnez **les propriétés**.

1. Déposez la flèche à côté **de Excluded From Build** et sélectionnez **Oui,** puis sélectionnez **OK**.

>[!NOTE]
>Pour débogage des projets exécutables, utilisez les éléments de solution pour ajouter des fichiers *.natvis* qui ne sont pas dans le *.pdb*, puisqu’il n’y a pas de projet Cmd disponible.

>[!NOTE]
>Les règles Natvis chargées à partir d’un *.pdb* ne s’appliquent qu’aux types dans les modules auxquels le *.pdb* fait référence. Par exemple, si *Module1.pdb* a une entrée `Test`Natvis pour `Test` un type nommé, il ne s’applique qu’à la classe dans *Module1.dll*. Si un autre module définit `Test`également une classe nommée, *l’entrée De Natvis Module1.pdb* ne s’applique pas à elle.

**Pour installer et enregistrer un fichier *.natvis* via un forfait VSIX :**

Un forfait VSIX peut installer et enregistrer des fichiers *.natvis.* Peu importe où ils sont installés, tous les fichiers *.natvis* enregistrés sont automatiquement ramassés lors du débogage.

1. Inclure le fichier *.natvis* dans le paquet VSIX. Par exemple, pour le fichier de projet suivant :
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Enregistrez le fichier *.natvis* dans le fichier *source.extension.vsixmanifest:*
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Emplacements de fichiers Natvis

Vous pouvez ajouter des fichiers *.natvis* à votre répertoire utilisateur ou à un répertoire système, si vous voulez qu’ils s’appliquent à plusieurs projets.

Les fichiers *.natvis* sont évalués dans l’ordre suivant :

1. Tous les fichiers *.natvis* qui sont intégrés dans un *.pdb* vous débogage, sauf si un fichier du même nom existe dans le projet chargé.

2. Tous les fichiers *.natvis* qui sont dans un projet C chargé ou une solution de haut niveau. Ce groupe comprend tous les projets de C, y compris les bibliothèques de classe, mais pas les projets dans d’autres langues.

3. Tous les fichiers *.natvis* installés et enregistrés via un forfait VSIX.

::: moniker range="vs-2017"

4. L’annuaire Natvis spécifique à l’utilisateur (par exemple, *%USERPROFILE% -Documents-Visual Studio 2017-Visualizers*).

::: moniker-end

::: moniker range=">= vs-2019"

4. L’annuaire Natvis spécifique à l’utilisateur (par exemple, *%USERPROFILE% -Documents-Visual Studio 2019-Visualizers*).

::: moniker-end

5. Le répertoire Natvis à l'échelle du système (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Ce répertoire a les fichiers *.natvis* qui sont installés avec Visual Studio. Si vous avez des autorisations d’administrateur, vous pouvez ajouter des fichiers à cet annuaire.

## <a name="modify-natvis-files-while-debugging"></a>Modifier les fichiers .natvis tout en débogage

Vous pouvez modifier un fichier *.natvis* dans l’IDE tout en débogage de son projet. Ouvrez le fichier dans le même cas de Visual Studio avec lequel vous débugging, modifiez-le et enregistrez-le. Dès que le fichier est enregistré, la mise à jour des fenêtres **Watch** and **Locals** pour refléter le changement.

Vous pouvez également ajouter ou supprimer des fichiers *.natvis* dans une solution que vous débogage, et Visual Studio ajoute ou supprime les visualisations pertinentes.

Vous ne pouvez pas mettre à jour les fichiers *.natvis* qui sont intégrés dans les fichiers *.pdb* pendant que vous débugging.

Si vous modifiez le fichier *.natvis* en dehors de Visual Studio, les modifications ne prennent pas effet automatiquement. Pour mettre à jour les fenêtres de débogénaire, vous pouvez réévaluer la commande **.natvisreload** dans la fenêtre **immédiate.** Ensuite, les modifications prennent effet sans redémarrer la session de débogage.

Utilisez également la commande **.natvisreload** pour mettre à niveau le fichier *.natvis* vers une version plus récente. Par exemple, le fichier *.natvis* peut être vérifié dans le contrôle de source, et vous voulez ramasser les changements récents que quelqu’un d’autre a fait.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Expressions et mise en forme
Les visualisations Natvis utilisent des expressions C++ pour spécifier les éléments de données à afficher. En plus des améliorations et des limites des expressions de C dans le débbugger, qui sont décrites dans [l’opérateur contextuelle (C)](../debugger/context-operator-cpp.md), soyez conscient des éléments suivants :

- Les expressions Natvis sont évaluées dans le contexte de l'objet qui est visualisé, et non dans le frame de pile actuel. Par exemple, `x` dans une expression Natvis se réfère au champ nommé **x** dans l’objet en cours de visualisation, pas à une variable locale nommée **x** dans la fonction actuelle. Vous ne pouvez pas accéder à des variables locales dans les expressions Natvis, bien que vous puissiez accéder à des variables globales.

- Les expressions Natvis n’autorisent pas l’évaluation de la fonction ou les effets secondaires. Les appels de fonction et les opérateurs d’affectation sont ignorés. Comme les [fonctions intrinsèques du débogueur](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) n'ont pas d'effets secondaires, elles peuvent librement être appelées à partir de toute expression Natvis, même si d'autres appels de fonction sont interdits.

- Pour contrôler l’affichage d’une expression, vous pouvez utiliser l’un des spécificateurs de format décrits dans [les spécificateurs format dans C .](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) Les spécitificateurs de format sont ignorés lorsque `Size` l’entrée est utilisée en interne par Natvis, comme l’expression dans une [expansion De ArrayItems.](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion)

## <a name="natvis-views"></a>Vues Natvis

Vous pouvez définir différentes vues Natvis pour afficher des types de différentes manières. Par exemple, voici une `std::vector` visualisation de qui définit `simple`une vue simplifiée nommée . Les `DisplayString` éléments `ArrayItems` et les éléments s’affichent dans la vue par défaut et la `simple` vue, tandis que les `[size]` éléments et `[capacity]` les éléments ne s’affichent pas dans la `simple` vue.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Dans la fenêtre **Watch,** utilisez le spécificateur de **format, vue** pour spécifier une vue alternative. La vue simple apparaît comme **vec,voir(simple)**:

![Fenêtre Espion avec vue simple](../debugger/media/watch-simpleview.png "Fenêtre Espion avec vue simple")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>Erreurs Natvis

Lorsque le débogénaire rencontre des erreurs dans une entrée de visualisation, il les ignore. Il affiche le type sous sa forme brute, soit choisit une autre visualisation appropriée. Vous pouvez utiliser le diagnostic Natvis pour comprendre pourquoi le débbuggeur ignoré une entrée de visualisation, et pour voir les erreurs sous-jacentes de syntaxe et d’analyse.

**Pour activer les diagnostics de Natvis :**

- Sous **outils** > **Options** (ou**Options** **Debug** > ) > **Debugging** > **Output Window**, définir les messages **diagnostiques Natvis (C seulement)** à **l’erreur**, **Avertissement**, ou **Verbose**, puis sélectionnez **OK**.

Les erreurs apparaissent dans la fenêtre **de sortie.**

## <a name="natvis-syntax-reference"></a><a name="BKMK_Syntax_reference"></a> Référence à la syntaxe Natvis

### <a name="autovisualizer-element"></a><a name="BKMK_AutoVisualizer"></a> Élément AutoVisualizer
L’élément `AutoVisualizer` est le nœud racine du fichier *.natvis* et contient l’attribut `xmlns:` de l’espace de noms.

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
.
.
</AutoVisualizer>
```

L’élément `AutoVisualizer` peut avoir [type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer), et [CustomVisualizer](#BKMK_CustomVisualizer) enfants.

### <a name="type-element"></a><a name="BKMK_Type"></a>Élément de type

Une `Type` base ressemble à cet exemple:

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 L’élément `Type` spécifie :

1. À quel type la visualisation doit `Name` être utilisée (l’attribut).

2. la valeur à laquelle doit ressembler un objet de ce type (élément `DisplayString` ) ;

3. À quoi doivent ressembler les membres du type lorsque l’utilisateur `Expand` étend le type dans une fenêtre variable (le nœud).

#### <a name="templated-classes"></a>Classes modélisées
L’attribut `Name` `Type` de l’élément accepte `*` un astérisque comme un personnage wildcard qui peut être utilisé pour les noms de classe modélnés.

Dans l’exemple suivant, la même visualisation est `CAtlArray<int>` utilisée `CAtlArray<float>`si l’objet est a ou a . S’il ya une entrée de `CAtlArray<float>`visualisation spécifique pour un , alors il a préséance sur le générique.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Vous pouvez référencer les paramètres du modèle dans l’entrée de visualisation en utilisant des macros $T1, $T2, et ainsi de suite. Pour trouver des exemples de ces macros, consultez les fichiers *.natvis* fournis avec Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Correspondance des types de visualiseur
Si une entrée de visualisation ne parvient pas à valider, la visualisation disponible suivante est utilisée.

#### <a name="inheritable-attribute"></a>Attribut pouvant être hérité
L’attribut facultatif `Inheritable` précise si une visualisation ne s’applique qu’à un type de base, ou à un type de base et à tous les types dérivés. La valeur par défaut de `Inheritable` est `true`.

Dans l’exemple suivant, la visualisation `BaseClass` ne s’applique qu’au type :

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Attribut de priorité

L’attribut facultatif `Priority` spécifie l’ordre dans lequel utiliser d’autres définitions, si une définition ne parvient pas à analyser. Les valeurs `Priority` possibles `Low`sont:`Medium` `MediumHigh`, `MediumLow` `High`, , et . La valeur par défaut est `Medium`. L’attribut `Priority` ne distingue que parmi les priorités dans le même fichier *.natvis.*

L’exemple suivant analyse d’abord l’entrée qui correspond à la STL 2015. Si cela ne parvient pas à analyser, il utilise l’entrée alternative pour la version 2013 de la STL:

```xml
<!-- VC 2013 -->
<Type Name="std::reference_wrapper&lt;*&gt;" Priority="MediumLow">
     <DisplayString>{_Callee}</DisplayString>
    <Expand>
        <ExpandedItem>_Callee</ExpandedItem>
    </Expand>
</Type>

<!-- VC 2015 -->
<Type Name="std::reference_wrapper&lt;*&gt;">
    <DisplayString>{*_Ptr}</DisplayString>
    <Expand>
        <Item Name="[ptr]">_Ptr</Item>
    </Expand>
</Type>
```

### <a name="optional-attribute"></a>Attribut Optional
Vous pouvez `Optional` mettre un attribut sur n’importe quel nœud. Si une sous-expression à l’intérieur d’un nœud facultatif ne parvient pas à `Type` analyser, le débogénaire ignore ce nœud, mais applique le reste des règles. Dans le type suivant, `[State]` est obligatoire, mais `[Exception]` est facultatif.  Si `MyNamespace::MyClass` un champ`M_exceptionHolder`a nommé `[State]` , le `[Exception]` nœud et le nœud apparaissent, mais s’il n’y a pas `_M_exceptionHolder` de champ, seul le `[State]` nœud apparaît.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Attribut Condition

L’attribut facultatif `Condition` est disponible pour de nombreux éléments de visualisation, et spécifie quand utiliser une règle de visualisation. Si l’expression à l’intérieur de l’attribut de condition se résout à `false`, la règle de visualisation ne s’applique pas. S’il évalue `true`à , `Condition` ou il n’y a pas d’attribut, la visualisation s’applique. Vous pouvez utiliser cet attribut pour la logique si-bien dans les entrées de visualisation.

Par exemple, la visualisation `DisplayString` suivante comporte deux éléments pour un type de pointeur intelligent. Lorsque `_Myptr` le membre est vide, `DisplayString` l’état `true`du premier élément se résout à , de sorte que le formulaire s’affiche. Lorsque `_Myptr` le membre n’est pas `false`vide, la `DisplayString` condition s’évalue à , et le deuxième élément s’affiche.

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

### <a name="includeview-and-excludeview-attributes"></a>Attributs IncludeView et ExcludeView

Les `IncludeView` `ExcludeView` éléments et les attributs spécifient les éléments à afficher ou à ne pas afficher dans des vues spécifiques. Par exemple, dans la spécification `std::vector`Natvis `simple` suivante de , `[size]` `[capacity]` la vue n’affiche pas le et les éléments.

```xml
<Type Name="std::vector&lt;*&gt;">
    <DisplayString>{{ size={_Mylast - _Myfirst} }}</DisplayString>
    <Expand>
        <Item Name="[size]" ExcludeView="simple">_Mylast - _Myfirst</Item>
        <Item Name="[capacity]" ExcludeView="simple">_Myend - _Myfirst</Item>
        <ArrayItems>
            <Size>_Mylast - _Myfirst</Size>
            <ValuePointer>_Myfirst</ValuePointer>
        </ArrayItems>
    </Expand>
</Type>
```

Vous pouvez `IncludeView` utiliser `ExcludeView` les et les attributs sur les types et sur les membres individuels.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>Élément de version
L’élément `Version` est l’accès à une entrée de visualisation à un module et à une version spécifiques. L’élément `Version` permet d’éviter les collisions de nom, réduit les décalages involontaires et permet différentes visualisations pour différentes versions de type.

Si un fichier d’en-tête commun utilisé par différents modules définit un type, la visualisation version n’apparaît que lorsque le type est dans la version du module spécifié.

Dans l’exemple suivant, la visualisation `DirectUI::Border` ne s’applique qu’au type trouvé dans la `Windows.UI.Xaml.dll` version 1.0 à 1.5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Vous n’avez `Min` pas `Max`besoin des deux et . Ce sont des attributs facultatifs. Aucun personnage wildcard n’est pris en charge.

L’attribut `Name` est dans le format *filename.ext*, comme *hello.exe* ou *some.dll*. Aucun nom de chemin n’est autorisé.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>Élément DisplayString
L’élément `DisplayString` spécifie une chaîne à montrer comme la valeur d’une variable. Il accepte les chaînes arbitraires mélangées à des expressions. Tout ce qui figure entre accolades est interprété comme une expression. Par exemple, `DisplayString` l’entrée suivante :

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Signifie que les `CPoint` variables de type d’affichage comme dans cette illustration:

 ![Utilisez un élément DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Utilisez un élément DisplayString")

Dans `DisplayString` `x` l’expression, et `y`, `CPoint`qui sont membres de , sont à l’intérieur des accolades bouclées, de sorte que leurs valeurs sont évaluées. L’exemple montre également comment vous pouvez échapper à une `{{` accolade `}}` bouclée en utilisant des accolades double bouclées ( ou ).

> [!NOTE]
> L'élément `DisplayString` est le seul élément qui accepte des chaînes arbitraires et la syntaxe avec accolades. Tous les autres éléments de visualisation n’acceptent que les expressions que le débbuggeur peut évaluer.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>Élément StringView

L’élément `StringView` définit une valeur que le débbuggeur peut envoyer au visualiseur de texte intégré. Par exemple, compte tenu de `ATL::CStringT` la visualisation suivante pour le type :

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

L’objet `CStringT` s’affiche dans une fenêtre variable comme cet exemple :

![Élément CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "Élément CStringT DisplayString")

L’ajout d’un `StringView` élément indique au débbuggeur qu’il peut afficher la valeur comme une visualisation de texte.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Pendant le débogage, vous pouvez sélectionner l’icône de loupe à côté de la variable, puis sélectionner **Visualizer texte** pour afficher la chaîne qui **m_pszData** points.

 ![Données CStringT avec visualiseur StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Données CStringT avec visualiseur StringView")

L’expression `{m_pszData,su}` comprend un spécificateur de format CMD **su**, pour afficher la valeur comme une chaîne Unicode. Pour plus d’informations, voir [Les spécificateurs format dans C .](../debugger/format-specifiers-in-cpp.md)

### <a name="expand-element"></a><a name="BKMK_Expand"></a>Élargir l’élément

Le `Expand` nœud optionnel personnalise les enfants d’un type visualisé lorsque vous étendez le type dans une fenêtre variable. Le `Expand` nœud accepte une liste de nœuds d’enfants qui définissent les éléments de l’enfant.

- Si `Expand` un nœud n’est pas spécifié dans une entrée de visualisation, les enfants utilisent les règles d’expansion par défaut.

- Si `Expand` un nœud est spécifié sans nœuds d’enfant en dessous, le type n’est pas extensible dans les fenêtres de débogéière.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Expansion d'éléments

 L’élément `Item` est l’élément le `Expand` plus basique et le plus commun dans un nœud. `Item` définit un seul élément enfant. Par exemple, `CRect` une `top`classe `left` `right`avec `bottom` des champs, , , et a l’entrée de visualisation suivante:

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Dans la fenêtre de débogénaire, le `CRect` type ressemble à cet exemple:

![CRect avec expansion d’élément Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect avec expansion d’élément Item")

Le débbuggeur évalue les expressions `Width` `Height` spécifiées dans les éléments et les éléments, et montre les valeurs dans la colonne de **valeur** de la fenêtre variable.

Le débagé crée automatiquement le nœud **[Raw View]** pour chaque extension personnalisée. La capture d’écran précédente affiche le nœud **[Raw View]** élargi, pour montrer comment la vue brute par défaut de l’objet diffère de sa visualisation Natvis. L’expansion par défaut crée un sous-arbre pour la classe de base, et répertorie tous les membres de données de la classe de base comme des enfants.

> [!NOTE]
> Si l’expression de l’élément d’élément indique un type complexe, le nœud **d’élément** lui-même est extensible.

#### <a name="arrayitems-expansion"></a><a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion
Utilisez le nœud `ArrayItems` pour que le débogueur Visual Studio interprète le type comme un tableau et en affiche les éléments individuels. La visualisation pour `std::vector` est un bon exemple :

```xml
<Type Name="std::vector&lt;*&gt;">
  <DisplayString>{{size = {_Mylast - _Myfirst}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mylast - _Myfirst</Item>
    <Item Name="[capacity]">(_Myend - _Myfirst)</Item>
    <ArrayItems>
      <Size>_Mylast - _Myfirst</Size>
      <ValuePointer>_Myfirst</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

Un `std::vector` montre ses éléments individuels quand il est développé dans la fenêtre de variables :

![std::vector utilisant une expansion ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector utilisant une expansion ArrayItems")

Le `ArrayItems` nœud doit avoir :

- une expression `Size` (qui doit prendre la valeur d’un entier) pour que le débogueur comprenne la longueur du tableau.
- Une `ValuePointer` expression qui pointe vers le premier élément (qui doit `void*`être un pointeur d’un type d’élément qui n’est pas ).

La valeur par défaut de la limite inférieure du tableau est 0. Pour remplacer la valeur, `LowerBound` utilisez un élément. Les fichiers *.natvis* expédiés avec Visual Studio ont des exemples.

>[!NOTE]
>Vous pouvez `[]` utiliser l’opérateur, par exemple, `vector[i]`avec n’importe quelle visualisation de tableau unidimensionnelle qui utilise `ArrayItems`, même si le type lui-même (par exemple `CATLArray`) ne permet pas à cet opérateur.

Vous pouvez également spécifier des tableaux multidimensionnels. Dans ce cas, le débbuggeur a besoin d’un peu plus d’informations pour afficher correctement les éléments de l’enfant :

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Direction>Forward</Direction>
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
  </Expand>
</Type>
```

- `Direction`précise si le tableau est en ordre de rame ou de colonne majeure.
- `Rank` spécifie le rang du tableau.
- L’élément `Size` accepte le paramètre `$i` implicite qu’il remplace par l’index de dimension pour déterminer la longueur du tableau dans cette dimension. Dans l’exemple précédent, l’expression `_M_extent.M_base[0]` devrait donner la `_M_extent._M_base[1]` longueur de la 0ème dimension, la 1ère, et ainsi de suite.

Voici comment un objet `Concurrency::array` bidimensionnel ressemble dans la fenêtre de débbuggeur:

![Tableau bidimensionnel avec l’expansion de ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Tableau bidimensionnel avec l’expansion de ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Expansion d'IndexListItems

Vous ne `ArrayItems` pouvez utiliser l’expansion que si les éléments du tableau sont disposés de façon contigu dans la mémoire. Le débbuggeur arrive à l’élément suivant en incrémentant simplement son pointeur. Si vous avez besoin de manipuler l’index au nœud de valeur, utilisez des `IndexListItems` nœuds. Voici une visualisation avec `IndexListItems` un nœud:

```xml
<Type Name="Concurrency::multi_link_registry&lt;*&gt;">
  <DisplayString>{{size = {_M_vector._M_index}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_M_vector._M_index</Item>
    <IndexListItems>
      <Size>_M_vector._M_index</Size>
      <ValueNode>*(_M_vector._M_array[$i])</ValueNode>
    </IndexListItems>
  </Expand>
</Type>
```

La seule `ArrayItems` différence `IndexListItems` entre `ValueNode`et est le , qui attend la `$i` pleine expression à l’élément i<sup>e</sup> avec le paramètre implicite.

>[!NOTE]
>Vous pouvez `[]` utiliser l’opérateur, par exemple, `vector[i]`avec n’importe quelle visualisation de tableau unidimensionnelle qui utilise `IndexListItems`, même si le type lui-même (par exemple `CATLArray`) ne permet pas à cet opérateur.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Expansion de LinkedListItems

Si le type visualisé représente une liste liée, le débogueur peut afficher ses enfants à l'aide d'un nœud `LinkedListItems` . La visualisation suivante `CAtlList` pour `LinkedListItems`le type utilise :

```xml
<Type Name="ATL::CAtlList&lt;*,*&gt;">
  <DisplayString>{{Count = {m_nElements}}}</DisplayString>
  <Expand>
    <Item Name="Count">m_nElements</Item>
    <LinkedListItems>
      <Size>m_nElements</Size>
      <HeadPointer>m_pHead</HeadPointer>
      <NextPointer>m_pNext</NextPointer>
      <ValueNode>m_element</ValueNode>
    </LinkedListItems>
  </Expand>
</Type>
```

L'élément `Size` fait référence à la longueur de la liste. `HeadPointer` pointe vers le premier élément, `NextPointer` fait référence à l'élément suivant et `ValueNode` fait référence à la valeur de l'élément.

Le débagénaire évalue `NextPointer` `ValueNode` les expressions et `LinkedListItems` les expressions dans le contexte de l’élément nœud, et non le type de liste parente. Dans l’exemple `CAtlList` précédent, a `CNode` `atlcoll.h`une classe (trouvée dans ) qui est un nœud de la liste liée. `m_pNext`et `m_element` sont des `CNode` domaines de `CAtlList` cette classe, pas de la classe.

`ValueNode`peut être laissé vide, ou `this` `LinkedListItems` utiliser pour se référer au nœud lui-même.

#### <a name="customlistitems-expansion"></a>Expansion CustomListItems

L'expansion `CustomListItems` vous permet d'écrire une logique personnalisée permettant de parcourir une structure de données telle qu'une table de hachage. Utilisez `CustomListItems` pour visualiser les structures de données qui peuvent utiliser des expressions C pour `ArrayItems`tout `IndexListItems`ce `LinkedListItems`que vous devez évaluer, mais ne correspondent pas tout à fait le moule pour , , ou .

Vous pouvez `Exec` utiliser pour exécuter `CustomListItems` le code à l’intérieur d’une extension, en utilisant les variables et les objets définis dans l’extension. Vous pouvez utiliser des opérateurs logiques, des `Exec`opérateurs arithmétiques et des opérateurs d’affectation avec . Vous ne pouvez `Exec` pas utiliser pour évaluer les fonctions, à l’exception [des fonctions intrinsèques de débbugger](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) supportées par l’évaluateur d’expression C.

Le visualiseur `CAtlMap` suivant est `CustomListItems` un excellent exemple lorsque cela est approprié.

```xml
<Type Name="ATL::CAtlMap&lt;*,*,*,*&gt;">
    <AlternativeType Name="ATL::CMapToInterface&lt;*,*,*&gt;"/>
    <AlternativeType Name="ATL::CMapToAutoPtr&lt;*,*,*&gt;"/>
    <DisplayString>{{Count = {m_nElements}}}</DisplayString>
    <Expand>
      <CustomListItems MaxItemsPerView="5000" ExcludeView="Test">
        <Variable Name="iBucket" InitialValue="-1" />
        <Variable Name="pBucket" InitialValue="m_ppBins == nullptr ? nullptr : *m_ppBins" />
        <Variable Name="iBucketIncrement" InitialValue="-1" />

        <Size>m_nElements</Size>
        <Exec>pBucket = nullptr</Exec>
        <Loop>
          <If Condition="pBucket == nullptr">
            <Exec>iBucket++</Exec>
            <Exec>iBucketIncrement = __findnonnull(m_ppBins + iBucket, m_nBins - iBucket)</Exec>
            <Break Condition="iBucketIncrement == -1" />
            <Exec>iBucket += iBucketIncrement</Exec>
            <Exec>pBucket = m_ppBins[iBucket]</Exec>
          </If>
          <Item>pBucket,na</Item>
          <Exec>pBucket = pBucket->m_pNext</Exec>
        </Loop>
      </CustomListItems>
    </Expand>
</Type>
```

#### <a name="treeitems-expansion"></a><a name="BKMK_TreeItems_expansion"></a> Expansion de TreeItems
 Si le type visualisé représente une arborescence, le débogueur peut la parcourir et afficher ses enfants à l'aide d'un nœud `TreeItems` . Voici la visualisation pour `std::map` le type `TreeItems` à l’aide d’un nœud :

```xml
<Type Name="std::map&lt;*&gt;">
  <DisplayString>{{size = {_Mysize}}}</DisplayString>
  <Expand>
    <Item Name="[size]">_Mysize</Item>
    <Item Name="[comp]">comp</Item>
    <TreeItems>
      <Size>_Mysize</Size>
      <HeadPointer>_Myhead->_Parent</HeadPointer>
      <LeftPointer>_Left</LeftPointer>
      <RightPointer>_Right</RightPointer>
      <ValueNode Condition="!((bool)_Isnil)">_Myval</ValueNode>
    </TreeItems>
  </Expand>
</Type>
```

La syntaxe est `LinkedListItems` similaire au nœud. `LeftPointer`, `RightPointer`et `ValueNode` sont évalués dans le contexte de la classe des nœuds d’arbre. `ValueNode`peut être laissé `this` vide ou `TreeItems` utiliser pour se référer au nœud lui-même.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Expansion d'ExpandedItem
 L’élément `ExpandedItem` génère une vue globale de l’enfant en affichant les propriétés des classes de base ou des membres de données comme s’ils étaient des enfants du type visualisé. Le débbuggeur évalue l’expression spécifiée et appende les nœuds de l’enfant du résultat à la liste enfant du type visualisé.

Par exemple, le `auto_ptr<vector<int>>` type de pointeur intelligent s’affiche généralement comme :

 ![auto&#95;ptr&#60;vecteur&#60;int&#62;&#62; expansion par défaut](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Expansion par défaut")

 Pour voir les valeurs du vecteur, vous devez forer deux niveaux `_Myptr` dans la fenêtre variable, en passant par le membre. En ajoutant un élément `ExpandedItem` , vous pouvez éliminer la variable `_Myptr` de la hiérarchie et afficher directement les éléments du vecteur :

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![auto&#95;ptr&#60;vecteur&#60;int&#62;&#62; expansion ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Expansion d'ExpandedItem")

L’exemple suivant montre comment agréger les propriétés de la classe de base dans une classe dérivée. Supposons que la classe `CPanel` dérive de la classe `CFrameworkElement`. Au lieu de répéter les `CFrameworkElement` propriétés `ExpandedItem` qui proviennent de la classe de base, `CPanel` la visualisation de nœud appende ces propriétés à la liste des enfants de la classe.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Le spécificateur de format **nd** qui désactive l’association de la visualisation de la classe dérivée est ici nécessaire. Dans le `*(CFrameworkElement*)this` cas contraire, l’expression entraînerait l’application de la `CPanel` visualisation à nouveau, parce que les règles de correspondance de type de visualisation par défaut le considèrent comme la plus appropriée. Utilisez le spécificateur de format **nd** pour instruire le débbuggeur d’utiliser la visualisation de la classe de base, ou l’expansion par défaut si la classe de base n’a pas de visualisation.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a>Expansion synthétique de l’article
 Alors que l’élément `ExpandedItem` offre une vue plus plate des données en éliminant les hiérarchies, le nœud `Synthetic` fait exactement le contraire. Il vous permet de créer un élément artificiel de l’enfant qui n’est pas le résultat d’une expression. L’élément artificiel peut avoir ses propres éléments d’enfant. Dans l'exemple suivant, la visualisation du type `Concurrency::array` utilise un nœud `Synthetic` pour présenter un message de diagnostic à l'utilisateur :

```xml
<Type Name="Concurrency::array&lt;*,*&gt;">
  <DisplayString>extent = {_M_extent}</DisplayString>
  <Expand>
    <Item Name="extent" Condition="_M_buffer_descriptor._M_data_ptr == 0">_M_extent</Item>
    <ArrayItems Condition="_M_buffer_descriptor._M_data_ptr != 0">
      <Rank>$T2</Rank>
      <Size>_M_extent._M_base[$i]</Size>
      <ValuePointer>($T1*) _M_buffer_descriptor._M_data_ptr</ValuePointer>
    </ArrayItems>
    <Synthetic Name="Array" Condition="_M_buffer_descriptor._M_data_ptr == 0">
      <DisplayString>Array members can be viewed only under the GPU debugger</DisplayString>
    </Synthetic>
  </Expand>
</Type>
```

 ![Concordance::Array avec l’expansion de l’élément synthétique](../debugger/media/dbg_natvis_expand_synthetic.png "Concordance::Array avec l’expansion de l’élément synthétique")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>Élément HResult
 L’élément `HResult` vous permet de personnaliser les informations affichées pour un **HRESULT** dans les fenêtres de débogénaire. L’élément `HRValue` doit contenir la valeur 32 bits du **HRESULT** à personnaliser. L’élément `HRDescription` contient les informations à afficher dans la fenêtre de débogé.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>Élément UIVisualizer
Un élément `UIVisualizer` permet d'inscrire un plug-in de visualiseur graphique auprès du débogueur. Un visualisateur graphique crée une boîte de dialogue ou une autre interface qui affiche une variable ou un objet d’une manière compatible avec son type de données. Le plug-in de visualisation doit être écrit comme un [VSPackage](../extensibility/internals/vspackages.md), et doit exposer un service que le débbuggeur peut consommer. Le fichier *.natvis* contient des informations d’enregistrement pour le plug-in, tels que son nom, le GUID du service exposé, et les types qu’il peut visualiser.

Voici un exemple d'élément UIVisualizer :

```xml
<?xml version="1.0" encoding="utf-8"?>
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="1" MenuName="Vector Visualizer"/>
    <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}"
        Id="2" MenuName="List Visualizer"/>
.
.
</AutoVisualizer>
```

- `ServiceId`  -  Une `Id` paire d’attributs identifie un `UIVisualizer`. Le `ServiceId` guiD du service que le paquet de visualisation expose. `Id`est un identifiant unique qui différencie les visualisateurs, si un service en fournit plus d’un. Dans l’exemple précédent, le même service de visualisation fournit deux visualisateurs.

- L’attribut `MenuName` définit un nom de visualiseur à afficher dans le drop-down à côté de l’icône de loupe dans le débrilleur. Par exemple :

  ![Menu contextuel du menu UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menu contextuel du menu UIVisualizer")

Chaque type défini dans le fichier *.natvis* doit inscrire explicitement tous les visualisateurs d’interface utilisateur qui peuvent l’afficher. Le débogénaire correspond aux références de visualisateur dans les entrées de type avec les visualisateurs enregistrés. Par exemple, l’entrée `std::vector` de `UIVisualizer` type suivante pour les références dans l’exemple précédent.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Vous pouvez voir un `UIVisualizer` exemple d’une extension de montre [d’image](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) utilisée pour afficher les bitmaps en mémoire.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Élément CustomVisualizer
 `CustomVisualizer`est un point d’extabilité qui spécifie une extension VSIX que vous écrivez pour contrôler les visualisations dans le code Visual Studio. Pour plus d’informations sur l’écriture d’extensions VSIX, voir le [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

C’est beaucoup plus de travail pour écrire un visualiseur personnalisé qu’une définition XML Natvis, mais vous êtes libre de contraintes sur ce que Natvis fait ou ne prend pas en charge. Les visualisateurs personnalisés ont accès à l’ensemble complet des API d’extétabilité de débbugger, qui peuvent interroger et modifier le processus de débbuggee ou communiquer avec d’autres parties de Visual Studio.

 Vous pouvez `Condition`utiliser `IncludeView`le `ExcludeView` , `CustomVisualizer` , et les attributs sur les éléments.

 ## <a name="limitations"></a>Limites

Les personnalisations Natvis fonctionnent avec les classes et les structs, mais pas les types.

Natvis ne prend pas en charge les `int`visualisateurs pour les types primitifs (par exemple, , `bool`) ou pour les pointeurs aux types primitifs. Dans ce scénario, une option consiste à utiliser le [spécificateur](../debugger/format-specifiers-in-cpp.md) de format approprié à votre cas d’utilisation. Par exemple, si `double* mydoublearray` vous utilisez dans votre code, vous pouvez utiliser un spécificateur de format `mydoublearray, [100]`de tableau dans la fenêtre de la **montre** du débagé, comme l’expression , qui affiche les 100 premiers éléments.
