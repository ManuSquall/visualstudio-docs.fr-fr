---
title: Créer des vues personnalisées d’objets C++
description: Utiliser l’infrastructure Natvis pour personnaliser la façon dont Visual Studio affiche les types natifs dans le débogueur
ms.date: 03/02/2020
ms.topic: how-to
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
ms.openlocfilehash: 5720511c15526a54a82018b2079b91aaf5dd6430
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350704"
---
# <a name="create-custom-views-of-c-objects-in-the-debugger-using-the-natvis-framework"></a>Créer des vues personnalisées d’objets C++ dans le débogueur à l’aide de l’infrastructure Natvis

L’infrastructure *Natvis* de Visual Studio personnalise le mode d’affichage des types natifs dans les fenêtres de variables du débogueur, telles que les fenêtres variables **locales** et **espions** , et dans les **DataTips**. Les visualisations Natvis peuvent aider à rendre les types que vous créez plus visibles pendant le débogage.

Natvis remplace le fichier *autoexp. dat* dans les versions antérieures de Visual Studio avec la syntaxe XML, de meilleurs diagnostics, le contrôle de version et la prise en charge de plusieurs fichiers.

> [!NOTE]
> Les personnalisations Natvis fonctionnent avec les classes et les structs, mais pas les typedefs.

## <a name="natvis-visualizations"></a><a name="BKMK_Why_create_visualizations_"></a>Visualisations Natvis

Vous utilisez l’infrastructure Natvis pour créer des règles de visualisation pour les types que vous créez, afin que les développeurs puissent les voir plus facilement pendant le débogage.

Par exemple, l’illustration suivante montre une variable de type [Windows :: UI :: XAML :: Controls :: TextBox](/uwp/api/Windows.UI.Xaml.Controls.TextBox) dans une fenêtre du débogueur sans aucune visualisation personnalisée appliquée.

![Visualisation TextBox par défaut](../debugger/media/dbg_natvis_textbox_default.png "Visualisation TextBox par défaut")

La ligne en surbrillance montre la propriété `Text` de la classe `TextBox` . La hiérarchie de classes complexe rend difficile la recherche de cette propriété. Le débogueur ne sait pas comment interpréter le type de chaîne personnalisé, de sorte que vous ne pouvez pas voir la chaîne contenue dans la zone de texte.

Le même `TextBox` aspect est bien plus simple dans la fenêtre de variables lorsque des règles de visualiseur personnalisé Natvis sont appliquées. Les membres importants de la classe apparaissent ensemble et le débogueur affiche la valeur de chaîne sous-jacente du type de chaîne personnalisé.

![TextBox, données utilisant un visualiseur](../debugger/media/dbg_natvis_textbox_visualizer.png "TextBox, données utilisant un visualiseur")

## <a name="use-natvis-files-in-c-projects"></a><a name="BKMK_Using_Natvis_files"></a>Utiliser des fichiers. natvis dans des projets C++

Natvis utilise des fichiers *. Natvis* pour spécifier des règles de visualisation. Un fichier *. natvis* est un fichier XML avec une extension *. natvis* . Le schéma Natvis est défini dans *%VSInstallDir%\Xml\Schemas\natvis.xsd*.

La structure de base d’un fichier *. natvis* est un ou plusieurs `Type` éléments représentant des entrées de visualisation. Le nom qualifié complet de chaque `Type` élément est spécifié dans son `Name` attribut.

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

Visual Studio fournit certains fichiers *. natvis* dans le dossier *%VSInstallDir%\Common7\Packages\Debugger\Visualizers* . Ces fichiers contiennent des règles de visualisation pour de nombreux types courants et peuvent servir d’exemples pour écrire des visualisations pour de nouveaux types.

### <a name="add-a-natvis-file-to-a-c-project"></a>Ajouter un fichier. natvis à un projet C++

Vous pouvez ajouter un fichier *. natvis* à n’importe quel projet C++.

**Pour ajouter un nouveau fichier *. natvis* :**

1. Sélectionnez le nœud de projet C++ dans **Explorateur de solutions**, puis sélectionnez **projet**  >  **Ajouter un nouvel élément**, ou cliquez avec le bouton droit sur le projet et sélectionnez **Ajouter**  >  **un nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Visual C++**  >  **Utility**  >  **fichier de visualisation du débogueur de l’utilitaire (. natvis)**.

1. Nommez le fichier, puis sélectionnez **Ajouter**.

   Le nouveau fichier est ajouté à **Explorateur de solutions**et s’ouvre dans le volet de document de Visual Studio.

Le débogueur Visual Studio charge automatiquement les fichiers *. natvis* dans les projets C++, et les intègre par défaut également dans le fichier *. pdb* lorsque le projet est généré. Si vous déboguez l’application générée, le débogueur charge le fichier *. natvis* à partir du fichier *. pdb* , même si vous n’avez pas ouvert le projet. Si vous ne voulez pas que le fichier *. natvis* soit inclus dans le fichier. *PDB*, vous pouvez l’exclure du fichier *. pdb* généré.

**Pour exclure un fichier *. natvis* d’un fichier *. pdb*:**

1. Sélectionnez le fichier *. natvis* dans **Explorateur de solutions**, sélectionnez l’icône **Propriétés** , ou cliquez avec le bouton droit sur le fichier et sélectionnez **Propriétés**.

1. Déposez la flèche en regard de **exclu de la génération** , sélectionnez **Oui**, puis sélectionnez **OK**.

>[!NOTE]
>Pour déboguer des projets exécutables, utilisez les éléments de solution pour ajouter tous les fichiers *. natvis* qui ne sont pas dans le fichier *. pdb*, car aucun projet C++ n’est disponible.

>[!NOTE]
>Les règles Natvis chargées à partir d’un fichier *. pdb* s’appliquent uniquement aux types des modules auxquels le fichier *. pdb* fait référence. Par exemple, si *Module1. pdb* a une entrée Natvis pour un type nommé `Test` , il s’applique uniquement à la `Test` classe dans *Module1.dll*. Si un autre module définit également une classe nommée `Test` , l’entrée *Module1. pdb* Natvis ne s’applique pas à celle-ci.

**Pour installer et inscrire un fichier *. natvis* par le biais d’un package VSIX :**

Un package VSIX peut installer et inscrire des fichiers *. natvis* . Quel que soit l’emplacement où elles sont installées, tous les fichiers *. natvis* inscrits sont automatiquement récupérés pendant le débogage.

1. Incluez le fichier *. natvis* dans le package VSIX. Par exemple, pour le fichier projet suivant :
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ToolsVersion="14.0">
     <ItemGroup>
       <VSIXSourceItem Include="Visualizer.natvis" />
     </ItemGroup>
   </Project>
   ```

2. Enregistrez le fichier *. natvis* dans le fichier *source. extension. vsixmanifest* :
   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
     <Assets>
       <Asset Type="NativeVisualizer" Path="Visualizer.natvis"  />
     </Assets>
   </PackageManifest>
   ```

### <a name="natvis-file-locations"></a><a name="BKMK_natvis_location"></a>Emplacements des fichiers Natvis

Vous pouvez ajouter des fichiers *. natvis* dans votre répertoire utilisateur ou dans un répertoire système, si vous souhaitez qu’ils s’appliquent à plusieurs projets.

Les fichiers *. natvis* sont évalués dans l’ordre suivant :

1. Tous les fichiers *. natvis* incorporés dans un fichier *. pdb* que vous déboguez, sauf s’il existe un fichier portant le même nom dans le projet chargé.

2. Tous les fichiers *. natvis* qui se trouvent dans un projet C++ chargé ou une solution de niveau supérieur. Ce groupe inclut tous les projets C++ chargés, y compris les bibliothèques de classes, mais pas les projets dans d’autres langages.

3. Tous les fichiers *. natvis* installés et inscrits par le biais d’un package VSIX.

::: moniker range="vs-2017"

4. Le répertoire Natvis spécifique à l’utilisateur (par exemple, *%USERPROFILE%\Documents\Visual Studio 2017 \ visualiseurs*).

::: moniker-end

::: moniker range=">= vs-2019"

4. Le répertoire Natvis spécifique à l’utilisateur (par exemple, *%USERPROFILE%\Documents\Visual Studio 2019 \ visualiseurs*).

::: moniker-end

5. Le répertoire Natvis à l'échelle du système (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Ce répertoire contient les fichiers *. natvis* installés avec Visual Studio. Si vous disposez d’autorisations d’administrateur, vous pouvez ajouter des fichiers à ce répertoire.

## <a name="modify-natvis-files-while-debugging"></a>Modifier les fichiers. natvis pendant le débogage

Vous pouvez modifier un fichier *. natvis* dans l’IDE lors du débogage de son projet. Ouvrez le fichier dans la même instance de Visual Studio que vous déboguez, modifiez-le et enregistrez-le. Dès que le fichier est enregistré, les fenêtres **Espion** et **variables locales** sont mises à jour pour refléter la modification.

Vous pouvez également ajouter ou supprimer des fichiers *. natvis* dans une solution que vous déboguez, et Visual Studio ajoute ou supprime les visualisations appropriées.

Vous ne pouvez pas mettre à jour les fichiers *. natvis* incorporés dans les fichiers *. pdb* pendant le débogage.

Si vous modifiez le fichier *. natvis* en dehors de Visual Studio, les modifications ne prennent pas effet automatiquement. Pour mettre à jour les fenêtres du débogueur, vous pouvez réévaluer la commande **. natvisreload** dans la fenêtre **exécution** . Les modifications prennent effet sans redémarrer la session de débogage.

Utilisez également la commande **. natvisreload** pour mettre à niveau le fichier *. natvis* vers une version plus récente. Par exemple, le fichier *. natvis* peut être archivé dans le contrôle de code source et vous souhaitez récupérer les modifications récentes apportées par une autre personne.

## <a name="expressions-and-formatting"></a><a name="BKMK_Expressions_and_formatting"></a> Expressions et mise en forme
Les visualisations Natvis utilisent des expressions C++ pour spécifier les éléments de données à afficher. En plus des améliorations et des limitations des expressions C++ dans le débogueur, qui sont décrites dans [opérateur de contexte (c++)](../debugger/context-operator-cpp.md), tenez compte des points suivants :

- Les expressions Natvis sont évaluées dans le contexte de l'objet qui est visualisé, et non dans le frame de pile actuel. Par exemple, `x` dans une expression Natvis fait référence au champ nommé **x** dans l’objet qui est visualisé, et non à une variable locale nommée **x** dans la fonction active. Vous ne pouvez pas accéder aux variables locales dans les expressions Natvis, même si vous pouvez accéder aux variables globales.

- Les expressions Natvis n’autorisent pas l’évaluation de fonction ou les effets secondaires. Les appels de fonction et les opérateurs d’assignation sont ignorés. Comme les [fonctions intrinsèques du débogueur](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) n'ont pas d'effets secondaires, elles peuvent librement être appelées à partir de toute expression Natvis, même si d'autres appels de fonction sont interdits.

- Pour contrôler l’affichage d’une expression, vous pouvez utiliser l’un des spécificateurs de format décrits dans [spécificateurs de format en C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Les spécificateurs de format sont ignorés quand l’entrée est utilisée en interne par Natvis, comme l' `Size` expression dans une [expansion ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).

## <a name="natvis-views"></a>Vues Natvis

Vous pouvez définir différentes vues Natvis pour afficher les types de différentes façons. Par exemple, voici une visualisation de `std::vector` qui définit une vue simplifiée nommée `simple` . Le `DisplayString` et les `ArrayItems` éléments s’affichent dans la vue par défaut et la `simple` vue, tandis que les `[size]` `[capacity]` éléments et ne s’affichent pas dans la `simple` vue.

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

Dans la fenêtre **Espion** , utilisez le spécificateur de format **, View** pour spécifier une autre vue. La vue simple apparaît sous la forme **vec, View (simple)**:

![Fenêtre Espion avec vue simple](../debugger/media/watch-simpleview.png "Fenêtre Espion avec vue simple")

## <a name="natvis-errors"></a><a name="BKMK_Diagnosing_Natvis_errors"></a>Erreurs Natvis

Quand le débogueur rencontre des erreurs dans une entrée de visualisation, il les ignore. Il affiche le type dans sa forme brute ou sélectionne une autre visualisation appropriée. Vous pouvez utiliser les diagnostics Natvis pour comprendre pourquoi le débogueur a ignoré une entrée de visualisation et pour voir les erreurs de syntaxe et d’analyse sous-jacentes.

**Pour activer les diagnostics Natvis :**

- Sous **Tools**  >  **options** des outils (ou options de **débogage**  >  **Options**) > fenêtre sortie de **débogage**  >  **Output Window**, affectez aux **messages de diagnostic Natvis (C++ uniquement)** la valeur **erreur**, **Avertissement**ou **Commentaires**, puis sélectionnez **OK**.

Les erreurs s’affichent dans la fenêtre **sortie** .

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

L' `AutoVisualizer` élément peut avoir des enfants de [type](#BKMK_Type), [HRESULT](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer)et [CustomVisualizer](#BKMK_CustomVisualizer) .

### <a name="type-element"></a><a name="BKMK_Type"></a>Élément type

Un exemple de base `Type` ressemble à ceci :

```xml
<Type Name="[fully qualified type name]">
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>
  <Expand>
    ...
  </Expand>
</Type>
```

 L' `Type` élément spécifie :

1. Le type pour lequel la visualisation doit être utilisée ( `Name` attribut).

2. la valeur à laquelle doit ressembler un objet de ce type (élément `DisplayString` ) ;

3. Ce à quoi les membres du type doivent ressembler quand l’utilisateur développe le type dans une fenêtre de variables ( `Expand` nœud).

#### <a name="templated-classes"></a>Classes basées sur un modèle
L' `Name` attribut de l' `Type` élément accepte un astérisque `*` comme caractère générique qui peut être utilisé pour les noms de classe basés sur un modèle.

Dans l’exemple suivant, la même visualisation est utilisée que l’objet soit un `CAtlArray<int>` ou un `CAtlArray<float>` . S’il existe une entrée de visualisation spécifique pour un `CAtlArray<float>` , il est prioritaire sur le modèle générique.

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

Vous pouvez faire référence à des paramètres de modèle dans l’entrée de visualisation à l’aide de macros $T 1, $T 2, et ainsi de suite. Pour trouver des exemples de ces macros, consultez les fichiers *.natvis* fournis avec Visual Studio.

#### <a name="visualizer-type-matching"></a><a name="BKMK_Visualizer_type_matching"></a> Correspondance des types de visualiseur
Si une entrée de visualisation ne parvient pas à être validée, la visualisation disponible suivante est utilisée.

#### <a name="inheritable-attribute"></a>Attribut pouvant être hérité
L' `Inheritable` attribut facultatif spécifie si une visualisation s’applique uniquement à un type de base, ou à un type de base et à tous les types dérivés. La valeur par défaut de `Inheritable` est `true`.

Dans l’exemple suivant, la visualisation s’applique uniquement au `BaseClass` type :

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>
</Type>
```

#### <a name="priority-attribute"></a>Attribut de priorité

L' `Priority` attribut facultatif spécifie l’ordre dans lequel utiliser les autres définitions, si une définition ne parvient pas à être analysée. Les valeurs possibles `Priority` sont les suivantes : `Low` ,,, `MediumLow` `Medium` `MediumHigh` et `High` . La valeur par défaut est `Medium`. L' `Priority` attribut distingue uniquement les priorités au sein du même fichier *. natvis* .

L’exemple suivant analyse d’abord l’entrée qui correspond à la bibliothèque STL 2015. Si l’analyse échoue, elle utilise l’autre entrée pour la version 2013 de la bibliothèque STL :

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
Vous pouvez placer un `Optional` attribut sur n’importe quel nœud. Si une sous-expression à l’intérieur d’un nœud facultatif ne parvient pas à être analysée, le débogueur ignore ce nœud, mais applique le reste des `Type` règles. Dans le type suivant, `[State]` est obligatoire, mais `[Exception]` est facultatif.  Si `MyNamespace::MyClass` contient un champ nommé _ `M_exceptionHolder` , le `[State]` nœud et le `[Exception]` nœud apparaissent, mais s’il n’y a aucun `_M_exceptionHolder` champ, seul le `[State]` nœud apparaît.

```xml
<Type Name="MyNamespace::MyClass">
    <Expand>
      <Item Name="[State]">_M_State</Item>
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>
    </Expand>
</Type>
```

### <a name="condition-attribute"></a><a name="BKMK_Condition_attribute"></a> Attribut Condition

L' `Condition` attribut facultatif est disponible pour de nombreux éléments de visualisation et spécifie quand utiliser une règle de visualisation. Si l’expression à l’intérieur de l’attribut condition correspond à `false` , la règle de visualisation ne s’applique pas. Si elle prend la valeur `true` ou s’il n’existe aucun `Condition` attribut, la visualisation s’applique. Vous pouvez utiliser cet attribut pour la logique if-else dans les entrées de visualisation.

Par exemple, la visualisation suivante comporte deux `DisplayString` éléments pour un type de pointeur intelligent. Lorsque le `_Myptr` membre est vide, la condition du premier `DisplayString` élément est résolue en `true` , afin que le formulaire s’affiche. Lorsque le `_Myptr` membre n’est pas vide, la condition prend la valeur `false` , et le deuxième `DisplayString` élément affiche.

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

Les `IncludeView` `ExcludeView` attributs et spécifient des éléments à afficher ou à ne pas afficher dans des vues spécifiques. Par exemple, dans la spécification Natvis suivante de `std::vector` , la `simple` vue n’affiche pas `[size]` les `[capacity]` éléments et.

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

Vous pouvez utiliser les `IncludeView` `ExcludeView` attributs et sur les types et sur des membres individuels.

### <a name="version-element"></a><a name="BKMK_Versioning"></a>Élément version
L' `Version` élément étend une entrée de visualisation à un module et une version spécifiques. L' `Version` élément permet d’éviter les conflits de noms, réduit les incompatibilités par inadvertance et autorise différentes visualisations pour différentes versions de type.

Si un fichier d’en-tête commun utilisé par différents modules définit un type, la visualisation avec version s’affiche uniquement lorsque le type est dans la version de module spécifiée.

Dans l’exemple suivant, la visualisation est applicable uniquement pour le `DirectUI::Border` type trouvé dans le `Windows.UI.Xaml.dll` de la version 1,0 à 1,5.

```xml
<Type Name="DirectUI::Border">
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>
  <Expand>
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>
  </Expand>
</Type>
```

Vous n’avez pas besoin `Min` de et de `Max` . Il s’agit d’attributs facultatifs. Aucun caractère générique n’est pris en charge.

L' `Name` attribut est au format *nom_fichier. ext*, par exemple *hello.exe* ou *some.dll*. Aucun nom de chemin d’accès n’est autorisé.

### <a name="displaystring-element"></a><a name="BKMK_DisplayString"></a>Élément DisplayString
L' `DisplayString` élément spécifie une chaîne à afficher en tant que valeur d’une variable. Il accepte les chaînes arbitraires mélangées à des expressions. Tout ce qui figure entre accolades est interprété comme une expression. Par exemple, l' `DisplayString` entrée suivante :

```xml
<Type Name="CPoint">
  <DisplayString>{{x={x} y={y}}}</DisplayString>
</Type>
```

Signifie que les variables de type s' `CPoint` affichent comme dans cette illustration :

 ![Utiliser un élément DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "Utiliser un élément DisplayString")

Dans l' `DisplayString` expression, `x` et `y` , qui sont membres de `CPoint` , sont placés entre accolades, donc leurs valeurs sont évaluées. L’exemple montre également comment vous pouvez échapper une accolade en utilisant des accolades doubles ( `{{` ou `}}` ).

> [!NOTE]
> L'élément `DisplayString` est le seul élément qui accepte des chaînes arbitraires et la syntaxe avec accolades. Tous les autres éléments de visualisation acceptent uniquement les expressions que le débogueur peut évaluer.

### <a name="stringview-element"></a><a name="BKMK_StringView"></a>Élément StringView

L' `StringView` élément définit une valeur que le débogueur peut envoyer au visualiseur de texte intégré. Par exemple, à partir de la visualisation suivante pour le `ATL::CStringT` type :

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
</Type>
```

L' `CStringT` objet s’affiche dans une fenêtre de variables comme dans l’exemple suivant :

![Élément CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "Élément CStringT DisplayString")

L’ajout d’un `StringView` élément indique au débogueur qu’il peut afficher la valeur sous la forme d’une visualisation de texte.

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>
  <StringView>m_pszData,su</StringView>
</Type>
```

Pendant le débogage, vous pouvez sélectionner l’icône de loupe en regard de la variable, puis sélectionner **visualiseur de texte** pour afficher la chaîne vers laquelle **m_pszData** pointe.

 ![Données CStringT avec visualiseur StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "Données CStringT avec visualiseur StringView")

L’expression `{m_pszData,su}` comprend un spécificateur de format C++ **su**pour afficher la valeur sous la forme d’une chaîne Unicode. Pour plus d’informations, consultez [spécificateurs de format en C++](../debugger/format-specifiers-in-cpp.md).

### <a name="expand-element"></a><a name="BKMK_Expand"></a>Développer l’élément

Le `Expand` nœud facultatif personnalise les enfants d’un type visualisé quand vous développez le type dans une fenêtre de variables. Le `Expand` nœud accepte une liste de nœuds enfants qui définissent les éléments enfants.

- Si un `Expand` nœud n’est pas spécifié dans une entrée de visualisation, les enfants utilisent les règles d’expansion par défaut.

- Si un `Expand` nœud est spécifié sans aucun nœud enfant, le type ne peut pas être développé dans les fenêtres du débogueur.

#### <a name="item-expansion"></a><a name="BKMK_Item_expansion"></a> Expansion d'éléments

 L' `Item` élément est l’élément le plus basique et le plus courant dans un `Expand` nœud. `Item` définit un seul élément enfant. Par exemple, une `CRect` classe avec des champs `top` ,, `left` `right` et `bottom` a l’entrée de visualisation suivante :

```xml
<Type Name="CRect">
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>
  <Expand>
    <Item Name="Width">right - left</Item>
    <Item Name="Height">bottom - top</Item>
  </Expand>
</Type>
```

Dans la fenêtre du débogueur, le `CRect` type ressemble à l’exemple suivant :

![CRect avec expansion d’élément Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect avec expansion d’élément Item")

Le débogueur évalue les expressions spécifiées dans `Width` les `Height` éléments et, et affiche les valeurs dans la colonne **valeur** de la fenêtre de variables.

Le débogueur crée automatiquement le nœud **[vue brute]** pour chaque expansion personnalisée. La capture d’écran ci-dessus affiche le nœud **[RAW View]** développé pour montrer comment la vue brute par défaut de l’objet diffère de sa visualisation Natvis. L’expansion par défaut crée une sous-arborescence pour la classe de base et répertorie tous les membres de données de la classe de base en tant qu’enfants.

> [!NOTE]
> Si l’expression de l’élément item pointe vers un type complexe, le nœud **Item** lui-même peut être développé.

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

Le `ArrayItems` nœud doit avoir :

- une expression `Size` (qui doit prendre la valeur d’un entier) pour que le débogueur comprenne la longueur du tableau.
- `ValuePointer`Expression qui pointe vers le premier élément (qui doit être un pointeur d’un type d’élément qui n’est pas `void*` ).

La valeur par défaut de la limite inférieure du tableau est 0. Pour remplacer la valeur, utilisez un `LowerBound` élément. Les fichiers *. natvis* fournis avec Visual Studio contiennent des exemples.

>[!NOTE]
>Vous pouvez utiliser l' `[]` opérateur, par exemple `vector[i]` , avec n’importe quelle visualisation de tableau unidimensionnel qui utilise `ArrayItems` , même si le type lui-même (par exemple `CATLArray` ) n’autorise pas cet opérateur.

Vous pouvez également spécifier des tableaux multidimensionnels. Dans ce cas, le débogueur a besoin d’un peu plus d’informations pour afficher correctement les éléments enfants :

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

- `Direction`Spécifie si le tableau est dans l’ordre ligne-principal ou colonne-principal.
- `Rank` spécifie le rang du tableau.
- L’élément `Size` accepte le paramètre `$i` implicite qu’il remplace par l’index de dimension pour déterminer la longueur du tableau dans cette dimension. Dans l’exemple précédent, l’expression `_M_extent.M_base[0]` doit indiquer la longueur de la dimension 0, `_M_extent._M_base[1]` la première, et ainsi de suite.

Voici à quoi ressemble un objet à deux dimensions `Concurrency::array` dans la fenêtre du débogueur :

![Tableau à deux dimensions avec expansion ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "Tableau à deux dimensions avec expansion ArrayItems")

#### <a name="indexlistitems-expansion"></a><a name="BKMK_IndexListItems_expansion"></a> Expansion d'IndexListItems

Vous pouvez utiliser `ArrayItems` l’expansion uniquement si les éléments du tableau sont disposés de façon contiguë en mémoire. Le débogueur passe à l’élément suivant en incrémentant simplement son pointeur. Si vous devez manipuler l’index sur le nœud de valeur, utilisez des `IndexListItems` nœuds. Voici une visualisation avec un `IndexListItems` nœud :

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

La seule différence entre `ArrayItems` et `IndexListItems` est `ValueNode` , qui attend l’expression complète de l’élément i<sup>ème</sup> avec le paramètre implicite `$i` .

>[!NOTE]
>Vous pouvez utiliser l' `[]` opérateur, par exemple `vector[i]` , avec n’importe quelle visualisation de tableau unidimensionnel qui utilise `IndexListItems` , même si le type lui-même (par exemple `CATLArray` ) n’autorise pas cet opérateur.

#### <a name="linkedlistitems-expansion"></a><a name="BKMK_LinkedListItems_expansion"></a> Expansion de LinkedListItems

Si le type visualisé représente une liste liée, le débogueur peut afficher ses enfants à l'aide d'un nœud `LinkedListItems` . La visualisation suivante pour le `CAtlList` type utilise `LinkedListItems` :

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

Le débogueur évalue les `NextPointer` `ValueNode` expressions et dans le contexte de l' `LinkedListItems` élément de nœud, et non le type de la liste parente. Dans l’exemple précédent, `CAtlList` a une `CNode` classe (trouvée dans `atlcoll.h` ) qui est un nœud de la liste liée. `m_pNext`et `m_element` sont des champs de cette `CNode` classe, et non de la `CAtlList` classe.

`ValueNode`peut être laissé vide ou utiliser `this` pour faire référence au `LinkedListItems` nœud lui-même.

#### <a name="customlistitems-expansion"></a>Expansion CustomListItems

L'expansion `CustomListItems` vous permet d'écrire une logique personnalisée permettant de parcourir une structure de données telle qu'une table de hachage. Utilisez `CustomListItems` pour visualiser des structures de données qui peuvent utiliser des expressions C++ pour tout ce dont vous avez besoin, mais qui ne correspondent pas tout à fait au moule pour `ArrayItems` , `IndexListItems` ou `LinkedListItems` .

Vous pouvez utiliser `Exec` pour exécuter du code à l’intérieur d’une `CustomListItems` expansion, à l’aide des variables et des objets définis dans le développement. Vous pouvez utiliser des opérateurs logiques, des opérateurs arithmétiques et des opérateurs d’assignation avec `Exec` . Vous ne pouvez pas utiliser `Exec` pour évaluer des fonctions, à l’exception des [fonctions intrinsèques du débogueur](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) prises en charge par l’évaluateur d’expression C++.

Le visualiseur suivant pour `CAtlMap` est un excellent exemple où `CustomListItems` est approprié.

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
 Si le type visualisé représente une arborescence, le débogueur peut la parcourir et afficher ses enfants à l'aide d'un nœud `TreeItems` . Voici la visualisation pour le `std::map` type à l’aide d’un `TreeItems` nœud :

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

La syntaxe est similaire au `LinkedListItems` nœud. `LeftPointer`, `RightPointer` et `ValueNode` sont évalués dans le contexte de la classe de nœud d’arbre. `ValueNode`peut être laissé vide ou utiliser `this` pour faire référence au `TreeItems` nœud lui-même.

#### <a name="expandeditem-expansion"></a><a name="BKMK_ExpandedItem_expansion"></a> Expansion d'ExpandedItem
 L' `ExpandedItem` élément génère une vue enfant agrégée en affichant les propriétés des classes de base ou des membres de données comme s’ils étaient des enfants du type visualisé. Le débogueur évalue l’expression spécifiée et ajoute les nœuds enfants du résultat à la liste enfant du type visualisé.

Par exemple, le type de pointeur intelligent `auto_ptr<vector<int>>` s’affiche généralement sous la forme :

 ![&#95;PTR&#60;Vector&#60;int&#62;&#62; l’expansion par défaut](../debugger/media/dbg_natvis_expand_expandeditem_default.png "Expansion par défaut")

 Pour voir les valeurs du vecteur, vous devez descendre dans la fenêtre de la variable deux niveaux, en passant par le `_Myptr` membre. En ajoutant un élément `ExpandedItem` , vous pouvez éliminer la variable `_Myptr` de la hiérarchie et afficher directement les éléments du vecteur :

```xml
<Type Name="std::auto_ptr&lt;*&gt;">
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>
  <Expand>
    <ExpandedItem>_Myptr</ExpandedItem>
  </Expand>
</Type>
```

 ![&#95;PTR&#60;Vector&#60;int&#62;&#62; expansion ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "Expansion d'ExpandedItem")

L’exemple suivant montre comment agréger des propriétés à partir de la classe de base dans une classe dérivée. Supposons que la classe `CPanel` dérive de la classe `CFrameworkElement`. Au lieu de répéter les propriétés provenant de la classe de base `CFrameworkElement` , la `ExpandedItem` visualisation de nœud ajoute ces propriétés à la liste enfant de la `CPanel` classe.

```xml
<Type Name="CPanel">
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>
  <Expand>
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>
  </Expand>
</Type>
```

Le spécificateur de format **nd** qui désactive l’association de la visualisation de la classe dérivée est ici nécessaire. Dans le cas contraire, l’expression `*(CFrameworkElement*)this` entraînerait `CPanel` une nouvelle application de la visualisation, car les règles de correspondance de type de visualisation par défaut la considèrent comme la plus appropriée. Utilisez le spécificateur de format **ND** pour indiquer au débogueur d’utiliser la visualisation de la classe de base, ou l’expansion par défaut si la classe de base n’a pas de visualisation.

#### <a name="synthetic-item-expansion"></a><a name="BKMK_Synthetic_Item_expansion"></a>Développement d’éléments synthétiques
 Alors que l’élément `ExpandedItem` offre une vue plus plate des données en éliminant les hiérarchies, le nœud `Synthetic` fait exactement le contraire. Elle vous permet de créer un élément enfant artificiel qui n’est pas le résultat d’une expression. L’élément artificiel peut avoir ses propres éléments enfants. Dans l'exemple suivant, la visualisation du type `Concurrency::array` utilise un nœud `Synthetic` pour présenter un message de diagnostic à l'utilisateur :

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

 ![Concurrence :: Array avec expansion d’élément synthétique](../debugger/media/dbg_natvis_expand_synthetic.png "Concurrence :: Array avec expansion d’élément synthétique")

### <a name="hresult-element"></a><a name="BKMK_HResult"></a>HResult, élément
 L' `HResult` élément vous permet de personnaliser les informations affichées pour un **HRESULT** dans les fenêtres du débogueur. L’élément `HRValue` doit contenir la valeur 32 bits du **HRESULT** à personnaliser. L' `HRDescription` élément contient les informations à afficher dans la fenêtre du débogueur.

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">
  <HRValue>0xABC0123</HRValue>
  <HRDescription>No elements in the collection.</HRDescription>
</HResult>
```

### <a name="uivisualizer-element"></a><a name="BKMK_UIVisualizer"></a>Élément UIVisualizer
Un élément `UIVisualizer` permet d'inscrire un plug-in de visualiseur graphique auprès du débogueur. Un visualiseur graphique crée une boîte de dialogue ou une autre interface qui affiche une variable ou un objet d’une manière cohérente avec son type de données. Le plug-in du visualiseur doit être créé en tant que [VSPackage](../extensibility/internals/vspackages.md)et doit exposer un service que le débogueur peut consommer. Le fichier *. natvis* contient les informations d’inscription du plug-in, telles que son nom, le GUID du service exposé et les types qu’il peut visualiser.

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

- Une `ServiceId`  -  `Id` paire d’attributs identifie un `UIVisualizer` . `ServiceId`Est le GUID du service exposé par le package du visualiseur. `Id`identificateur unique qui différencie les visualiseurs, si un service en fournit plusieurs. Dans l’exemple précédent, le même service de visualiseur fournit deux visualiseurs.

- L' `MenuName` attribut définit un nom de visualiseur à afficher dans la liste déroulante en regard de l’icône de loupe dans le débogueur. Par exemple :

  ![Menu contextuel du menu UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "Menu contextuel du menu UIVisualizer")

Chaque type défini dans le fichier *. natvis* doit répertorier explicitement les visualiseurs d’interface utilisateur qui peuvent l’afficher. Le débogueur met en correspondance les références de visualiseur dans les entrées de type avec les visualiseurs inscrits. Par exemple, l’entrée de type suivante pour `std::vector` fait référence à `UIVisualizer` dans l’exemple précédent.

```xml
<Type Name="std::vector&lt;int,*&gt;">
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />
</Type>
```

 Vous pouvez voir un exemple de `UIVisualizer` dans l’extension [image Watch](https://marketplace.visualstudio.com/search?term=%22Image%20Watch%22&target=VS&category=All%20categories&vsVersion=&sortBy=Relevance) utilisée pour afficher les bitmaps en mémoire.

### <a name="customvisualizer-element"></a><a name="BKMK_CustomVisualizer"></a>Élément CustomVisualizer
 `CustomVisualizer`est un point d’extensibilité qui spécifie une extension VSIX que vous écrivez pour contrôler les visualisations dans Visual Studio code. Pour plus d’informations sur l’écriture d’extensions VSIX, consultez le [Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk.md).

Il y a beaucoup plus de travail pour écrire un visualiseur personnalisé qu’une définition de Natvis XML, mais vous êtes libre des contraintes concernant ce que Natvis ne prend pas en charge. Les visualiseurs personnalisés ont accès à l’ensemble complet des API d’extensibilité du débogueur, qui peuvent interroger et modifier le processus du programme débogué ou communiquer avec d’autres parties de Visual Studio.

 Vous pouvez utiliser les `Condition` `IncludeView` attributs, et `ExcludeView` sur les `CustomVisualizer` éléments.

 ## <a name="limitations"></a>Limites

Les personnalisations Natvis fonctionnent avec les classes et les structs, mais pas les typedefs.

Natvis ne prend pas en charge les visualiseurs pour les types primitifs (par exemple, `int` , `bool` ) ou pour les pointeurs vers des types primitifs. Dans ce scénario, une option consiste à utiliser le [spécificateur de format](../debugger/format-specifiers-in-cpp.md) approprié à votre cas d’usage. Par exemple, si vous utilisez `double* mydoublearray` dans votre code, vous pouvez utiliser un spécificateur de format de tableau dans la fenêtre **Espion** du débogueur, telle que l’expression `mydoublearray, [100]` , qui affiche les 100 premiers éléments.
