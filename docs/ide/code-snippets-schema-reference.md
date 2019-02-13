---
title: Référence de schéma des extraits de code
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 203236c454b2047872bc9f71242e4992a1c1294f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929633"
---
# <a name="code-snippets-schema-reference"></a>Référence de schéma des extraits de code

Les extraits de code IntelliSense sont des bouts de code précréés et prêts à être insérés dans votre application avec Visual Studio. Vous pouvez augmenter la productivité en fournissant des extraits de code qui réduisent le nombre d'heures passées à taper un code répétitif ou à rechercher des exemples. Vous pouvez utiliser le schéma XML des extraits de code IntelliSense pour créer vos propres extraits de code et les ajouter aux extraits de code que Visual Studio contient déjà.

## <a name="assembly-element"></a>Assembly, élément

Spécifie le nom de l'assembly référencé par l'extrait de code.

La valeur du texte de l’élément **Assembly** correspond soit au nom convivial de l’assembly, comme `System.dll`, soit à son nom fort, comme `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Élément parent|Description|
| - |-----------------|
|[Reference, élément](../ide/code-snippets-schema-reference.md#reference-element)|Contient des informations à propos des références d'assembly requises par l'extrait de code.|

 Une valeur texte est requise. Ce texte spécifie l'assembly auquel l'extrait de code fait référence.

## <a name="author-element"></a>Author, élément

Spécifie le nom de l'auteur de l'extrait de code. Le **Gestionnaire des extraits de code** affiche le nom stocké dans l’élément `Author` de l’extrait de code.

```xml
<Author>
   Code Snippet Author
</Author>
```

|Élément parent|Description|
| - |-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header-element)|Contient des informations générales sur l'extrait de code.|

 Une valeur texte est requise. Ce texte spécifie l'auteur de l'extrait de code.

## <a name="code-element"></a>Élément de code

Fournit de petits blocs d'extraits de code à un conteneur.

### <a name="keywords"></a>Mots clés

Deux mots réservés peuvent être utilisés dans le texte de l'élément `Code` : `$end$` et `$selected$`. `$end$` marque l'emplacement pour placer le curseur après insertion de l'extrait de code. `$selected$` représente le texte sélectionné dans le document qui sera inséré dans l'extrait de code lorsqu'il est appelé. Par exemple, étant donné un extrait de code qui inclut :

```
$selected$ is a great color.
```

et que le mot « Blue » est sélectionné lorsque l'utilisateur appelle le modèle, le résultat est le suivant :

```
Blue is a great color.
```

Vous ne pouvez pas utiliser `$end$` ou `$selected$` plus d'une fois dans un extrait de code. Si vous le faites, seule la deuxième instance est reconnue. Étant donné un extrait de code qui inclut :

```
$selected$ is a great color. I love $selected$.
```

si le mot « Blue » est sélectionné, le résultat est le suivant :

```
 is a great color. I love Blue.
```

L'espace initial s'affiche car il y a un espace entre `$selected$` et `is`.

Tous les autres mots clés `$` sont définis dynamiquement dans les balises `<Literal>` et `<Object>`.

Voici la structure de l’élément Code :

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

Une valeur texte est requise. Ce texte spécifie le code, avec les littéraux et les objets, que vous pouvez utiliser quand cet extrait de code est inséré dans un fichier de code.

### <a name="attributes"></a>Attributs

Trois attributs sont disponibles pour l’élément Code :

- **Langage** - Attribut _obligatoire_ qui spécifie le langage de l’extrait de code. Il peut avoir l’une des valeurs suivantes :

   |Value|Description|
   |-----|-----------|
   |`VB`|Identifie un extrait de code Visual Basic.|
   |`CSharp`|Identifie un extrait de code C#.|
   |`CPP`|Identifie un extrait de code C++.|
   |`XML`|Identifie un extrait de code XML.|
   |`JavaScript`|Identifie un extrait de code JavaScript.|
   |`SQL`|Identifie un extrait de code SQL.|
   |`HTML`|Identifie un extrait de code HTML.|

- **Kind** - Attribut _facultatif_ qui spécifie le type de code contenu dans l’extrait de code, ainsi que l’emplacement auquel un extrait de code doit être inséré pour pouvoir être compilé. Il peut avoir l’une des valeurs suivantes :

   |Value|Description|
   |-----|-----------|
   |`method body`|Spécifie que l'extrait de code est un corps de méthode, et par conséquent, qu'il doit être inséré à l'intérieur d'une déclaration de méthode.|
   |`method decl`|Spécifie que l'extrait de code est une méthode, et par conséquent, qu'il doit être inséré à l'intérieur d'une classe ou d'un module.|
   |`type decl`|Spécifie que l'extrait de code est un type, et par conséquent, qu'il doit être inséré à l'intérieur d'une classe, d'un module ou d'un espace de noms.|
   |`file`|Spécifie que l'extrait de code est un fichier de code complet. Ces extraits de code peuvent être insérés seuls dans un fichier de code, ou à l'intérieur d'un espace de noms.|
   |`any`|Spécifie que l'extrait de code peut être inséré n'importe où. Cette balise est utilisée pour les extraits de code indépendants du contexte, comme les commentaires.|

- **Delimiter** - Attribut _facultatif_ qui spécifie le délimiteur utilisé pour décrire les littéraux et les objets contenus dans le code. Par défaut, le délimiteur est `$`.

### <a name="parent-element"></a>Élément parent

|Élément parent|Description|
| - |-----------------|
|[Snippet, élément](../ide/code-snippets-schema-reference.md#snippet-element)|Contient les références, importations, déclarations et code de l'extrait de code.|

## <a name="codesnippet-element"></a>CodeSnippet, élément

Vous permet de spécifier un titre et plusieurs extraits de code IntelliSense que vous pouvez insérer dans des fichiers de Visual Studio Code.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>
```

|Attribut|Description|
|---------------|-----------------|
|`Format`|Attribut requis. Spécifie la version de schéma de l'extrait de code. L'attribut Format doit être une chaîne dont la syntaxe est x.x.x, où chaque "x" représente une valeur numérique du numéro de version. Visual Studio ignore les extraits de code dont il ne comprend pas les attributs `Format`.|

|Élément enfant|Description|
|-------------------|-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header-element)|Élément requis. Contient des informations générales sur l'extrait de code. Il doit y avoir un seul élément `Header` dans un extrait de code.|
|[Snippet, élément](../ide/code-snippets-schema-reference.md#snippet-element)|Élément requis. Contient le code qui sera inséré par Visual Studio. Il doit y avoir un seul élément `Snippet` dans un extrait de code.|

|Élément parent|Description|
| - |-----------------|
|[CodeSnippets, élément](../ide/code-snippets-schema-reference.md#codesnippets-element)|Élément racine du schéma XML de l'extrait de code.|

## <a name="codesnippets-element"></a>CodeSnippets, élément

Regroupe des éléments [CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet-element). L'élément `CodeSnippets` est l'élément racine du schéma XML de l'extrait de code.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[CodeSnippet, élément](../ide/code-snippets-schema-reference.md#codesnippet-element)|Élément facultatif. Élément parent pour toutes les données d'extrait de code. Un élément `CodeSnippet` peut ne contenir aucun élément `CodeSnippets` ou en contenir plusieurs.|

## <a name="declarations-element"></a>Declarations, élément

Spécifie les littéraux et les objets qui composent un extrait de code que vous pouvez modifier.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Literal, élément](../ide/code-snippets-schema-reference.md#literal-element)|Élément facultatif. Définit les littéraux de l'extrait de code que vous pouvez modifier. Un élément `Literal` peut ne contenir aucun élément `Declarations` ou en contenir plusieurs.|
|[Object, élément](../ide/code-snippets-schema-reference.md#object-element)|Élément facultatif. Définit les objets de l'extrait de code que vous pouvez modifier. Un élément `Object` peut ne contenir aucun élément `Declarations` ou en contenir plusieurs.|

|Élément parent|Description|
| - |-----------------|
|[Snippet, élément](../ide/code-snippets-schema-reference.md#snippet-element)|Contient les références, importations, déclarations et code de l'extrait de code.|

## <a name="default-element"></a>Default, élément

Spécifie la valeur par défaut du littéral ou de l'objet d'un extrait de code IntelliSense.

```xml
<Default>
    Default value
</Default>
```

|Élément parent|Description|
| - |-----------------|
|[Literal, élément](../ide/code-snippets-schema-reference.md#literal-element)|Définit les champs littéraux de l'extrait de code que vous pouvez modifier.|
|[Object, élément](../ide/code-snippets-schema-reference.md#object-element)|Définit les champs objet de l'extrait de code que vous pouvez modifier.|

 Une valeur texte est requise. Ce texte spécifie la valeur par défaut du littéral ou de l'objet qui remplit les champs de l'extrait de code que vous pouvez modifier.

## <a name="description-element"></a>Description, élément

Spécifie des informations relatives à la description du contenu d'un extrait de code IntelliSense.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Élément parent|Description|
| - |-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header-element)|Contient des informations générales sur l'extrait de code.|

 Une valeur texte est requise. Ce texte décrit l'extrait de code.

## <a name="function-element"></a>Function, élément

Spécifie une fonction à exécuter lorsque le littéral ou l'objet reçoit le focus dans Visual Studio.

> [!NOTE]
> L'élément `Function` est uniquement pris en charge par les extraits de code C#.

```xml
<Function>
    FunctionName
</Function>
```

|Élément parent|Description|
| - |-----------------|
|[Literal, élément](../ide/code-snippets-schema-reference.md#literal-element)|Définit les champs littéraux de l'extrait de code que vous pouvez modifier.|
|[Object, élément](../ide/code-snippets-schema-reference.md#object-element)|Définit les champs objet de l'extrait de code que vous pouvez modifier.|

 Une valeur texte est requise. Ce texte spécifie une fonction à exécuter lorsque le littéral ou le champ objet reçoit le focus dans Visual Studio.

## <a name="header-element"></a>Header, élément

Spécifie des informations d'ordre général sur l'extrait de code IntelliSense.

```xml
<Header>
    <Title>... </Title>
    <Author>... </Author>
    <Description>... </Description>
    <HelpUrl>... </HelpUrl>
    <SnippetTypes>... </SnippetTypes>
    <Keywords>... </Keywords>
    <Shortcut>... </Shortcut>
</Header>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Author, élément](../ide/code-snippets-schema-reference.md#author-element)|Élément facultatif. Nom de la personne ou de la société qui a créé l'extrait de code. Il peut y avoir zéro ou un élément `Author` dans un élément `Header`.|
|[Description, élément](../ide/code-snippets-schema-reference.md#description-element)|Élément facultatif. Description de l'extrait de code. Il peut y avoir zéro ou un élément `Description` dans un élément `Header`.|
|[HelpUrl, élément](../ide/code-snippets-schema-reference.md#helpurl-element)|Élément facultatif. URL contenant plus d'informations sur l'extrait de code. Il peut y avoir zéro ou un élément `HelpURL` dans un élément . **Remarque :**  Visual Studio n'utilise pas l'élément `HelpUrl`. L'élément fait partie du schéma XML des extraits de code IntelliSense et tout extrait de code contenant l'élément est validé mais la valeur de l'élément n'est jamais utilisée.|
|[Keywords, élément](../ide/code-snippets-schema-reference.md#keywords-element)|Élément facultatif. Groupe les éléments `Keyword`. Il peut y avoir zéro ou un élément `Keywords` dans un élément `Header`.|
|[Shortcut, élément](../ide/code-snippets-schema-reference.md#shortcut-element)|Élément facultatif. Spécifie le texte du raccourci qui peut être utilisé pour insérer l'extrait de code. Il peut y avoir zéro ou un élément `Shortcut` dans un élément `Header`.|
|[SnippetTypes, élément](../ide/code-snippets-schema-reference.md#snippettypes-element)|Élément facultatif. Groupe les éléments `SnippetType`. Il peut y avoir zéro ou un élément `SnippetTypes` dans un élément `Header`. S'il n'y a pas d'éléments `SnippetTypes`, l'extrait de code est toujours valide.|
|[Title, élément](../ide/code-snippets-schema-reference.md#title-element)|Élément requis. Nom convivial de l'extrait de code. Un élément `Title` doit contenir exactement un élément `Header`.|

|Élément parent|Description|
| - |-----------------|
|[CodeSnippet, élément](../ide/code-snippets-schema-reference.md#codesnippet-element)|Élément parent pour toutes les données d'extrait de code.|

## <a name="helpurl-element"></a>HelpUrl, élément

Spécifie une URL qui fournit des informations supplémentaires sur un extrait de code.

> [!NOTE]
> Visual Studio n'utilise pas l'élément `HelpUrl`. L'élément fait partie du schéma XML des extraits de code IntelliSense et tout extrait de code contenant l'élément est validé mais la valeur de l'élément n'est jamais utilisée.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>
```

|Élément parent|Description|
| - |-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header-element)|Contient des informations générales sur l'extrait de code.|

Une valeur texte est facultative. Ce texte spécifie l'URL à visiter pour plus d'informations sur un extrait de code.

## <a name="id-element"></a>ID, élément

Spécifie l'identificateur unique d'un élément `Literal` ou `Object`. Deux littéraux ou deux objets du même extrait de code ne peuvent pas avoir la même valeur texte dans leurs éléments `ID`. Les littéraux et les objets ne peuvent pas contenir d’élément `ID` avec la valeur « end ». La valeur `$end$` est réservée et utilisée pour marquer l'emplacement du curseur après que l'extrait de code a été inséré.

```xml
<ID>
    Unique Identifier
</ID>
```

|Élément parent|Description|
| - |-----------------|
|[Literal, élément](../ide/code-snippets-schema-reference.md#literal-element)|Définit les champs littéraux de l'extrait de code que vous pouvez modifier.|
|[Object, élément](../ide/code-snippets-schema-reference.md#object-element)|Définit les champs objet de l'extrait de code que vous pouvez modifier.|

Une valeur texte est requise. Ce texte spécifie l'identificateur unique de l'objet ou du littéral.

## <a name="import-element"></a>Import, élément

Spécifie les espaces de noms importés et utilisés par un extrait de code IntelliSense.

> [!NOTE]
> L'élément `Import` est uniquement pris en charge pour les projets Visual Basic.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Namespace, élément](../ide/code-snippets-schema-reference.md#namespace-element)|Élément requis. Spécifie l'espace de noms utilisé par l'extrait de code. Un élément `Namespace` doit contenir exactement un élément `Import`.|

|Élément parent|Description|
| - |-----------------|
|[Imports, élément](../ide/code-snippets-schema-reference.md#imports-element)|Élément grouping pour les éléments **Import**.|

## <a name="imports-element"></a>Imports, élément

Groupe des éléments `Import` individuels.

> [!NOTE]
> L'élément `Imports` est uniquement pris en charge pour les projets Visual Basic.

```xml
<Imports>
    <Import>... </Import>
</Imports>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Import, élément](../ide/code-snippets-schema-reference.md#import-element)|Élément facultatif. Contient les espaces de noms importés pour l'extrait de code. Un élément **Import** peut ne contenir aucun élément `Imports` ou en contenir plusieurs.|

|Élément parent|Description|
| - |-----------------|
|[Snippet, élément](../ide/code-snippets-schema-reference.md#snippet-element)|Contient les références, importations, déclarations et code de l'extrait de code.|

## <a name="keyword-element"></a>Keyword, élément

Spécifie un mot clé personnalisé pour l'extrait de code. Les mots clés d'extrait de code sont utilisés par Visual Studio et représentent une manière standard pour les fournisseurs de contenu en ligne d'ajouter des mots clés personnalisés pour les recherches ou la catégorisation.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Élément parent|Description|
| - |-----------------|
|[Keywords, élément](../ide/code-snippets-schema-reference.md#keywords-element)|Groupe des éléments `Keyword` individuels.|

Une valeur texte est requise. Mot clé pour l'extrait de code.

## <a name="keywords-element"></a>Keywords, élément

Groupe des éléments `Keyword` individuels. Les mots clés d'extrait de code sont utilisés par Visual Studio et représentent une manière standard pour les fournisseurs de contenu en ligne d'ajouter des mots clés personnalisés pour les recherches ou la catégorisation.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
</Keywords>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Keyword, élément](../ide/code-snippets-schema-reference.md#keyword-element)|Élément facultatif. Contient les mots clés de l'extrait de code. Un élément `Keyword` peut ne contenir aucun élément `Keywords` ou en contenir plusieurs.|

|Élément parent|Description|
| - |-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header-element)|Contient des informations générales sur l'extrait de code.|

## <a name="literal-element"></a>Literal, élément

Définit les littéraux de l'extrait de code que vous pouvez modifier. L'élément `Literal` est utilisé pour identifier le remplacement d'une partie de code entièrement contenue dans l'extrait de code, mais qui sera probablement personnalisée après avoir été insérée dans le code. Par exemple, les chaînes littérales, les valeurs numériques et certains noms de variables doivent être déclarés comme des littéraux.

Les littéraux et les objets ne peuvent pas contenir d’élément **ID** avec la valeur selected ou end. La valeur `$selected$` représente le texte sélectionné dans le document qui sera inséré dans l'extrait de code lorsqu'il est appelé. `$end$` marque l'emplacement pour placer le curseur après insertion de l'extrait de code.

```xml
<Literal Editable="true/false">
   <ID>... </ID>
   <ToolTip>... </ToolTip>
   <Default>... </Default>
   <Function>... </Function>
</Literal>
```

|Attribut|Description|
|---------------|-----------------|
|`Editable`|Attribut `Boolean` facultatif. Spécifie si vous pouvez modifier ou non le littéral une fois l'extrait de code inséré. La valeur par défaut de cet attribut est `true`.|

|Élément enfant|Description|
|-------------------|-----------------|
|[Default, élément](../ide/code-snippets-schema-reference.md#default-element)|Élément requis. Spécifie la valeur par défaut du littéral lorsque vous insérez l'extrait de code. Un élément `Default` doit contenir exactement un élément `Literal`.|
|[Function, élément](../ide/code-snippets-schema-reference.md#function-element)|Élément facultatif. Spécifie une fonction à exécuter lorsque le littéral reçoit le focus dans Visual Studio. Il peut y avoir zéro ou un élément `Function` dans un élément `Literal`.|
|[ID, élément](../ide/code-snippets-schema-reference.md#id-element)|Élément requis. Spécifie l'identificateur unique du littéral. Un élément `ID` doit contenir exactement un élément `Literal`.|
|[ToolTip, élément](../ide/code-snippets-schema-reference.md#tooltip-element)|Élément facultatif. Décrit la valeur attendue et l'utilisation du littéral. Un élément **peut contenir zéro ou un élément**Tooltip`Literal`.|

|Élément parent|Description|
| - |-----------------|
|[Declarations, élément](../ide/code-snippets-schema-reference.md#declarations-element)|Contient les littéraux et les objets d'un extrait de code que vous pouvez modifier.|

## <a name="namespace-element"></a>Namespace, élément

Spécifie l'espace de noms qui doit être importé pour compiler l'extrait de code et l'exécuter. L'espace de noms spécifié dans l'élément `Namespace` est ajouté automatiquement au début du code à une instruction `Imports`, s'il n'y figure pas déjà.

> [!NOTE]
> L'élément `Namespace` est uniquement pris en charge pour les projets Visual Basic.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Élément parent|Description|
| - |-----------------|
|[Import, élément](../ide/code-snippets-schema-reference.md#import-element)|Importe l'espace de noms spécifié.|

Une valeur texte est requise. Ce texte spécifie un espace de noms que l'extrait de code considère comme importé.

## <a name="object-element"></a>Object, élément

Définit les objets de l'extrait de code que vous pouvez modifier. L'élément `Object` est utilisé pour identifier un élément qui est requis par l'extrait de code, mais qui est vraisemblablement en dehors de l'extrait de code lui-même. Par exemple, les contrôles Windows Forms, les contrôles ASP.NET, les instances d'objet et les instances de type doivent être déclarées comme objets. Les déclarations d'objet requièrent qu'un type soit spécifié, ce qui est fait avec l'élément `Type`.

```xml
<Object Editable="true/false">
    <ID>... </ID>
    <Type>... </Type>
    <ToolTip>... </ToolTip>
    <Default>... </Default>
    <Function>... </Function>
</Object>
```

|Attribut|Description|
|---------------|-----------------|
|`Editable`|Attribut `Boolean` facultatif. Spécifie si vous pouvez modifier ou non le littéral une fois l'extrait de code inséré. La valeur par défaut de cet attribut est `true`.|

|Élément enfant|Description|
|-------------------|-----------------|
|[Default, élément](../ide/code-snippets-schema-reference.md#default-element)|Élément requis. Spécifie la valeur par défaut du littéral lorsque vous insérez l'extrait de code. Un élément `Default` doit contenir exactement un élément `Literal`.|
|[Function, élément](../ide/code-snippets-schema-reference.md#function-element)|Élément facultatif. Spécifie une fonction à exécuter lorsque le littéral reçoit le focus dans Visual Studio. Il peut y avoir zéro ou un élément `Function` dans un élément `Literal`.|
|[ID, élément](../ide/code-snippets-schema-reference.md#id-element)|Élément requis. Spécifie l'identificateur unique du littéral. Un élément `ID` doit contenir exactement un élément `Literal`.|
|[ToolTip, élément](../ide/code-snippets-schema-reference.md#tooltip-element)|Élément facultatif. Décrit la valeur attendue et l'utilisation du littéral. Un élément **peut contenir zéro ou un élément**Tooltip`Literal`.|
|[Type, élément](../ide/code-snippets-schema-reference.md#type-element)|Élément requis. Spécifie le type de l'objet. Un élément `Type` doit contenir exactement un élément `Object`.|

|Élément parent|Description|
| - |-----------------|
|[Declarations, élément](../ide/code-snippets-schema-reference.md#declarations-element)|Contient les littéraux et les objets d'un extrait de code que vous pouvez modifier.|

## <a name="reference-element"></a>Reference, élément

Spécifie des informations sur les références d'assembly requises par l'extrait de code.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Assembly, élément](../ide/code-snippets-schema-reference.md#assembly-element)|Élément requis. Spécifie le nom de l'assembly référencé par l'extrait de code. Un élément `Assembly` doit contenir exactement un élément `Reference`.|
|[Url, élément](../ide/code-snippets-schema-reference.md#url-element)|Élément facultatif. Contient une URL qui fournit plus d'informations sur l'assembly référencé. Il peut y avoir zéro ou un élément `Url` dans un élément `Reference`.|

|Élément parent|Description|
| - |-----------------|
|[References, élément](../ide/code-snippets-schema-reference.md#references-element)|Élément de regroupement pour les éléments `Reference`.|

## <a name="references-element"></a>References, élément

Groupe des éléments `Reference` individuels.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Reference, élément](../ide/code-snippets-schema-reference.md#reference-element)|Élément facultatif. Contient des informations à propos des références d'assembly de l'extrait de code. Un élément `Reference` peut ne contenir aucun élément `References` ou en contenir plusieurs.|

|Élément parent|Description|
| - |-----------------|
|[Snippet, élément](../ide/code-snippets-schema-reference.md#snippet-element)|Contient les références, importations, déclarations et code de l'extrait de code.|

## <a name="shortcut-element"></a>Shortcut, élément

Spécifie le texte de raccourci utilisé pour insérer l'extrait de code. La valeur texte d'un élément `Shortcut` peut contenir uniquement des signes alphanumériques, des traits d'union (-) et des traits de soulignement (_).

> [!CAUTION]
> _ et - ne sont pas des caractères pris en charge dans les raccourcis de l’extrait de code C++.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Élément parent|Description|
| - |-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header-element)|Contient des informations générales sur l'extrait de code.|

 Une valeur texte est facultative. Ce texte est utilisé comme raccourci pour insérer l'extrait de code.

## <a name="snippet-element"></a>Snippet, élément

Spécifie les références, les importations, les déclarations et le code de l'extrait de code.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Code, élément](../ide/code-snippets-schema-reference.md#code-element)|Élément requis. Spécifie le code que vous souhaitez insérer dans un fichier documentation. Un élément `Code` doit contenir exactement un élément `Snippet`.|
|[Declarations, élément](../ide/code-snippets-schema-reference.md#declarations-element)|Élément facultatif. Spécifie les littéraux et les objets qui composent un extrait de code que vous pouvez modifier. Il peut y avoir zéro ou un élément `Declarations` dans un élément `Snippet`.|
|[Imports, élément](../ide/code-snippets-schema-reference.md#imports-element)|Élément facultatif. Groupe des éléments `Import` individuels. Il peut y avoir zéro ou un élément `Imports` dans un élément `Snippet`.|
|[References, élément](../ide/code-snippets-schema-reference.md#references-element)|Élément facultatif. Groupe des éléments `Reference` individuels. Il peut y avoir zéro ou un élément `References` dans un élément `Snippet`.|

|Élément parent|Description|
| - |-----------------|
|[CodeSnippet, élément](../ide/code-snippets-schema-reference.md#codesnippet-element)|Vous permet de spécifier un titre et plusieurs extraits de code IntelliSense que vous pouvez insérer dans des fichiers de Visual Studio Code.|

## <a name="snippettype-element"></a>SnippetType, élément

Spécifie la manière dont Visual Studio insère l'extrait de code.

```xml
<SnippetType>
    SurroundsWith/Expansion
</SnippetType>
```

|Élément parent|Description|
| - |-----------------|
|[SnippetTypes, élément](../ide/code-snippets-schema-reference.md#snippettypes-element)|Groupe les éléments `SnippetType`.|

Le texte doit avoir l'une des valeurs suivantes :

-   `SurroundsWith` : autorise à placer l'extrait de code autour d'une partie de code sélectionnée.

-   `Expansion` : autorise à insérer l'extrait de code au curseur.

-   `Refactoring` : spécifie que l'extrait de code est utilisé pendant la refactorisation C#. `Refactoring` ne peut pas être utilisé dans les extraits de code personnalisés.

## <a name="snippettypes-element"></a>SnippetTypes, élément

Groupe des éléments `SnippetType` individuels. Si l'élément `SnippetTypes` est absent, l'extrait de code peut être inséré n'importe où dans le code.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
</SnippetTypes>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[SnippetType, élément](../ide/code-snippets-schema-reference.md#snippettype-element)|Élément facultatif. Spécifie la manière dont Visual Studio insère l'extrait de code dans le code. Un élément `SnippetType` peut ne contenir aucun élément `SnippetTypes` ou en contenir plusieurs.|

|Élément parent|Description|
| - |-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header-element)|Spécifie des informations générales sur l'extrait de code.|

## <a name="title-element"></a>Title, élément

Spécifie le titre de l'extrait de code. Le titre stocké dans l’élément `Title` de l’extrait de code apparaît dans le **Sélecteur d’extraits de code**, ainsi que dans la description de l’extrait de code située dans le **Gestionnaire des extraits de code**.

```xml
<Title>
    Code Snippet Title
</Title>
```

|Élément parent|Description|
| - |-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header-element)|Spécifie des informations générales sur l'extrait de code.|

 Une valeur texte est requise. Ce texte spécifie le titre de l'extrait de code.

## <a name="tooltip-element"></a>ToolTip, élément

Décrit la valeur attendue et l'utilisation d'un littéral ou d'un objet d'extrait de code que Visual Studio affiche dans une info-bulle lorsqu'il insère l'extrait de code dans un projet. Le texte d'Info-bulle est affiché lorsque la souris pointe sur le littéral ou sur l'objet après que l'extrait de code a été inséré.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Élément parent|Description|
| - |-----------------|
|[Literal, élément](../ide/code-snippets-schema-reference.md#literal-element)|Définit les champs littéraux de l'extrait de code que vous pouvez modifier.|
|[Object, élément](../ide/code-snippets-schema-reference.md#object-element)|Définit les champs objet de l'extrait de code que vous pouvez modifier.|

 Une valeur texte est requise. Ce texte spécifie la description de l'info-bulle à associer à l'objet ou au littéral dans l'extrait de code.

## <a name="type-element"></a>Élément Type

Spécifie le type de l'objet. L'élément `Object` est utilisé pour identifier un élément qui est requis par l'extrait de code, mais qui est vraisemblablement en dehors de l'extrait de code lui-même. Par exemple, les contrôles Windows Forms, les contrôles ASP.NET, les instances d'objet et les instances de type doivent être déclarées comme objets. Les déclarations d'objet requièrent qu'un type soit spécifié, ce qui est fait avec l'élément `Type`.

```xml
<Type>
    Type
</Type>
```

|Élément parent|Description|
| - |-----------------|
|[Object, élément](../ide/code-snippets-schema-reference.md#object-element)|Définit les champs objet de l'extrait de code que vous pouvez modifier.|

 Une valeur texte est requise. Ce texte spécifie le type de l'objet.

## <a name="url-element"></a>Url, élément

Spécifie une URL qui fournit des informations supplémentaires sur l'assembly référencé.

> [!NOTE]
> L'élément `Url` est uniquement pris en charge pour les projets Visual Basic.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Élément parent|Description|
| - |-----------------|
|[Reference, élément](../ide/code-snippets-schema-reference.md#reference-element)|Spécifie les références d'assembly requises par l'extrait de code.|

Une valeur texte est requise. Ce texte spécifie une URL avec plus d'informations sur l'assembly référencé. Cette URL est affichée lorsque la référence ne peut pas être ajoutée au projet.

## <a name="see-also"></a>Voir aussi

- [Extraits de code](../ide/code-snippets.md)
- [Procédure pas à pas : Créer un extrait de code](../ide/walkthrough-creating-a-code-snippet.md)
