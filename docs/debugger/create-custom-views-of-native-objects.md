---
title: Créer des vues personnalisées d'objets natifs
description: Utiliser l’infrastructure Natvis pour personnaliser la façon dont Visual Studio affiche les types natifs dans le débogueur
ms.date: 10/31/2018
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
ms.openlocfilehash: ca1cf68af84556a76c29417c9bd56894a70f12ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997323"
---
# <a name="create-custom-views-of-native-objects-in-the-debugger"></a>Créer des vues personnalisées d’objets natifs dans le débogueur

Visual Studio *Natvis* framework personnalise l’apparence des types natifs dans les fenêtres de variables du débogueur, telles que la **variables locales** et **espion** windows et dans **DataTips**. Les visualisations Natvis peuvent aider à rendre les types que vous créez plus visible pendant le débogage. 

Natvis remplace le *autoexp.dat* fichier dans les versions antérieures de Visual Studio avec la syntaxe XML, de meilleurs diagnostics, le contrôle de version et prend en charge de plusieurs fichiers.  


## <a name="BKMK_Why_create_visualizations_"></a>Visualisations Natvis

L’infrastructure Natvis vous permet de créer des règles de visualisation pour les types que vous créez, afin que les développeurs peuvent les voir plus facilement pendant le débogage.  

Par exemple, l’illustration suivante montre une variable de type [Windows::UI::Xaml::Controls::TextBox](http://go.microsoft.com/fwlink/?LinkId=258422) dans une fenêtre du débogueur sans aucune visualisation personnalisée appliquée.  

![Visualisation TextBox par défaut](../debugger/media/dbg_natvis_textbox_default.png "visualisation TextBox par défaut")  

La ligne en surbrillance montre la propriété `Text` de la classe `TextBox` . La hiérarchie de classes complexe rend difficile de trouver cette propriété. Le débogueur ne sait pas comment interpréter le type de chaîne personnalisé, vous ne voyez pas la chaîne figurant dans la zone de texte.  

Le même `TextBox` ressemble beaucoup plus simple dans la fenêtre de variables lorsque les règles de visualiseur personnalisé Natvis sont appliquées. Les membres importants de la classe apparaissent ensemble, et le débogueur affiche la valeur de chaîne sous-jacente du type de chaîne personnalisée.  

![Les données de zone de texte à l’aide de visualiseur](../debugger/media/dbg_natvis_textbox_visualizer.png "les données de zone de texte à l’aide de visualiseur")  

##  <a name="BKMK_Using_Natvis_files"></a>Utilisation de fichiers .natvis dans les projets C++  

Natvis utilise *.natvis* fichiers pour spécifier les règles de visualisation. Un *.natvis* fichier est un fichier XML avec un *.natvis* extension. Le schéma Natvis est défini dans *%VSINSTALLDIR%\Xml\Schemas\natvis.xsd*.  

La structure de base d’un *.natvis* fichier comporte un ou plusieurs `Type` éléments représentant des entrées de visualisation. Le nom qualifié complet de chaque `Type` élément est spécifié dans son `Name` attribut.  

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

Visual Studio propose certains *.natvis* des fichiers dans le *%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers* dossier. Ces fichiers ont des règles de visualisation pour de nombreux types courants et peuvent servir d’exemples pour écrire des visualisations pour nouveaux types.  

### <a name="add-a-natvis-file-to-a-c-project"></a>Ajouter un fichier .natvis à un projet C++  

Vous pouvez ajouter un *.natvis* fichier à tout projet C++.  

**Pour ajouter un nouveau *.natvis* fichier :**

1. Sélectionnez le nœud de projet C++ dans **l’Explorateur de solutions**, puis sélectionnez **projet** > **ajouter un nouvel élément**, ou cliquez sur le projet et sélectionnez **ajouter**   >  **Un nouvel élément**.
   
1. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **Visual C++** > **utilitaire** > **fichier de visualisation du débogueur (.natvis)**. 
   
1. Nommez le fichier, puis sélectionnez **ajouter**.
   
   Le nouveau fichier est ajouté à **l’Explorateur de solutions**et s’ouvre dans le volet de document de Visual Studio. 

Le débogueur Visual Studio charge *.natvis* fichiers dans les projets C++ et automatiquement par défaut, également les inclut dans le *.pdb* fichier lorsque le projet est généré. Si vous déboguez l’application générée, le débogueur charge les *.natvis* de fichiers à partir de la *.pdb* fichier, même si vous n’avez pas le projet ouvert. Si vous ne souhaitez pas la *.natvis* fichier inclus dans le *.pdb*, vous pouvez l’exclure de la génération *.pdb* fichier.

**Pour exclure un *.natvis* de fichiers à partir d’un *.pdb*:**

1. Sélectionnez le *.natvis* de fichiers dans **l’Explorateur de solutions**, puis sélectionnez le **propriétés** icône, ou cliquez sur le fichier et sélectionnez **propriétés**.
   
1. Faites glisser la flèche à côté **exclu de la génération** et sélectionnez **Oui**, puis sélectionnez **OK**.  

>[!NOTE]
>Pour le débogage des projets exécutables, utilisez les éléments de solution pour ajouter les *.natvis* les fichiers qui ne figurent pas dans le *.pdb*, car aucun projet C++ est disponible.  

>[!NOTE]
>Natvis règles chargement à partir d’un *.pdb* s’appliquent uniquement aux types dans les modules qui les *.pdb* fait référence à. Par exemple, si *Module1.pdb* comporte une entrée Natvis pour un type nommé `Test`, elle s’applique uniquement à la `Test` classe *Module1.dll*. Si un autre module définit également une classe nommée `Test`, le *Module1.pdb* entrée Natvis ne s’y applique pas.  

### <a name="BKMK_natvis_location"></a> Emplacements des fichiers Natvis  

Vous pouvez ajouter *.natvis* des fichiers dans votre répertoire utilisateur ou dans un répertoire système, si vous souhaitez qu’ils s’appliquent à plusieurs projets.  

Le *.natvis* fichiers sont évalués dans l’ordre suivant :  

1. N’importe quel *.natvis* fichiers incorporés dans un *.pdb* vous déboguez, sauf si un fichier du même nom existe dans le projet chargé.  

1. N’importe quel *.natvis* les fichiers qui se trouvent dans un projet C++ chargé ou d’une solution de niveau supérieur. Ce groupe inclut des projets C++ tous chargés, y compris les bibliothèques de classes, mais pas les projets dans d’autres langages. 

1.  Le répertoire Natvis spécifique à l’utilisateur (par exemple, *%USERPROFILE%\Documents\Visual Studio 2017\Visualizers*).  

1.  Le répertoire Natvis à l'échelle du système (*%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers*). Ce répertoire a la *.natvis* fichiers qui sont installés avec Visual Studio. Si vous disposez des autorisations d’administrateur, vous pouvez ajouter des fichiers dans ce répertoire.  

## <a name="modify-natvis-files-while-debugging"></a>Modifier des fichiers .natvis pendant le débogage  

Vous pouvez modifier un *.natvis* fichier dans l’IDE pendant le débogage de son projet. Ouvrez le fichier dans la même instance de Visual Studio que vous déboguez avec, modifiez-le et enregistrez-le. Dès que le fichier est enregistré, le **espion** et **variables locales** windows mise à jour pour refléter la modification. 

Vous pouvez également ajouter ou supprimer *.natvis* fichiers dans une solution que vous déboguez, Visual Studio ajoute ou supprime les visualisations correspondantes.  

Vous ne pouvez pas mettre à jour *.natvis* fichiers incorporés dans *.pdb* fichiers pendant que vous déboguez.  

Si vous modifiez le *.natvis* fichier en dehors de Visual Studio, les modifications ne prennent effet automatiquement. Pour mettre à jour les fenêtres du débogueur, vous pouvez réévaluer le **.natvisreload** commande dans le **espion** fenêtre. Ensuite, les modifications prennent effet sans avoir à redémarrer la session de débogage.  

Utilisez également le **.natvisreload** commande pour mettre à niveau le *.natvis* fichier vers une version plus récente. Par exemple, le *.natvis* fichier peut être archivé dans le contrôle de code source, et que vous souhaitez reprendre les modifications récentes qu’une personne créée. 

##  <a name="BKMK_Expressions_and_formatting"></a> Expressions et mise en forme  
Les visualisations Natvis utilisent des expressions C++ pour spécifier les éléments de données à afficher. Outre les améliorations et les limitations des expressions C++ dans le débogueur, qui sont décrites dans [opérateur de contexte (C++)](../debugger/context-operator-cpp.md), tenez compte des éléments suivants :  

- Les expressions Natvis sont évaluées dans le contexte de l'objet qui est visualisé, et non dans le frame de pile actuel. Par exemple, `x` dans un Natvis expression fait référence au champ nommé **x** dans l’objet qui est visualisé, pas à une variable locale nommée **x** dans la fonction active. Impossible d’accéder à des variables locales dans des expressions Natvis, même si vous pouvez accéder aux variables globales.  

- Expressions de Natvis n’autorisent pas l’évaluation de fonction ou des effets secondaires. Appels de fonction et les opérateurs d’assignation sont ignorés. Comme les [fonctions intrinsèques du débogueur](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) n'ont pas d'effets secondaires, elles peuvent librement être appelées à partir de toute expression Natvis, même si d'autres appels de fonction sont interdits.  

- Pour contrôler l’affichage d’une expression, vous pouvez utiliser un des spécificateurs de format décrits dans [Format specifiers dans C++](format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers). Spécificateurs de format sont ignorés lors de l’entrée est utilisée en interne par Natvis, notamment le `Size` expression dans une [expansion d’ArrayItems](../debugger/create-custom-views-of-native-objects.md#BKMK_ArrayItems_expansion).  

## <a name="natvis-views"></a>Vues Natvis  

Vous pouvez définir différentes vues Natvis pour afficher les types de différentes façons. Par exemple, voici une visualisation de `std::vector` qui définit une vue simplifiée nommée `simple`. Le `DisplayString` et le `ArrayItems` affichent les éléments dans la vue par défaut et le `simple` vue, tandis que le `[size]` et `[capacity]` éléments ne s’affichent dans le `simple` vue. 

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


Dans le **espion** fenêtre, utilisez le **, vue** spécificateur pour spécifier un autre affichage de format. La vue simple s’affiche en tant que **vec,view(simple)**:  

![Fenêtre Espion avec vue simple](../debugger/media/watch-simpleview.png "fenêtre Espion avec vue simple")  

##  <a name="BKMK_Diagnosing_Natvis_errors"></a> Erreurs Natvis  

Lorsque le débogueur rencontre des erreurs dans une entrée de visualisation, il les ignore. Il affiche le type dans sa forme brute, ou récupère une autre visualisation appropriée. Vous pouvez utiliser le diagnostic Natvis pour comprendre pourquoi le débogueur ignorée une entrée de visualisation et pour voir la syntaxe sous-jacente et les erreurs d’analyse. 

**Pour activer le diagnostic Natvis :**

- Sous **outils** > **Options** (ou **déboguer** > **Options**) > **dedébogage**  >  **Fenêtre sortie**, affectez la valeur **messages de diagnostic Natvis (C++ uniquement)** à **erreur**, **avertissement**, ou  **Verbose**, puis sélectionnez **OK**. 

Les erreurs apparaissent dans le **sortie** fenêtre.  

##  <a name="BKMK_Syntax_reference"></a> Référence à la syntaxe Natvis  

###  <a name="BKMK_AutoVisualizer"></a> Élément AutoVisualizer  
L’élément `AutoVisualizer` est le nœud racine du fichier *.natvis* et contient l’attribut `xmlns:` de l’espace de noms. 

```xml
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

Le `AutoVisualizer` élément peut avoir [Type](#BKMK_Type), [HResult](#BKMK_HResult), [UIVisualizer](#BKMK_UIVisualizer), et [CustomVisualizer](#BKMK_CustomVisualizer) enfants. 

###  <a name="BKMK_Type"></a> Type, élément  

Base `Type` ressemble à ceci :  

```xml
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  
```  

 Le `Type` élément spécifie :  

1. Le type de la visualisation doit être utilisé pour (le `Name` attribut).  
   
2. la valeur à laquelle doit ressembler un objet de ce type (élément `DisplayString` ) ;  
   
3. À quoi les membres du type doivent ressembler quand l’utilisateur développe le type dans une fenêtre de variable (le `Expand` nœud).  
   
#### <a name="templated-classes"></a>Classes basées sur un modèle
Le `Name` attribut de la `Type` élément accepte l’astérisque `*` comme un caractère générique qui peut être utilisé pour les noms de classes basé sur un modèle.  

Dans l’exemple suivant, la même visualisation est utilisée si l’objet est un `CAtlArray<int>` ou un `CAtlArray<float>`. S’il existe une entrée de visualisation spécifique pour un `CAtlArray<float>`, puis elle est prioritaire sur la générique.  

```xml
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

Vous pouvez référencer des paramètres de modèle dans l’entrée de visualisation à l’aide de macros $T1, $T2 et ainsi de suite. Pour trouver des exemples de ces macros, consultez les fichiers *.natvis* fournis avec Visual Studio.  

####  <a name="BKMK_Visualizer_type_matching"></a> Correspondance des types de visualiseur  
Si une entrée de visualisation ne parvient pas à valider, la visualisation disponible suivante est utilisée.  

#### <a name="inheritable-attribute"></a>Attribut pouvant être hérité  
Le paramètre facultatif `Inheritable` attribut spécifie si une visualisation s’applique uniquement à un type de base ou à un type de base et tous les types dérivés. La valeur par défaut de `Inheritable` est `true`.  

Dans l’exemple suivant, la visualisation s’applique uniquement à la `BaseClass` type :  

```xml
<Type Name="Namespace::BaseClass" Inheritable="false">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

#### <a name="priority-attribute"></a>Attribut de priorité  

Le paramètre facultatif `Priority` attribut spécifie l’ordre dans lequel utiliser d’autres définitions, si une définition ne parvient pas à analyser. Les valeurs possibles de `Priority` sont : `Low`, `MediumLow`,`Medium`, `MediumHigh`, et `High`. La valeur par défaut est `Medium`. Le `Priority` fait la distinction entre les priorités au sein du même attribut *.natvis* fichier.  

L’exemple suivant analyse tout d’abord l’entrée qui correspond à la bibliothèque STL 2015. En cas d’échec d’analyse, il utilise l’autre entrée pour la version 2013 de la bibliothèque STL :  

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
Vous pouvez placer un `Optional` attribut sur n’importe quel nœud. Si une sous-expression à l’intérieur d’un nœud facultatif ne parvient pas à analyser, le débogueur ignore ce nœud, mais s’applique le reste de la `Type` règles. Dans le type suivant, `[State]` est obligatoire, mais `[Exception]` est facultatif.  Si `MyNamespace::MyClass` possède un champ nommé _`M_exceptionHolder`, à la fois le `[State]` nœud et le `[Exception]` nœud apparaît, mais s’il existe aucune `_M_exceptionHolder` champ uniquement le `[State]` nœud s’affiche.

```xml
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

###  <a name="BKMK_Condition_attribute"></a> Attribut Condition  

Le paramètre facultatif `Condition` attribut n’est disponible pour de nombreux éléments de visualisation et spécifie à quel moment utiliser une règle de visualisation. Si l’expression à l’intérieur de l’attribut condition correspond à `false`, la règle de visualisation ne s’applique pas. Si elle a la valeur `true`, ou il n’est pas `Condition` attribut, la visualisation s’applique. Vous pouvez utiliser cet attribut pour la logique if-else dans les entrées de visualisation. 

Par exemple, la visualisation suivante possède deux `DisplayString` éléments pour un type pointeur intelligent. Lorsque le `_Myptr` membre est vide, la condition de la première `DisplayString` élément se résout en `true`, pour que ce formulaire s’affiche. Lorsque le `_Myptr` membre n’est pas vide, la condition prend la valeur `false`et le second `DisplayString` affiche de l’élément.  

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

Le `IncludeView` et `ExcludeView` attributs spécifient les éléments pour afficher ou pas dans des vues spécifiques. Par exemple, dans la spécification Natvis de `std::vector`, le `simple` vue n’affiche pas le `[size]` et `[capacity]` éléments.

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

Vous pouvez utiliser la `IncludeView` et `ExcludeView` attributs sur les types et sur des membres individuels.  

###  <a name="BKMK_Versioning"></a> Élément Version  
Le `Version` élément étendues d’une entrée de visualisation à un module spécifique et une version. Le `Version` élément permet d’éviter les collisions de noms, réduit les correspondances par inadvertance et permet à différentes visualisations pour les versions de type différent.  

Si un fichier d’en-tête commun qui est utilisé par différents modules définit un type, la visualisation avec version s’affiche uniquement lorsque le type est dans la version du module spécifié.  

Dans l’exemple suivant, la visualisation est applicable uniquement pour le `DirectUI::Border` type trouvé dans le `Windows.UI.Xaml.dll` à partir de la version 1.0 à 1.5. 

```xml
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

###  <a name="BKMK_DisplayString"></a> Élément DisplayString 
Le `DisplayString` élément spécifie une chaîne à afficher en tant que la valeur d’une variable. Il accepte les chaînes arbitraires mélangées à des expressions. Tout ce qui figure entre accolades est interprété comme une expression. Par exemple, ce qui suit `DisplayString` entrée :  

```xml
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  
```  

Signifie que les variables de type `CPoint` afficher comme dans cette illustration :  

 ![Utiliser un élément DisplayString](../debugger/media/dbg_natvis_cpoint_displaystring.png "utiliser un élément DisplayString")  

Dans le `DisplayString` expression, `x` et `y`, qui sont membres de `CPoint`, sont à l’intérieur des accolades, donc leurs valeurs sont évaluées. L’exemple montre également comment échapper une accolade en utilisant des accolades doubles ( `{{` ou `}}` ).  

> [!NOTE]
> L'élément `DisplayString` est le seul élément qui accepte des chaînes arbitraires et la syntaxe avec accolades. Tous les autres éléments de visualisation acceptent uniquement les expressions que le débogueur peut évaluer.  

###  <a name="BKMK_StringView"></a> Élément de StringView 

Le `StringView` élément définit une valeur que le débogueur peut envoyer au visualiseur de texte intégré. Par exemple, étant donné la visualisation suivante pour le `ATL::CStringT` type :  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>
```  

Le `CStringT` objet s’affiche dans une fenêtre de variables comme dans cet exemple :   

![Élément CStringT DisplayString](../debugger/media/dbg_natvis_displaystring_cstringt.png "élément CStringT DisplayString")  

Ajout d’un `StringView` élément indique au débogueur il peut afficher la valeur sous la forme une visualisation de texte.  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

Pendant le débogage, vous pouvez sélectionner l’icône de loupe qui se trouve en regard de la variable, puis sélectionnez **visualiseur de texte** pour afficher la chaîne qui **m_pszData** pointe vers.  

 ![Données CStringT avec visualiseur StringView](../debugger/media/dbg_natvis_stringview_cstringt.png "données CStringT avec visualiseur StringView")  

L’expression `{m_pszData,su}` inclut un spécificateur de format C++ **su**, pour afficher la valeur sous forme de chaîne Unicode. Pour plus d’informations, consultez [Format specifiers dans C++](../debugger/format-specifiers-in-cpp.md).  

###  <a name="BKMK_Expand"></a> Développez l’élément 

Le paramètre facultatif `Expand` nœud personnalise les enfants d’un type visualisé quand vous développez le type dans une fenêtre de variable. Le `Expand` nœud accepte une liste de nœuds enfants qui définissent les éléments enfants.  

- Si un `Expand` nœud n’est pas spécifié dans une entrée de visualisation, les enfants utilisent les règles d’expansion par défaut.  
  
- Si un `Expand` nœud est spécifié sans nœuds enfants dans cette section, le type n’est pas extensible dans les fenêtres du débogueur.  

####  <a name="BKMK_Item_expansion"></a> Expansion d'éléments  

 Le `Item` est le meilleur parti des élément de base et courants dans un `Expand` nœud. `Item` définit un seul élément enfant. Par exemple, un `CRect` classe avec des champs `top`, `left`, `right`, et `bottom` a l’entrée de visualisation suivante :  

```xml
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  
```  

Dans la fenêtre du débogueur, le `CRect` type ressemble à cet exemple :  

![CRect avec expansion d’élément Item](../debugger/media/dbg_natvis_expand_item_crect1.png "CRect avec expansion d’élément Item")  

Le débogueur évalue les expressions spécifiées dans le `Width` et `Height` éléments et affiche les valeurs dans le **valeur** colonne de la fenêtre de variables. 

Le débogueur crée automatiquement le **[affichage brut]** nœud pour chaque extension personnalisée. La capture d’écran précédente affiche la **[affichage brut]** nœud développé, pour montrer comment l’affichage brut de la valeur par défaut de l’objet diffère de sa visualisation Natvis. L’expansion par défaut crée une sous-arborescence pour la classe de base et répertorie tous les membres de données de la classe de base en tant qu’enfants.  

> [!NOTE]
> Si l’expression de l’élément item pointe vers un type complexe, le **élément** nœud lui-même est extensible.  

####  <a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion  
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

![std::Vector utilisant une expansion ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_stdvector.png "std::vector utilisant une expansion ArrayItems")  

Le `ArrayItems` nœud doit avoir :  

- une expression `Size` (qui doit prendre la valeur d’un entier) pour que le débogueur comprenne la longueur du tableau.  
- Un `ValuePointer` expression qui pointe vers le premier élément (qui doit être un pointeur d’un type d’élément qui n’est pas `void*`).  

La valeur par défaut de la limite inférieure du tableau est 0. Pour remplacer la valeur, utilisez un `LowerBound` élément. Le *.natvis* comportent des exemples de fichiers fournis avec Visual Studio.  

>[!NOTE]
>Vous pouvez utiliser la `[]` opérateur, par exemple `vector[i]`, avec n’importe quel visualisation d’un tableau unidimensionnel qui utilise `ArrayItems`, même si le type lui-même (par exemple `CATLArray`) n’autorise pas cet opérateur.  

Vous pouvez également spécifier des tableaux multidimensionnels. Dans ce cas, le débogueur doit légèrement plus d’informations pour afficher correctement les éléments enfants :  

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

- `Direction` Spécifie si le tableau est dans l’ordre ligne-major ou column-major. 
- `Rank` spécifie le rang du tableau. 
- L’élément `Size` accepte le paramètre `$i` implicite qu’il remplace par l’index de dimension pour déterminer la longueur du tableau dans cette dimension. Dans l’exemple précédent, l’expression `_M_extent.M_base[0]` doit indiquer la longueur de la dimension 0, `_M_extent._M_base[1]` le 1er et ainsi de suite.  

Voici comment une à deux dimensions `Concurrency::array` objet recherche dans la fenêtre du débogueur :  

![Tableau à deux dimensions avec expansion ArrayItems](../debugger/media/dbg_natvis_expand_arrayitems_2d.png "tableau à deux dimensions avec expansion ArrayItems")  

####  <a name="BKMK_IndexListItems_expansion"></a> Expansion d'IndexListItems  

Vous pouvez utiliser `ArrayItems` expansion uniquement si les éléments du tableau sont présentés de façon contiguë en mémoire. Le débogueur atteint l’élément suivant tout simplement en incrémentant son pointeur. Si vous devez manipuler l’index vers le nœud de valeur, utilisez `IndexListItems` nœuds. Voici une visualisation avec une `IndexListItems` nœud :  

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

La seule différence entre `ArrayItems` et `IndexListItems` est la `ValueNode`, lequel attend l’expression complète de l’i<sup>th</sup> élément avec le caractère implicite `$i` paramètre.  

>[!NOTE]
>Vous pouvez utiliser la `[]` opérateur, par exemple `vector[i]`, avec n’importe quel visualisation d’un tableau unidimensionnel qui utilise `IndexListItems`, même si le type lui-même (par exemple `CATLArray`) n’autorise pas cet opérateur.  

####  <a name="BKMK_LinkedListItems_expansion"></a> Expansion de LinkedListItems  

Si le type visualisé représente une liste liée, le débogueur peut afficher ses enfants à l'aide d'un nœud `LinkedListItems` . La visualisation suivante pour le `CAtlList` tapez utilise `LinkedListItems`:  

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

Le débogueur évalue la `NextPointer` et `ValueNode` expressions dans le contexte de la `LinkedListItems` élément du nœud, pas le type de liste parente. Dans l’exemple précédent, `CAtlList` a un `CNode` classe (trouvé dans `atlcoll.h`) qui est un nœud de la liste liée. `m_pNext` et `m_element` sont des champs de cette `CNode` (classe), pas de la `CAtlList` classe.  

`ValueNode` peut être laissée vide, ou utilisez `this` pour faire référence à la `LinkedListItems` nœud lui-même.  

#### <a name="customlistitems-expansion"></a>Expansion CustomListItems  
L'expansion `CustomListItems` vous permet d'écrire une logique personnalisée permettant de parcourir une structure de données telle qu'une table de hachage. Utilisez `CustomListItems` visualiser des structures de données qui utilisent des expressions C++ pour tout ce dont vous avez besoin pour évaluer, et non pas tout à fait au moule pour ajuster `ArrayItems`, `IndexListItems`, ou `LinkedListItems`.  

Le visualiseur suivant pour `CAtlMap` est un excellent exemple où `CustomListItems` est appropriée.  

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

Vous pouvez utiliser `Exec` pour exécuter du code à l’intérieur d’un `CustomListItems` expansion, à l’aide des variables et objets définis dans l’expansion. Vous pouvez utiliser des opérateurs logiques, les opérateurs arithmétiques et les opérateurs d’assignation avec `Exec`. Vous ne pouvez pas utiliser `Exec` pour évaluer les fonctions.

`CustomListItems` prend en charge les fonctions intrinsèques suivantes :

- `strlen`, `wcslen`, `strnlen`, `wcsnlen`, `strcmp`, `wcscmp`, `_stricmp`, `_strcmpi`, `_wcsicmp`, `strncmp`, `wcsncmp`, `_strnicmp`, `_wcsnicmp`, `memcmp`, `memicmp`, `wmemcmp`, `strchr`, `wcschr`, `memchr`, `wmemchr`, `strstr`, `wcsstr`, `__log2`, `__findNonNull`
- `GetLastError`, `TlsGetValue`, `DecodeHString`, `WindowsGetStringLen`, `WindowsGetStringRawBuffer`, `WindowsCompareStringOrdinal`, `RoInspectCapturedStackBackTrace`, `CoDecodeProxy`, `GetEnvBlockLength`, `DecodeWinRTRestrictedException`, `DynamicMemberLookup`, `DecodePointer`, `DynamicCast`
- `ConcurrencyArray_OperatorBracket_idx // Concurrency::array<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArray_OperatorBracket_int // Concurrency::array<>::operator(int, int, ...)`
- `ConcurrencyArray_OperatorBracket_tidx // Concurrency::array<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `ConcurrencyArrayView_OperatorBracket_idx // Concurrency::array_view<>::operator[index<>] and operator(index<>)`
- `ConcurrencyArrayView_OperatorBracket_int // Concurrency::array_view<>::operator(int, int, ...)`
- `ConcurrencyArrayView_OperatorBracket_tidx // Concurrency::array_view<>::operator[tiled_index<>] and operator(tiled_index<>)`
- `Stdext_HashMap_Int_OperatorBracket_idx`
- `Std_UnorderedMap_Int_OperatorBracket_idx`
- `TreeTraverse_Init // Initializes a new tree traversal`
- `TreeTraverse_Next // Returns nodes in a tree`
- `TreeTraverse_Skip // Skips nodes in a pending tree traversal`

####  <a name="BKMK_TreeItems_expansion"></a> Expansion de TreeItems  
 Si le type visualisé représente une arborescence, le débogueur peut la parcourir et afficher ses enfants à l'aide d'un nœud `TreeItems` . Voici la visualisation pour le `std::map` type à l’aide un `TreeItems` nœud :  

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

La syntaxe est semblable à la `LinkedListItems` nœud. `LeftPointer`, `RightPointer`, et `ValueNode` sont évaluées dans le contexte de la classe de nœud d’arborescence. `ValueNode` peut être laissée vide ou utiliser `this` pour faire référence à la `TreeItems` nœud lui-même.  

####  <a name="BKMK_ExpandedItem_expansion"></a> Expansion d'ExpandedItem  
 Le `ExpandedItem` élément génère un affichage agrégé des enfants en affichant les propriétés des membres de données ou les classes de base comme s’ils étaient des enfants du type visualisé. Le débogueur évalue l’expression spécifiée et ajoute les nœuds enfants du résultat à la liste des enfants du type visualisé. 

Par exemple, le type de pointeur intelligent `auto_ptr<vector<int>>` affiche généralement sous la forme :  

 ![Auto&#95;ptr&#60;vecteur&#60;int&#62; &#62; expansion par défaut](../debugger/media/dbg_natvis_expand_expandeditem_default.png "expansion par défaut")  

 Pour afficher les valeurs du vecteur, vous devez descendre de deux niveaux dans la fenêtre variable, en passant par la `_Myptr` membre. En ajoutant un élément `ExpandedItem` , vous pouvez éliminer la variable `_Myptr` de la hiérarchie et afficher directement les éléments du vecteur :  

```xml
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  
```  

 ![Auto&#95;ptr&#60;vecteur&#60;int&#62; &#62; d’ExpandedItem](../debugger/media/dbg_natvis_expand_expandeditem_visualized.png "d’ExpandedItem")  

L’exemple suivant montre comment agréger des propriétés de la classe de base dans une classe dérivée. Supposons que la classe `CPanel` dérive de la classe `CFrameworkElement`. Au lieu de répéter les propriétés qui proviennent de la base de `CFrameworkElement` (classe), le `ExpandedItem` visualisation de nœud ajoute ces propriétés à la liste enfant de la `CPanel` classe. 

```xml
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  
```  

Le spécificateur de format **nd** qui désactive l’association de la visualisation de la classe dérivée est ici nécessaire. Sinon, l’expression `*(CFrameworkElement*)this` provoquerait la `CPanel` visualisation à appliquer à nouveau, étant donné que les règles de correspondance de type de la visualisation par défaut considérez-la comme celui qui est plus approprié. Utiliser le **nd** spécificateur pour indiquer au débogueur d’utiliser la visualisation de la classe de base ou l’expansion par défaut si la classe de base ne possède aucune visualisation de format.  

####  <a name="BKMK_Synthetic_Item_expansion"></a> Expansion de l’élément Synthetic  
 Alors que l’élément `ExpandedItem` offre une vue plus plate des données en éliminant les hiérarchies, le nœud `Synthetic` fait exactement le contraire. Il vous permet de créer un élément enfant artificiel qui n’est pas un résultat d’une expression. L’élément artificiel peut avoir ses propres éléments enfants. Dans l'exemple suivant, la visualisation du type `Concurrency::array` utilise un nœud `Synthetic` pour présenter un message de diagnostic à l'utilisateur :  

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

 ![Concurrence::tableau avec expansion d’élément synthétique](../debugger/media/dbg_natvis_expand_synthetic.png "concurrence::tableau avec expansion d’élément synthétique")  

###  <a name="BKMK_HResult"></a> Élément de HResult 
 Le `HResult` élément vous permet de personnaliser les informations affichées pour un **HRESULT** dans les fenêtres du débogueur. L’élément `HRValue` doit contenir la valeur 32 bits du **HRESULT** à personnaliser. Le `HRDescription` élément contient les informations à afficher dans la fenêtre du débogueur.  

```xml

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

###  <a name="BKMK_UIVisualizer"></a> Élément UIVisualizer 
Un élément `UIVisualizer` permet d'inscrire un plug-in de visualiseur graphique auprès du débogueur. Un visualiseur graphique crée une boîte de dialogue ou une autre interface illustrant une variable ou un objet de manière cohérente avec son type de données. Le plug-in de visualiseur doit être créé comme un [VSPackage](../extensibility/internals/vspackages.md)et doit exposer un service que le débogueur peut consommer. Le *.natvis* fichier contient des informations d’inscription pour le plug-in, telles que son nom, le GUID du service exposé et les types qu’il peut visualiser.  

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

- Un `ServiceId`  -  `Id` paire attribut identifie un `UIVisualizer`. Le `ServiceId` est le GUID du service le visualiseur expose de package. `Id` est un identificateur unique qui différencie les visualiseurs, si un service en propose plusieurs. Dans l’exemple précédent, le même service de visualiseur fournit deux visualiseurs.  
  
- Le `MenuName` attribut définit un nom de visualiseur à afficher dans la liste déroulante en regard de l’icône de loupe qui se trouve dans le débogueur. Par exemple :  

  ![Menu contextuel du menu UIVisualizer](../debugger/media/dbg_natvis_vectorvisualizer.png "menu contextuel du menu UIVisualizer")  

Chaque type défini dans le *.natvis* fichier doit répertorier explicitement les visualiseurs d’interface utilisateur peuvent l’afficher. Le débogueur associe les références de visualiseur dans les entrées de type avec les visualiseurs inscrits. Par exemple, ce qui suit tapez entrée pour `std::vector` références le `UIVisualizer` dans l’exemple précédent.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Vous pouvez voir un exemple d’un `UIVisualizer` dans le [Image Watch](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.ImageWatch2017) extension utilisée pour afficher des bitmaps en mémoire. 

### <a name="BKMK_CustomVisualizer"></a>Élément CustomVisualizer  
 `CustomVisualizer` est un point d’extensibilité qui spécifie une extension VSIX que vous écrivez pour contrôler les visualisations dans Visual Studio code. Pour plus d’informations sur l’écriture d’extensions VSIX, consultez le [Visual Studio SDK](../extensibility/visual-studio-sdk.md). 

Il est beaucoup plus de travail pour écrire un visualiseur personnalisé à une définition Natvis de XML, mais vous êtes libre de toute contrainte relative à ce que fait Natvis ou ne prend en charge. Les visualiseurs personnalisés ont accès à l’ensemble complet de l’extensibilité du débogueur API, ce qui peuvent interroger et modifier le processus du programme débogué ou communiquer avec d’autres parties de Visual Studio.  

 Vous pouvez utiliser la `Condition`, `IncludeView`, et `ExcludeView` sur des attributs `CustomVisualizer` éléments.
