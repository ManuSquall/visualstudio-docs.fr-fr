---
title: Créer des vues personnalisées d’objets natifs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- natvis
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2d9a177a-e14b-404f-a6af-49498eff0bd7
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a510c522723cf991c7a3fff21542a069a3de000a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299486"
---
# <a name="create-custom-views-of-native-objects"></a>Créer des vues personnalisées d’objets natifs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'infrastructure Natvis de Visual Studio vous permet de personnaliser la façon dont Visual Studio affiche les types natifs dans les fenêtres de variables du débogueur (par exemple, les fenêtres **Espion**, **Variables locales**et **DataTips** ).  

 Natvis remplace le fichier **autoexp.dat** utilisé dans les versions antérieures de Visual Studio et propose la syntaxe XML, de meilleurs diagnostics, le contrôle de version et la prise en charge de plusieurs fichiers.  

> [!NOTE]
> Vous ne pouvez pas utiliser l'infrastructure Natvis pour les visualisations dans les cas suivants :  
> 
> - Vous effectuez le débogage d'un projet de bureau Windows C++ avec le type de débogueur **mixte**.  
>   - Vous effectuez un débogage en mode mixte dans une application de bureau Windows en mode de compatibilité managé (**Outils / Options / Débogage / Général / Utiliser le mode de compatibilité managé**).  
>   - Vous effectuez un débogage dans une application de bureau Windows en mode de compatibilité native (**Outils / Options / Débogage / Général / Utiliser le mode de compatibilité native**).  

## <a name="BKMK_Why_create_visualizations_"></a> Pourquoi créer des visualisations Natvis ?  
 Vous pouvez utiliser l'infrastructure Natvis pour créer des règles de visualisation pour les types que vous créez, afin que les développeurs puissent les voir facilement en phase de débogage.  

 Par exemple, l’image ci-dessous montre une variable de type [Windows::UI::Xaml::Controls::TextBox](https://go.microsoft.com/fwlink/?LinkId=258422) qui s’affiche dans le débogueur sans aucune visualisation personnalisée appliquée.  

 ![Visualisation par défaut de la zone de texte](../debugger/media/dbg-natvis-textbox-default.png "DBG_NATVIS_TextBox_Default")  

 La ligne en surbrillance montre la propriété `Text` de la classe `TextBox` . La hiérarchie de classes complexe rend difficile la recherche de cette valeur. De plus, le débogueur ne sait pas comment interpréter le type de chaîne personnalisé utilisé par l'objet, si bien que vous ne pouvez pas voir la chaîne figurant dans la zone de texte.  

 Le même objet `TextBox` semble beaucoup plus simple dans la fenêtre de variable quand les règles de visualisation personnalisées sont appliquées. Il est possible d'afficher ensemble les membres importants de la classe, et le débogueur montre la valeur de chaîne sous-jacente du type de chaîne personnalisé.  

 ![Données de zone de texte à l’aide du visualiseur](../debugger/media/dbg-natvis-textbox-visualizer.png "DBG_NATVIS_TextBox_Visualizer")  

## <a name="BKMK_Using_Natvis_files"></a> Utilisation de fichiers Natvis  
 Les fichiers .natvis sont des fichiers XML avec une extension .natvis. Le schéma est défini dans **%VSINSTALLDIR%\Xml\Schemas\natvis.xsd**.  

 La structure de base d’un fichier .natvis est constituée d’un ou de plusieurs éléments `Type` , où chaque élément `Type` représente une entrée de visualisation pour un type dont le nom qualifié complet est spécifié dans l’attribut `Name` .  

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

 Visual Studio fournit certains fichiers .natvis dans le dossier **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers** . Ces fichiers contiennent des règles de visualisation pour de nombreux types communs et ils peuvent servir d'exemples pour écrire des visualisations pour de nouveaux types.  

## <a name="adding-natvis-files-to-your-projects"></a>Ajout de fichiers .natvis à vos projets  
 Vous pouvez ajouter des fichiers .natvis à tout projet C++.  

 Pour ajouter un nouveau fichier .natvis, avec un projet C++ ouvert, sélectionnez le nœud du projet dans l’ **Explorateur de solutions**et cliquez sur **Ajouter / Nouvel élément / Visual C++ / Utilitaire / Fichier de visualisation du débogueur (.natvis)** . Le débogueur charge automatiquement les fichiers Natvis des projets C++. Par défaut, les fichiers Natvis de votre projet sont également insérés dans le fichier .pdb généré par le projet. Cela signifie que si vous déboguez le fichier binaire généré par ce projet, le débogueur charge le fichier Natvis à partir du fichier .pdb même si le projet n'est pas ouvert. Si vous ne voulez pas que le fichier .natvis soit inclus dans le fichier .pdb, cliquez sur le fichier .natvis dans l’ **Explorateur de solutions**et, dans la fenêtre **Propriétés de configuration** , définissez **Exclu de la génération** sur **Oui**.  

 Il est recommandé de modifier les fichiers Natvis à l'aide de Visual Studio. Toutes les modifications que vous apportez pendant le débogage prennent effet automatiquement quand vous enregistrez le fichier. Vous bénéficiez également d'une meilleure expérience d'édition IntelliSense.  

 Les fichiers Natvis chargés à partir d'un fichier .pdb s'appliquent uniquement aux types dans le module auquel le fichier .pdb fait référence. Par exemple, si Module1.pdb définit une entrée pour un type nommé `Test`, cette entrée s’applique seulement à la classe **Test** dans Module1.dll. Si un autre module définit également une classe nommée **Test**, l’entrée natvis du fichier Module1.pdb ne s’y applique pas.  

## <a name="BKMK_natvis_location"></a> Déploiement de fichiers .natvis  
 Si votre fichier .natvis s’applique seulement aux types que vous créez dans un projet Visual Studio, vous n’avez rien à faire, car le fichier .natvis est inclus dans le fichier .pdb. Vous pouvez cependant ajouter des fichiers .natvis dans votre répertoire utilisateur ou dans un répertoire système si vous voulez qu’ils s’appliquent à plusieurs projets.  

 L’ordre dans lequel les fichiers .natvis sont évalués est le suivant :  

1. les fichiers .natvis incorporés dans un fichier .pdb que vous déboguez (sauf si un fichier du même nom existe dans un projet chargé) ;  

2. les fichiers .natvis qui font partie d’un projet C++ chargé ou d’un élément de solution du plus haut niveau. Ceci comprend tous les projets C++ chargés, notamment les bibliothèques de classes, mais pas les projets dans d’autres langages (par exemple, vous ne pouvez pas charger un fichier .natvis d’un projet C++). Pour les projets exécutables, vous devez utiliser les éléments de solution pour héberger les fichiers .natvis qui ne sont pas déjà présents dans un fichier .pdb, car aucun projet C++ est disponible.  

3. Le répertoire natvis spécifique à l'utilisateur ( **%USERPROFILE%\My Documents\Visual Studio 2015\Visualizers**).  

4. Le répertoire Natvis à l'échelle du système ( **%VSINSTALLDIR%\Common7\Packages\Debugger\Visualizers**). C’est l’emplacement où les fichiers .natvis installés avec Visual Studio sont copiés. Vous pouvez ajouter également d'autres fichiers dans ce répertoire si vous disposez des autorisations d'administrateur.  

## <a name="modifying-natvis-files-while-debugging"></a>Modification des fichiers .natvis pendant le débogage  
 Vous pouvez modifier un fichier .natvis dans l’environnement IDE pendant le débogage du projet dans lequel il est inclus. Ouvrez le fichier dans l'IDE (à l'aide de l'instance de Visual Studio que vous utilisez pour le débogage), modifiez-le et enregistrez-le. Dès que le fichier est enregistré, les fenêtres **Espion** et **Variables locales** doivent être mises à jour pour refléter la modification. Si vous modifiez le fichier .natvis en dehors de l’IDE, les modifications ne prennent pas effet automatiquement. Pour mettre à jour les fenêtres, vous pouvez évaluer la commande **.natvisreload** dans la fenêtre **Espion** . Cela entraîne la prise en compte des modifications sans redémarrer la session de débogage.  

 Vous pouvez aussi ajouter ou supprimer des fichiers .natvis dans une solution que vous déboguez : Visual Studio ajoutera ou supprimera les visualisations appropriées.  

 Vous ne pouvez pas modifier un fichier .natvis en phase de débogage s’il est incorporé dans un fichier .pdb.  

 Utilisez la commande **.natvisreload** quand vous mettez à niveau le fichier .natvis vers une version plus récente (par exemple s’il est archivé dans le contrôle de code source et que vous voulez reprendre les modifications récentes qu’une autre personne a apportées au fichier). Il est recommandé de modifier les fichiers natvis à l'aide de l'éditeur XML de Visual Studio.  

## <a name="BKMK_Expressions_and_formatting"></a> Expressions et mise en forme  
 Les visualisations Natvis utilisent des expressions C++ pour spécifier les éléments de données à afficher. En plus des améliorations et des limitations des C++ expressions dans le débogueur qui sont décrites dans opérateur de [contexte (C++)](../debugger/context-operator-cpp.md), vous devez tenir compte des différences suivantes :  

- Les expressions Natvis sont évaluées dans le contexte de l'objet qui est visualisé, et non dans le frame de pile actuel. Par exemple, si vous utilisez `x` dans une expression Natvis, cela fait référence au champ nommé `x` dans l'objet qui est visualisé, et non à une variable locale nommée `x` dans la fonction en cours d'exécution. Vous ne pouvez pas accéder aux variables locales dans des expressions Natvis, même si vous pouvez accéder aux variables globales.  

- Les expressions de Natvis n'autorisent pas l'évaluation de fonctions ni les effets secondaires. Cela signifie que les appels de fonction et les opérateurs d'assignation sont ignorés. Comme les [fonctions intrinsèques du débogueur](../debugger/expressions-in-the-debugger.md#BKMK_Using_debugger_intrinisic_functions_to_maintain_state) n'ont pas d'effets secondaires, elles peuvent librement être appelées à partir de toute expression Natvis, même si d'autres appels de fonction sont interdits.  

  Pour contrôler l’affichage d’une expression dans une fenêtre de variables, vous pouvez utiliser l’un des spécificateurs de format décrits dans la section [spécificateurs de format](../debugger/format-specifiers-in-cpp.md#BKMK_Visual_Studio_2012_format_specifiers) des [spécificateurs de format C++ dans](../debugger/format-specifiers-in-cpp.md) la rubrique. Notez que les spécificateurs de format sont ignorés quand l’entrée de virtualisation est utilisée en interne par Natvis, comme l’expression `Size` dans une expansion ArrayItems.  

## <a name="natvis-views"></a>Vues Natvis  
 Les vues Natvis vous permettent de voir n'importe quel type de plusieurs façons. Par exemple, vous pouvez définir une vue nommée **simple** qui vous donne une vue simplifiée d’un type. Par exemple, voici la visualisation de `std::vector`:  

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

 Les éléments `DisplayString` et `ArrayItems` sont utilisés dans la vue par défaut et la vue simple, tandis que les éléments `[size]` et `[capacity]` sont exclus de la vue simple. Vous pouvez utiliser le spécificateur de format **,view** pour spécifier une autre vue. Dans la fenêtre **Espion** , vous spécifiez la vue simple sous la forme **vec,view(simple)** :  

 ![Fenêtre Espion avec affichage simple](../debugger/media/watch-simpleview.png "Watch-SimpleView")  

## <a name="BKMK_Diagnosing_Natvis_errors"></a> Diagnostic des erreurs Natvis  
 Vous pouvez utiliser les diagnostics Natvis pour résoudre des erreurs de syntaxe et d'analyse. Quand le débogueur rencontre des erreurs dans une entrée de visualisation, il ignore les erreurs et affiche le type dans sa forme brute ou reprend une autre visualisation appropriée. Pour comprendre pourquoi une certaine entrée de visualisation est ignorée et pour voir les erreurs sous-jacentes, vous pouvez activer l'option des diagnostics Natvis **Outils / Options / Débogage / Fenêtre Sortie / Messages de diagnostic Natvis (C++ uniquement)** . Les erreurs sont affichées dans la fenêtre **Sortie** .  

## <a name="BKMK_Syntax_reference"></a> Référence à la syntaxe Natvis  

### <a name="BKMK_AutoVisualizer"></a> Élément AutoVisualizer  
 L’élément `AutoVisualizer`  est le nœud racine du fichier .natvis et contient l’attribut `xmlns:` de l’espace de noms.  

```xml  
<?xml version="1.0" encoding="utf-8"?>  
<AutoVisualizer xmlns="http://schemas.microsoft.com/vstudio/debugger/natvis/2010">  
.  
.  
</AutoVisualizer>  
```  

### <a name="BKMK_Type"></a> Élément Type  
 Un Type de base ressemble à ceci :  

```xml  
<Type Name="[fully qualified type name]">  
  <DisplayString Condition="[Boolean expression]">[Display value]</DisplayString>  
  <Expand>  
    ...  
  </Expand>  
</Type>  

```  

 Il spécifie :  

1. le type pour lequel elle doit être utilisée (attribut `Type Name` ) ;  

2. la valeur à laquelle doit ressembler un objet de ce type (élément `DisplayString` ) ;  

3. à quoi les membres du type doivent ressembler quand l'utilisateur le développe dans une fenêtre de variable (nœud `Expand` ).  

   **Classes avec modèles** L'attribut `Name` de l'élément `Type` accepte l'astérisque `*` en tant que caractère générique dans les noms des classes avec modèles :  

```xml  
<Type Name="ATL::CAtlArray&lt;*&gt;">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  

```  

 Dans cet exemple, la même visualisation est utilisée que l'objet soit un `CAtlArray<int>` ou un `CAtlArray<float>`. S'il existe une entrée de visualisation spécifique pour un `CAtlArray<float>` , alors elle a la priorité sur la générique.  

 Notez qu'il est possible de faire référence à des paramètres de modèle dans l'entrée de visualisation à l'aide de macros $T1, $T2, et ainsi de suite. Pour rechercher des exemples de ces macros, consultez les fichiers .natvis fournis avec Visual Studio.  

#### <a name="BKMK_Visualizer_type_matching"></a> Correspondance des types de visualiseur  
 Si une entrée de visualisation ne parvient pas à être validée, la visualisation disponible suivante est utilisée.  

#### <a name="inheritable-attribute"></a>Attribut pouvant être hérité  
 Vous pouvez spécifier si une visualisation s'applique uniquement à un type de base ou à un type de base et à tous les types dérivés à l'aide de l'attribut facultatif `Inheritable` . Dans le code suivant, la visualisation s'applique uniquement au type `BaseClass` :  

```xml  
<Type Name="Namespace::BaseClass" Inheritable="true">  
    <DisplayString>{{Count = {m_nSize}}}</DisplayString>  
</Type>  
```  

 La valeur par défaut de `Inheritable` est `true`.  

#### <a name="priority-attribute"></a>Attribut de priorité  
 L'attribut `Priority` spécifie l'ordre dans lequel les autres définitions sont utilisées si une définition ne parvient pas à être analysée. Les valeurs possibles de `Priority` sont : `Low`, `MediumLow`,`Medium`, `MediumHigh`et `High`, et la valeur par défaut est `Medium`.  

 L’attribut Priority doit être utilisé seulement pour distinguer les priorités dans un même fichier .natvis, et non pas entre différents fichiers.  

 Dans l'exemple suivant, vous allez tout d'abord analyser l'entrée qui correspond à la bibliothèque STL 2015 et, en cas d'échec d'analyse, vous utiliserez l'autre entrée pour la version 2013 de la bibliothèque STL :  

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

#### <a name="BKMK_Versioning"></a> Élément Version  
 Utilisez l'élément `Version` pour définir l'étendue des visualisations à des modules spécifiques et à leurs versions afin que les collisions de nom soient réduites et que des visualisations différentes puissent être utilisées pour différentes versions des types. Exemple :  

```xml  
<Type Name="DirectUI::Border">  
  <Version Name="Windows.UI.Xaml.dll" Min="1.0" Max="1.5"/>  
  <DisplayString>{{Name = {*(m_pDO->m_pstrName)}}}</DisplayString>  
  <Expand>  
    <ExpandedItem>*(CBorder*)(m_pDO)</ExpandedItem>  
  </Expand>  
</Type>  
```  

 Dans cet exemple, la visualisation est applicable uniquement pour le type `DirectUI::Border` qui figure dans `Windows.UI.Xaml.dll` de la version 1.0 à 1.5. Notez que l'ajout d'éléments de version définit l'étendue de l'entrée de visualisation sur un module et une version spécifiques, et qu'il réduit les correspondances par inadvertance. En revanche, si un type est défini dans un fichier d'en-tête commun utilisé par différents modules, la visualisation avec version n'est pas appliquée quand le type n'est pas dans le module spécifié.  

#### <a name="optional-attribute"></a>Attribut Optional  
 L'attribut `Optional` peut apparaître sur n'importe quel nœud. Si une sous-expression quelconque figurant à l'intérieur d'un nœud facultatif ne parvient pas à être analysée, ce nœud est ignoré, mais le reste de l'élément Type est toujours valide. Dans le type suivant, `[State]` est obligatoire, mais `[Exception]` est facultatif.  Cela signifie que si `MyNamespace::MyClass` contient un champ nommé _`M_exceptionHolder`, vous verrez toujours les deux nœuds `[State]` et `[Exception]` , mais que si `_M_exceptionHolder` est manquant, vous verrez uniquement le nœud `[State]` .  

```xml  
<Type Name="MyNamespace::MyClass">  
    <Expand>  
      <Item Name="[State]">_M_State</Item>  
      <Item Name="[Exception]" Optional="true">_M_exceptionHolder</Item>  
    </Expand>  
</Type>  
```  

### <a name="BKMK_Condition_attribute"></a> Attribut Condition  
 L'attribut `Condition` facultatif est disponible pour de nombreux éléments de visualisation. Il indique quand une règle de visualisation doit être utilisée. Si la résolution de l'expression incluse dans l'attribut Condition est `false`, la règle de visualisation spécifiée par l'élément n'est pas appliquée. Si elle prend la valeur true, ou en l'absence d'attribut `Condition` , la règle de visualisation est appliquée au type. Vous pouvez utiliser cet attribut pour inclure une logique `if-else` dans les entrées de visualisation. Par exemple, la visualisation ci-dessous possède deux éléments `DisplayString` pour un type de pointeur intelligent :  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString Condition="_Myptr == 0">empty</DisplayString>  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 Quand le membre `_Myptr` a la valeur `null`, la condition du premier élément `DisplayString` prend la valeur `true`, si bien que ce formulaire s'affiche. Quand le membre `_Myptr` n'a pas la valeur `null`, la condition prend la valeur `false`et le second élément `DisplayString` s'affiche.  

### <a name="includeview-and-excludeview-attributes"></a>Attributs IncludeView et ExcludeView  
 Ces attributs spécifient les éléments qui doivent être affichés ou non dans les différentes vues. Par exemple, pour une spécification Natvis de `std::vector`donnée :  

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

 La vue simple n'affiche pas les éléments [taille] et [capacité] dans la vue simple. Si vous aviez utilisé `IncludeView="simple"` à la place de `ExcludeView`, les éléments `[size]` et `[capacity]` seraient affichés dans la vue simple et non pas dans la vue par défaut.  

 Vous pouvez utiliser les attributs `IncludeView` et `ExcludeView` sur des types, ainsi que sur des membres individuels.  

### <a name="BKMK_DisplayString"></a> DisplayString  
 Un élément `DisplayString` spécifie la chaîne à afficher comme valeur de la variable. Il accepte les chaînes arbitraires mélangées à des expressions. Tout ce qui figure entre accolades est interprété comme une expression. Par exemple, une entrée `DisplayString` comme celle-ci :  

```xml  
<Type Name="CPoint">  
  <DisplayString>{{x={x} y={y}}}</DisplayString>   
</Type>  

```  

 Signifie que les variables de type `CPoint` s'affichent comme suit :  

 ![Utilisation d’un élément DisplayString](../debugger/media/dbg-natvis-cpoint-displaystring.png "DBG_NATVIS_CPoint_DisplayString")  

 Dans l'expression `DisplayString` , `x` et `y`, qui sont membres de `CPoint`, sont entre des accolades, donc leurs valeurs sont évaluées. L'expression montre également comment échapper une accolade en utilisant des accolades doubles ( `{{` ou `}}` ).  

> [!NOTE]
> L'élément `DisplayString` est le seul élément qui accepte des chaînes arbitraires et la syntaxe avec accolades. Tous les autres éléments de visualisation acceptent uniquement les expressions qui sont évaluées par le débogueur.  

### <a name="BKMK_StringView"></a> StringView  
 L'élément `StringView` définit l'expression dont la valeur va être envoyée au visualiseur de texte intégré. Supposons, par exemple, que nous avons la visualisation suivante pour le type `ATL::CStringT` :  

```xml  
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
</Type>  

```  

 L'objet `CStringT` ressemble à ce qui suit :  

 ![CStringT DisplayString, élément](../debugger/media/dbg-natvis-displaystring-cstringt.png "DBG_NATVIS_DisplayString_CStringT")  

 La visualisation affiche un objet `CStringT` dans une fenêtre de variables comme celle-ci :  

 L'ajout d'un élément `StringView` indique au débogueur que cette valeur peut être affichée par une visualisation de texte :  

```xml
<Type Name="ATL::CStringT&lt;wchar_t,*&gt;">  
  <DisplayString>{m_pszData,su}</DisplayString>  
  <StringView>m_pszData,su</StringView>  
</Type>  
```  

 Remarquez l'icône de loupe située en regard de la valeur ci-dessous. Choisir l'icône lance le visualiseur de texte qui affiche la chaîne vers laquelle pointe `m_pszData` .  

 ![Données CStringT avec le visualiseur StringView](../debugger/media/dbg-natvis-stringview-cstringt.png "DBG_NATVIS_StringView_CStringT")  

> [!NOTE]
> Notez que l'expression `{m_pszData,su}` inclut un spécificateur de format C++, `su` , pour afficher la valeur sous forme de chaîne Unicode. Pour plus d'informations, voir [Format Specifiers in C++](../debugger/format-specifiers-in-cpp.md) .  

### <a name="BKMK_Expand"></a> Expand  
 Le nœud `Expand` est utilisé pour personnaliser les enfants du type visualisé quand l'utilisateur le développe dans les fenêtres de variables. Il accepte la liste des nœuds enfants qui définissent les éléments enfants.  

 Le nœud `Expand` est facultatif.  

- Si aucun nœud `Expand` n'est spécifié dans une entrée de visualisation, les règles d'expansion par défaut de Visual Studio sont utilisées.  

- Si un nœud `Expand` est spécifié sans aucun nœud enfant en dessous, le type ne peut pas être développé dans les fenêtres du débogueur.  

#### <a name="BKMK_Item_expansion"></a> Expansion d'éléments  
 L'élément `Item` est le plus basique et le plus courant des éléments utilisés dans un nœud `Expand` . `Item` définit un seul élément enfant. Supposons, par exemple, que vous ayez une classe `CRect` avec des champs `top`, `left`, `right`et `bottom` et l'entrée de visualisation suivante :  

```xml  
<Type Name="CRect">  
  <DisplayString>{{top={top} bottom={bottom} left={left} right={right}}}</DisplayString>  
  <Expand>  
    <Item Name="Width">right - left</Item>  
    <Item Name="Height">bottom - top</Item>  
  </Expand>  
</Type>  

```  

 Le type `CRect` se présentera comme suit :  

 ![CRect avec expansion d’élément Item](../debugger/media/dbg-natvis-expand-item-crect1.png "DBG_NATVIS_Expand_Item_CRect1")  

 Les expressions spécifiées dans les éléments `Width` et `Height` sont évaluées et elles s'affichent dans la colonne Valeur. Le nœud `[Raw View]` est automatiquement créé par le débogueur chaque fois qu'une expansion personnalisée est utilisée. Il est développé dans la capture d'écran ci-dessus pour montrer comment l'affichage brut de l'objet diffère de sa visualisation. L'expansion par défaut Visual Studio crée une sous-arborescence pour la classe de base et répertorie tous les membres de données de la classe de base en tant qu'enfants.  

> [!NOTE]
> Si l'expression de l'élément item pointe vers un type complexe, le nœud `Item` lui-même peut être développé.  

#### <a name="BKMK_ArrayItems_expansion"></a> ArrayItems expansion  
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

 ![std :: Vector avec expansion ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-stdvector.png "DBG_NATVIS_Expand_ArrayItems_StdVector")  

 Au minimum, le nœud `ArrayItems` doit avoir :  

1. une expression `Size` (qui doit prendre la valeur d'un entier) pour que le débogueur comprenne la longueur du tableau ;  

2. une expression `ValuePointer` qui doit pointer vers le premier élément (qui doit être un pointeur d'un type d'élément autre que `void*`).  

   La valeur par défaut de la limite inférieure du tableau est 0. Elle peut être remplacée en utilisant un élément `LowerBound` (des exemples sont donnés dans les fichiers .natvis livrés avec Visual Studio).  

   Vous pouvez maintenant utiliser l'opérateur `[]` avec une expansion `ArrayItems` , par exemple `vector[i]`. L'opérateur [] peut être utilisé avec n'importe quel visualisation d'un tableau unidimensionnel qui utilise `ArrayItems` ou `IndexListItems`,même si le type lui-même n'autorise pas cet opérateur (par exemple `CATLArray`).  

   Il est également possible de spécifier des tableaux multidimensionnels. Le débogueur a juste besoin d'un peu plus d'informations pour afficher correctement les éléments enfants dans ce cas :  

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

 `Direction` indique si l'ordre du tableau est row-major ou column-major. `Rank` spécifie le rang du tableau. L'élément `Size` accepte le paramètre `$i` implicite qu'il substitue par l'index de dimension pour déterminer la longueur du tableau dans cette dimension. Ainsi, dans l'exemple précédent ci-dessus, l'expression `_M_extent.M_base[0]` doit indiquer la longueur de la dimension 0, `_M_extent._M_base[1]` celle de la dimension 1, etc.  

 Voici ce à quoi un objet `Concurrency::array` à deux dimensions ressemble dans le débogueur :  

 ![Tableau à deux dimensions avec expansion ArrayItems](../debugger/media/dbg-natvis-expand-arrayitems-2d.png "DBG_NATVIS_Expand_ArrayItems_2D")  

#### <a name="BKMK_IndexListItems_expansion"></a> Expansion d'IndexListItems  
 Vous pouvez utiliser l'expansion `ArrayItems` , uniquement si les éléments du tableau sont disposés de façon contiguë en mémoire. Le débogueur atteint l'élément suivant tout simplement en incrémentant son pointeur vers l'élément actuel. Pour prendre en charge les cas où vous devez manipuler l'index du nœud de valeur, vous pouvez utiliser des nœuds `IndexListItems` . Voici une visualisation qui utilise le nœud `IndexListItems` :  

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

 Vous pouvez maintenant utiliser l'opérateur `[]` avec une expansion `IndexListItems` , par exemple `vector[i]`. L'opérateur `[]` peut être utilisé avec n'importe quelle visualisation d'un tableau unidimensionnel qui utilise `ArrayItems` ou `IndexListItems`, même si le type lui-même n'autorise pas cet opérateur (par exemple `CATLArray`).  

 La seule différence entre `ArrayItems` et `IndexListItems` est que `ValueNode` attend l'expression complète de l'élément i<sup>ème</sup> avec le paramètre `$i` implicite.  

#### <a name="BKMK_LinkedListItems_expansion"></a> Expansion de LinkedListItems  
 Si le type visualisé représente une liste liée, le débogueur peut afficher ses enfants à l'aide d'un nœud `LinkedListItems` . Voici la visualisation pour le type `CAtlList` qui utilise cette fonctionnalité :  

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

- Les expressions `NextPointer` et `ValueNode` sont évalués dans le contexte du nœud de la liste liée et non du type de la liste parent. Dans l'exemple ci-dessus, `CAtlList` a une classe `CNode` (située dans `atlcoll.h`) qui représente un nœud de la liste liée. `m_pNext` et `m_element` sont des champs de cette classe `CNode` et non de la classe `CAtlList` .  

- L'expression `ValueNode` peut être laissée vide ou utiliser `this` pour faire référence au nœud même de la liste liée.  

#### <a name="customlistitems-expansion"></a>Expansion CustomListItems  
 L'expansion `CustomListItems` vous permet d'écrire une logique personnalisée permettant de parcourir une structure de données telle qu'une table de hachage. Vous devez utiliser `CustomListItems` pour visualiser des structures de données dans lesquelles tout ce que vous devez évaluer peut être exprimé via des expressions C++ mais ne correspond pas tout à fait au moule pour `ArrayItems`, `TreeItems`ou `LinkedListItems.`  

 Le visualiseur pour CAtlMap est un excellent exemple où `CustomListItems` est approprié.  

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

#### <a name="BKMK_TreeItems_expansion"></a> Expansion de TreeItems  
 Si le type visualisé représente une arborescence, le débogueur peut la parcourir et afficher ses enfants à l'aide d'un nœud `TreeItems` . Voici la visualisation pour le type `std::map` qui utilise cette fonctionnalité :  

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

 La syntaxe est très similaire à celle du nœud `LinkedListItems` . `LeftPointer`, `RightPointer`et `ValueNode` sont évalués dans le contexte de la classe du nœud de l'arborescence et l'expression `ValueNode` peut être laissée vide ou utiliser `this` pour faire référence au nœud même de l'arborescence.  

#### <a name="BKMK_ExpandedItem_expansion"></a> Expansion d'ExpandedItem  
 L'élément `ExpandedItem` peut servir à générer un affichage agrégé des enfants en présentant les propriétés des classes de base ou des membres de données comme s'ils étaient des enfants du type visualisé. L'expression spécifiée est évaluée et les nœuds enfants du résultat sont ajoutés à la liste enfant du type visualisé. Supposons, par exemple, que vous ayez un type de pointeur intelligent `auto_ptr<vector<int>>` qui se présente généralement comme suit :  

 ![développement&#95;par&#60;défaut&#60;de&#62; &#62; Vector PTR automatique int](../debugger/media/dbg-natvis-expand-expandeditem-default.png "DBG_NATVIS_Expand_ExpandedItem_Default")  

 Pour voir les valeurs du vecteur, vous devez descendre de deux niveaux dans la fenêtre de variables en passant par le membre _Myptr. En ajoutant un élément `ExpandedItem` , vous pouvez éliminer la variable `_Myptr` de la hiérarchie et afficher directement les éléments du vecteur :  

```xml  
<Type Name="std::auto_ptr&lt;*&gt;">  
  <DisplayString>auto_ptr {*_Myptr}</DisplayString>  
  <Expand>  
    <ExpandedItem>_Myptr</ExpandedItem>  
  </Expand>  
</Type>  

```  

 ![développement&#95;de&#60;Vector&#60;PTR&#62; &#62; automatique int ExpandedItem](../debugger/media/dbg-natvis-expand-expandeditem-visualized.png "DBG_NATVIS_Expand_ExpandedItem_Visualized")  

 L'exemple ci-dessous montre comment agréger des propriétés de la classe de base dans une classe dérivée. Supposons que la classe `CPanel` dérive de la classe `CFrameworkElement`. Au lieu de répéter les propriétés provenant de la classe `CFrameworkElement` de base, le nœud `ExpandedItem` permet à ces propriétés d'être ajoutées à la liste enfant de la classe `CPanel` . Le spécificateur de format **nd** qui désactive l'association de la visualisation de la classe dérivée est ici nécessaire. Sinon, l'expression `*(CFrameworkElement*)this` entraîne une nouvelle application de la visualisation `CPanel` car les règles d'association des types de visualisation par défaut la considèrent comme la plus appropriée. L'utilisation du spécificateur de format **nd** oblige le débogueur à utiliser la visualisation de la classe de base ou l'expansion par défaut de la classe de base si cette dernière n'a pas de visualisation.  

```xml  
<Type Name="CPanel">  
  <DisplayString>{{Name = {*(m_pstrName)}}}</DisplayString>  
  <Expand>  
    <Item Name="IsItemsHost">(bool)m_bItemsHost</Item>  
    <ExpandedItem>*(CFrameworkElement*)this,nd</ExpandedItem>  
  </Expand>  
</Type>  

```  

#### <a name="BKMK_Synthetic_Item_expansion"></a> Expansion de l'élément Synthetic  
 Alors que l'élément `ExpandedItem` offre une vue plus plate des données en éliminant les hiérarchies, le nœud `Synthetic` fait exactement le contraire. Il vous permet de créer un élément enfant artificiel (c'est-à-dire, un élément enfant qui n'est pas le résultat d'une expression). Cet élément enfant peut contenir ses propres éléments enfants. Dans l'exemple suivant, la visualisation du type `Concurrency::array` utilise un nœud `Synthetic` pour présenter un message de diagnostic à l'utilisateur :  

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

 ![Concurrency :: Array avec expansion, élément sythentic](../debugger/media/dbg-natvis-expand-synthetic.png "DBG_NATVIS_Expand_Synthetic")  

### <a name="BKMK_HResult"></a> HResult  
 L'élément `HResult` vous permet de personnaliser les informations affichées pour un HRESULT dans les fenêtres du débogueur. L'élément `HRValue` doit contenir la valeur 32 bits du HRESULT à personnaliser. L'élément `HRDescription` contient les informations affichées dans le débogueur.  

```  

<HResult Name="MY_E_COLLECTION_NOELEMENTS">  
  <HRValue>0xABC0123</HRValue>  
  <HRDescription>No elements in the collection.</HRDescription>  
</HResult>  
```  

### <a name="BKMK_UIVisualizer"></a> UIVisualizer  
 Un élément `UIVisualizer` permet d'inscrire un plug-in de visualiseur graphique auprès du débogueur. Un plug-in de visualiseur graphique crée une boîte de dialogue ou une autre interface pour afficher une variable ou un objet de manière appropriée par rapport à son type de données. Il doit être créé en tant que [VSPackage](../extensibility/internals/vspackages.md) et il doit exposer un service consommable par le débogueur. Le fichier .natvis contient les informations d’inscription du plug-in, comme son nom, le GUID du service exposé et les types qu’il peut visualiser.  

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

 Un élément `UIVisualizer` est identifié par une paire d’attributs `ServiceId` - `Id` . `ServiceId` correspond au GUID du service exposé par le package du visualiseur. `Id` correspond à un identificateur unique pouvant servir à différencier les visualiseurs si un service en propose plusieurs. Dans l'exemple ci-dessus, le même service de visualiseur fournit deux visualiseurs.  

 L'attribut `MenuName` correspond au nom du visualiseur que voient les utilisateurs quand ils ouvrent le menu contextuel situé en regard de l'icône de loupe dans les fenêtres de variables du débogueur, comme dans cet exemple :  

 ![Menu contextuel du menu UIVisualizer](../debugger/media/dbg-natvis-vectorvisualizer.png "DBG_NATVIS_VectorVisualizer")  

 Chaque type défini dans le fichier .natvis doit explicitement répertorier les visualiseurs d’interface utilisateur capables de l’afficher. Le débogueur associe les références de visualiseur incluses dans les entrées de type aux types avec les visualiseurs inscrits. Par exemple, l'entrée de type suivante pour `std::vector` fait référence au UIVisualizer de notre exemple ci-dessus.  

```xml
<Type Name="std::vector&lt;int,*&gt;">  
  <UIVisualizer ServiceId="{5452AFEA-3DF6-46BB-9177-C0B08F318025}" Id="1" />  
</Type>  
```  

 Vous pouvez voir un exemple de UIVisualizer dans l’extension Image Watch utilisée pour afficher des images bitmap en mémoire : [ImageWatch](https://visualstudiogallery.msdn.microsoft.com/e682d542-7ef3-402c-b857-bbfba714f78d)  

### <a name="customvisualizer-element"></a>Élément CustomVisualizer  
 `CustomVisualizer` est un point d'extensibilité qui spécifie une extension VSIX que vous pouvez écrire pour contrôler la visualisation dans le code qui s'exécute dans Visual Studio. Pour plus d’informations sur l’écriture d’extensions VSIX, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md). L'écriture d'un visualiseur personnalisé représente beaucoup plus de travail que l'écriture d'une définition natvis XML, mais vous êtes libre de toute contrainte relative à ce que natvis prend ou non en charge. Les visualiseurs personnalisés ont accès à l'ensemble des API d'extensibilité du débogueur, qui peuvent être utilisées pour interroger et modifier le processus du programme débogué ou pour communiquer avec d'autres parties de Visual Studio.  

 Vous pouvez utiliser les attributs `Condition`, `IncludeView`et `ExcludeView` sur les éléments CustomVisualizer.
