---
title: "Paramètres des conventions de codage .NET pour EditorConfig | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 1
author: kaseyu
ms.author: kaseyu
manager: davidcsa
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 3037d92e9de377ab4b306a5a0e164e29fa6659e7
ms.openlocfilehash: 600cd62e7843274b52da5ac7200b5168311cab07
ms.contentlocale: fr-fr
ms.lasthandoff: 08/07/2017

---

# <a name="net-coding-convention-settings-for-editorconfig"></a>Paramètres des conventions de codage .NET pour EditorConfig
Les conventions de codage .NET sont configurées avec un fichier [EditorConfig](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options). Grâce aux fichiers EditorConfig, vous pouvez **activer/désactiver des conventions de codage .NET spécifiques** et **configurer le degré d’application de la convention** (au moyen d’un niveau de gravité). Pour en savoir plus sur l’utilisation d’EditorConfig pour appliquer la cohérence sur votre base de code, lisez [cet article](https://docs.microsoft.com/en-us/visualstudio/ide/create-portable-custom-editor-options).

Trois catégories de conventions de codage .NET sont prises en charge :
- Les **[conventions de langage](#language)** sont des règles relatives au langage C# ou Visual Basic, par exemple, `var`/type explicite ou utilisation de membres expression-bodied.
- Les **[règles de mise en forme](#formatting)** sont les règles qui régissent la disposition et la structure de votre code pour en faciliter la lecture, par exemple, au moyen d’accolades Allman ou d’espaces dans les blocs de contrôle.
- Les **[conventions de nommage](#naming)** sont les règles qui régissent la façon dont les objets sont nommés ; par exemple, les méthodes `async` doivent se terminer par « Async ». 

# <a name="language">Conventions de langage</a>
## <a name="overview"></a>Vue d'ensemble
**Format de la règle :**
`options_name = false|true : none|suggestion|warning|error`

Pour l’option de style de code, vous devez spécifier **true** (préférez cette option) ou **false** (option déconseillée), un signe deux-points (`:`) et un niveau de gravité (`none`, `silent`, `suggestion`, `warning` ou `error`). La gravité correspond au niveau d’application de ce style souhaité dans votre base de code.

`none` et `silent` sont synonymes et signifient qu’aucun genre d’indication ne doit être affiché à l’utilisateur. Cela a pour effet de désactiver cette règle.

Gravité | effet
------------ | -------------
none/silent | Ne rien afficher à l’utilisateur quand ce style n’est pas suivi, quelle que soit la manière dont les fonctionnalités de génération de code seront générées dans ce style. 
suggestion | Quand ce style n’est pas suivi, l’afficher à l’utilisateur comme suggestion (points de soulignement sur les deux premiers caractères).
avertissement | Quand ce style n’est pas suivi, afficher un avertissement du compilateur.
erreur | Quand ce style n’est pas suivi, afficher une erreur du compilateur.

## <a name="net-language-convention-options"></a>Options de convention de langage .NET

- **[Paramètres de style de code .NET](#this_and_me)**
    - [« This. » et « Me. » Qualification](#this_and_me)
        - [Champs](#this_and_me_fields)
        - [Propriétés](#this_and_me_properties)
        - [Méthodes](#this_and_me_methods)
        - [Événements](#this_and_me_events)
    - [Mots clés de langage (int, string, etc.) vs type de framework pour les références de type](#language_keywords)
        - [Variables locales, paramètres et membres](#language_keywords_variables)
        - [Expressions d’accès de membre](#language_keywords_member_access)
    - [Préférences au niveau de l’expression](#expression_level)
        - [Initialiseurs d’objets](#expression_level_object_initializers)
        - [Initialiseurs de collection](#expression_level_collection_initializers)
        - [Noms de tuples explicites](#expression_level_tuple_names)
        - [Expressions de fusion lors de la vérification « null »](#expression_level_null_checking)
        - [Propagation de NULL lors de la vérification « null »](#expression_level_null_propogation)
- **[Paramètres de style de code CSharp](#csharp_codestyle)**
    - [« var »](#var)
        - [« var » pour les types intégrés](#var_built_in)
        - [« var » quand le type est visible](#var_apparent)
        - [« var » ailleurs](#var_elsewhere)
    - [Membres expression-bodied](#expression_body)
        - [Méthodes](#expression_bodied_members_methods)
        - [Constructeurs](#expression_bodied_members_constructors)
        - [Opérateurs](#expression_bodied_members_operators)
        - [Propriétés](#expression_bodied_members_properties)
        - [Indexeurs](#expression_bodied_members_indexers)
        - [Accesseurs](#expression_bodied_members_accessors)
    - [Critères spéciaux](#pattern_matching)
        - [« is » avec vérification « cast »](#pattern_matching_is_cast)
        - [« as » avec vérification « null »](#pattern_matching_as_null)
    - [Déclarations de variables inline](#inlined_variable_declarations)
    - [Préférences au niveau de l’expression](#expression_level_csharp) -[Simplifier les expressions `default`](#expression_level_default)
    - [Préférences de vérification « null »](#null_checking)
        - [Expressions-throw](#null_checking_throw_expressions)
        - [Appels de délégué conditionnels](#null_checking_conditional_delegate_calls)

## <a name="this_and_me">« This. » et « Me. » Qualification</a>
### <a name="this_and_me_fields">Champs (IDE0003/IDE0009)</a>
|  Nom de l’option | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Dans l’idéal, faire précéder tous les champs non statiques utilisés dans les méthodes non statiques par `this.` en C# ou `Me.` en Visual Basic. | **C# :** <br>`this.capacity = 0;` <br><br> **Visual Basic :** <br> `Me.capacity = 0`
| False | Dans l’idéal, ne pas faire précéder les champs non statiques utilisés dans les méthodes non statiques par `this.` en C# ou `Me.` en Visual Basic. | **C# :** <br>`capacity = 0;` <br><br> **Visual Basic :** <br>`capacity = 0`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">Propriétés (IDE0003/IDE0009) </a>

|  Nom de l’option | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Dans l’idéal, faire précéder toutes les propriétés non statiques utilisées dans les méthodes non statiques par `this.` en C# ou `Me.` en Visual Basic.| **C# :** <br>`this.ID = 0;` <br><br> **Visual Basic :** <br>`Me.ID = 0`
| False | Dans l’idéal, ne *pas* faire précéder les propriétés non statiques utilisées dans les méthodes non statiques par `this.` en C# ou `Me.` en Visual Basic. | **C# :** <br>`ID = 0;` <br><br> **Visual Basic :** <br> `ID = 0`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```

### <a name="this_and_me_methods">Méthodes (IDE0003/IDE0009) </a>
|  Nom de l’option | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Dans l’idéal, faire précéder toutes les méthodes non statiques appelées à partir de méthodes non statiques par `this.` en C# ou `Me.` en VB.| **C# :** <br>`this.Display();` <br><br> **Visual Basic :** <br> `Me.Display()`
| False | Dans l’idéal, ne *pas* faire précéder toutes les méthodes non statiques appelées à partir de méthodes non statiques par `this.` en C# ou `Me.` en VB. | **C# :** <br>`Display();` <br><br> **Visual Basic :** <br> `Display()`


#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">Événements (IDE0003/IDE0009) </a>
|  Nom de l’option | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Dans l’idéal, faire précéder tous les événements non statiques référencés à partir de méthodes non statiques par `this.` en C# ou `Me.` en VB.| **C# :** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic :** <br> `AddHandler Me.Elapsed, AddressOf Handler`
| False | Dans l’idéal, ne *pa*s faire précéder tous les événements non statiques référencés à partir de méthodes non statiques par `this.` en C# ou `Me.` en VB. | **C# :** <br>`Elapsed += Handler;` <br><br> **Visual Basic :** <br>`AddHandler Elapsed, AddressOf Handler`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Mots clés de langage (int, string, etc.) vs type de framework pour les références de type </a>
### <a name="language_keywords_variables"> Variables locales, paramètres et membres (IDE0012/IDE0014)</a>
|  Nom de l’option | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Pour les variables locales, les paramètres et les membres de type, faire en sorte que les types qui ont un mot clé de langage pour les représenter (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) utilisent le mot clé au lieu du nom de type (`Int32`, `Int64`, etc.).| **C# :** <br>`private int _member;` <br><br> **Visual Basic :** `Private _member As Integer`
| False | Pour les variables locales, les paramètres et les membres de type, faire en sorte que les types qui ont un mot clé de langage pour les représenter (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) utilisent le nom de type (`Int32`, `Int64`, etc.) au lieu du mot clé.  | **C# :** <br>`private Int32 _member;` <br><br> **Visual Basic :** <br> `Private _member As Int32`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">Expressions d’accès de membre (IDE0013/IDE0015)</a>
|  Nom de l’option | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer le mot clé chaque fois qu’une expression d’accès au membre est utilisée sur un type avec une représentation sous forme de mot clé (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`).| **C# :** <br>`var local = int.MaxValue;` <br><br> **Visual Basic :** <br> `Dim local = Integer.MaxValue`
| False | Préférer le nom de type chaque fois qu’une expression d’accès au membre est utilisée sur un type avec une représentation sous forme de mot clé (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`). | **C# :** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic :** <br> `Dim local = Int32.MaxValue`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">Préférences au niveau de l’expression</a>
### <a name="expression_level_object_initializers">Initialiseurs d’objets (IDE0017)</a>
|  Nom de l’option | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’initialisation des objets à l’aide d’initialiseurs d’objets dans la mesure du possible.| **C# :** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic :** <br> `Dim c = New Customer() With { .Age = 21 }`
| False | Faire en sorte que les objets ne soient *pas* initialisés à l’aide d’initialiseurs d’objets. | **C# :** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic :** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">Initialiseurs de collections (IDE0028)</a>
|  Nom de l’option | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’initialisation des collections à l’aide d’initialiseurs de collection dans la mesure du possible.| **C# :** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic :** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | Faire en sorte que les objets ne soient *pas* initialisés à l’aide d’initialiseurs de collection. | **C# :** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic :** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">Noms de tuples explicites (IDE0033)</a>
|  Nom de l’option | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **Langages applicables** | C# 7.0+ et Visual Basic 15+

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les noms de tuple aux propriétés ItemX.| **C# :** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic :** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | Préférer les propriétés ItemX aux noms de tuple. | **C# :** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic :** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">Expressions de fusion lors de la vérification « null » (IDE0029)</a>
|  Nom de l’option | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’expression de fusion null à la vérification d’opérateur ternaire.| **C# :** <br>`var v = x ?? y;` <br><br> **Visual Basic :** <br> `Dim v = If(x, y)`
| False | Préférer la vérification d’opérateur ternaire à l’expression de fusion null. | **C# :** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic :** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">Propagation de NULL lors de la vérification « null » (IDE0031)</a>
|  Nom de l’option | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’utilisation de l’opérateur de condition null dans la mesure du possible.| **C# :** <br>`var v = o?.ToString();` <br><br> **Visual Basic :** <br> `Dim v = o?.ToString()`
| False | Préférer la vérification de la valeur null ternaire dans la mesure du possible. | **C# :** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic :** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">Paramètres de style de code CSharp</a>
## <a name="var">« var » et types explicites</a>
### <a name="var_built_in">« var » pour les types intégrés (IDE0007, IDE0008)</a>
|  Nom de l’option | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’utilisation de `var` pour les types système intégrés tels que `int`.| **C# :** <br>`var x = 5;`
| False | Ne pas utiliser `var` pour les types système intégrés tels que `int`. | **C# :** <br>`int x = 5;`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">« var » quand le type est visible (IDE0007, IDE0008)</a>
|  Nom de l’option | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer `var` quand le type est déjà mentionné dans la partie droite d’une expression de déclaration.| **C# :** <br>`var obj = new C();`
| False | Ne pas utiliser `var` quand le type est déjà mentionné dans la partie droite d’une expression de déclaration. | **C# :** <br>`C obj = new C();`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">« var » ailleurs (IDE0007, IDE0008)</a>
|  Nom de l’option | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer `var` dans tous les cas sauf substitution par une autre règle de style de code.| **C# :** <br>`var f = this.Init();`
| False | Ne pas utiliser var dans tous les cas, sauf substitution par une autre règle de style de code.| **C# :** <br>`bool f = this.Init();`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

##<a name="expression_bodied_members">Membres expression-bodied</a>
### <a name="expression_bodied_members_methods">Méthodes (IDE0022)</a>
|  Nom de l’option | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **Langages applicables** | C# 6.0+

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les méthodes.| **C# :** <br>`public int GetAge() => this.Age;`
| False | Ne pas préférer les membres expression-bodied pour les méthodes.| **C# :** <br>`public int GetAge() { return this.Age; }`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">Constructeurs (IDE0021)</a>
|  Nom de l’option | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **Langages applicables** | C# 6.0+

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les constructeurs.| **C# :** <br>`public Customer(int age) => Age = age;`
| False | Ne pas préférer les membres expression-bodied pour les constructeurs.| **C# :** <br>`public Customer(int age) { Age = age; }`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">Opérateurs (IDE0023, IDE0024)</a>
|  Nom de l’option | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **Langages applicables** | C# 6.0+

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les opérateurs.| **C# :** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | Ne pas préférer les membres expression-bodied pour les opérateurs.| **C# :** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">Propriétés (IDE0025)</a>
|  Nom de l’option | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **Langages applicables** | C# 7.0+

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les propriétés.| **C# :** <br>`public int Age => _age;`
| False | Ne pas préférer les membres expression-bodied pour les propriétés.| **C# :** <br>`public int Age { get { return _age; }}`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="expression_bodied_members_indexers">Indexeurs (IDE0026)</a>
|  Nom de l’option | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **Langages applicables** | C# 7.0+

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les indexeurs.| **C# :** <br>`public T this[int i] => _value[i];`
| False | Ne pas préférer les membres expression-bodied pour les indexeurs.| **C# :** <br>`public T this[int i] { get { return _values[i]; } }`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">Accesseurs (IDE0027)</a>
|  Nom de l’option | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **Langages applicables** | C# 7.0+

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les accesseurs.| **C# :** <br>`public int Age { get => _age; set => _age = value; }`
| False | Ne pas préférer les membres expression-bodied pour les accesseurs.| **C# :** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">Critères spéciaux</a>
### <a name="pattern_matching_is_cast">« is » avec vérification « cast » (IDE0020)</a>
|  Nom de l’option | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **Langages applicables** | C# 7.0+

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les critères spéciaux plutôt que les expressions `is` avec des casts de type.| **C# :** <br>`if (o is int i) {...}`
| False | Préférer les expressions `is` avec des casts de type plutôt que les critères spéciaux.| **C# :** <br>`if (o is int) {var i = (int)o; ... }`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">« as » avec vérification « null » (IDE0019)</a>
|  Nom de l’option | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **Langages applicables** | C# 7.0+

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les critères spéciaux plutôt que les expressions `as` avec vérifications « null » pour déterminer si un élément est d’un type particulier.| **C# :** <br>`if (o is string s) {...}`
| False | Préférer les expressions `as` avec vérifications « null » plutôt que les critères spéciaux pour déterminer si un élément est d’un type particulier.| **C# :** <br>`var s = o as string; if (s != null) {...}`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">Déclarations de variables inline (IDE0018)</a>
|  Nom de l’option | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer la déclaration inline des variables `out` dans la mesure du possible. | **C# :** <br>`if (int.TryParse(value, out int i) {...}`
| False | Préférer la déclaration explicite des variables `out`.| **C# :** <br>`int i; if (int.TryParse(value, out i) {...}`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```
## <a name="expression_level_csharp">Préférences au niveau de l’expression</a>
### <a name="expression_level_default">Simplifier les expressions `default` (IDE0034)</a>
|  Nom de l’option | `csharp_prefer_simple_default_expression` |
| ------------- |:-------------:|
| **Langages applicables** | C# 7.1+ et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer `default` à `default(T)` | **C# :** <br>`void DoWork(CancellationToken cancellationToken = default){ ... }`
| False | Préférer. | **C# :** <br>`void DoWork(CancellationToken cancellationToken = default(CancellationToken)){ ... }`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp and VisualBasic code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
``` 

## <a name="null_checking">Préférences de vérification « null »</a>
### <a name="null_checking_throw_expressions">Expressions throw (IDE0016)</a>
|  Nom de l’option | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **Langages applicables** | C# 7.0+

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’utilisation d’expressions throw plutôt que d’instructions throw. | **C# :** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | Préférer l’utilisation d’instructions throw plutôt que d’expressions throw.| **C# :** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">Préférer les appels de délégué conditionnels (IDE0041)</a>
|  Nom de l’option | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’utilisation de l’opérateur de fusion conditionnelle (`?.`) lors de l’appel d’une expression lambda, plutôt que d’effectuer une vérification de valeur null. | **C# :** <br>`func?.Invoke(args);`
| False | Préférer l’exécution d’une vérification de valeur null avant d’appeler une expression lambda, plutôt que d’utiliser l’opérateur de fusion conditionnelle (`?.`).| **C# :** <br>`if (func!=null) { func(args); }`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

# <a name="formatting"> Règles de mise en forme </a>
## <a name="overview"></a>Vue d'ensemble
**Format de la règle :**
`options_name = false|true`

Pour les options de mise en forme, vous devez spécifier **true** (préférez cette option) ou **false** (option déconseillée), sauf dans quelques cas où vous devez spécifier les conditions auxquelles la règle doit s’appliquer.

## <a name="net-formatting-options"></a>Options de mise en forme .NET

- **[Paramètres de mise en forme .NET](#usings)**
    - [Organiser les instructions Using](#usings)
        - [Trier d’abord les directives System](#usings_sort_system_first)
- **[Paramètres de mise en forme C#](#newline)**
    - [Options de saut de ligne](#newline)
        - [Saut de ligne avant l’accolade ouvrante (`{`)](#newline_before_brace)
        - [Saut de ligne avant `else`](#newline_before_else)
        - [Saut de ligne avant `catch`](#newline_before_catch)
        - [Saut de ligne avant `finally`](#newline_before_finally)
        - [Saut de ligne avant les membres dans les initialiseurs d’objet](#newline_before_object)
        - [Saut de ligne avant les membres dans les types anonymes](#newline_before_anonymous)
        - [Saut de ligne avant les membres dans les clauses d’expression de requête](#newline_before_query)
    - [Options de mise en retrait](#indent)
        - [Mettre en retrait le contenu de `switch` case](#indent_switch)
        - [Positionnement des étiquettes](#label)
    - [Options d’espacement](#spacing)
        - [Espace après un cast](#space_after_cast)
        - [Espace après les mots clés dans les instructions de flux de contrôle](#space_control_flow)
        - [Espace entre les parenthèses de la liste des paramètres de déclaration de méthode](#space_parameter_list)
        - [Espace dans les parenthèses de la liste d’arguments d’appel de méthode](#space_method_call)
        - [Espace dans les parenthèses pour les autres options](#space_other)
    - [Options d’inclusion dans un wrapper](#wrapping)
        - [Laisser les instructions et les déclarations de membre sur la même ligne](#wrapping_statement)
        - [Laisser un bloc sur une seule ligne](#wrapping_block)

## <a name="usings">Organiser les instructions Using</a>
### <a name="usings_sort_system_first">Trier d’abord les directives System</a>
|  Nom de l’option | `dotnet_sort_system_directives_first` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Trier les instructions using System.* par ordre alphabétique et les placer avant les autres instructions using.| **C# :** <br>`using System.Collections.Generic;`<br> `using System.Threading.Tasks;`<br> `using Octokit;`
| False | Ne pas indiquer d’exigence quant à l’ordre des instructions Using | **C# :** <br>`using System.Collections.Generic;`<br> `using Octokit;` <br> `using System.Threading.Tasks;`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# .NET formatting settings:
[*.cs, *.vb]
dotnet_sort_system_directives_first = true
``` 

# <a name="csharp_formatting">Paramètres de mise en forme C#</a>
## <a name="newline">Options de saut de ligne</a>
### <a name="newline_before_brace"> Saut de ligne avant l’accolade ouvrante (`{`)</a>
|  Nom de l’option | `csharp_new_line_before_open_brace` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description 
| ------------- |:-------------|
| accessors, anonymous_methods, anonymous_types, control_blocks, events, indexers, lambdas, local_functions, methods, object_collection, properties, types. (Pour indiquer plusieurs valeurs, séparez-les par « , »). | Les accolades doivent se trouver sur une nouvelle ligne pour les expressions données (style Allman) |
| toutes les | Les accolades doivent se trouver sur une nouvelle ligne pour toutes les expressions (Allman) |
| aucun | Les accolades doivent se trouver sur la même ligne pour toutes les expressions (K&R) |

#### <a name="applied"></a>Application :
```csharp
// csharp_new_line_before_open_brace = all
void MyMethod() 
{
    if (...) 
    {
        ...
    }
}
```

```csharp
// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
``` 

### <a name="newline_before_else"> Saut de ligne avant `else`</a>
|  Nom de l’option | `csharp_new_line_before_else` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description 
| ------------- |:-------------|
| True | Placer les instructions `else` sur une nouvelle ligne.  |
| False | Placer les instructions `else` sur la même ligne.  |

#### <a name="applied"></a>Application :
```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}
```

```csharp
// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_else = true
``` 

### <a name="newline_before_catch"> Saut de ligne avant `catch`</a>
|  Nom de l’option | `csharp_new_line_before_catch` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description 
| ------------- |:-------------|
| True | Placer les instructions `catch` sur une nouvelle ligne.  |
| False | Placer les instructions `catch` sur la même ligne. |

#### <a name="applied"></a>Application :
```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}
```

```csharp
// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_catch = true
``` 

### <a name="newline_before_finally"> Saut de ligne avant `finally`</a>
|  Nom de l’option | `csharp_new_line_before_catch` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description 
| ------------- |:-------------|
| True | Les instructions `finally` doivent se trouver sur une nouvelle ligne après l’accolade fermante.  |
| False | Les instructions `finally` doivent se trouver sur la même ligne que l’accolade fermante.  |

#### <a name="applied"></a>Application :
```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}
```

```csharp
// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_finally = true
``` 

### <a name="newline_before_object"> Saut de ligne avant les membres dans les initialiseurs d’objet</a>
|  Nom de l’option | `csharp_new_line_before_members_in_object_initializers` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description 
| ------------- |:-------------|
| True | Les membres d’initialiseurs d’objet doivent être sur des lignes distinctes.  |
| False | Les membres d’initialiseurs d’objet doivent être sur la même ligne.  |

#### <a name="applied"></a>Application :
```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_object_initializers = true
``` 

### <a name="newline_before_anonymous"> Saut de ligne avant les membres dans les types anonymes</a>
|  Nom de l’option | `csharp_new_line_before_members_in_anonymous_types` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description 
| ------------- |:-------------|
| True | Les membres de types anonymes doivent être sur des lignes distinctes.  |
| False | Les membres de types anonymes doivent être sur la même ligne.  |

#### <a name="applied"></a>Application :
```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}
```

```csharp
// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_members_in_anonymous_types = true
``` 

### <a name="newline_before_query"> Saut de ligne avant les membres dans les clauses d’expression de requête</a>
|  Nom de l’option | `csharp_new_line_within_query_expression_clauses` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description 
| ------------- |:-------------|
| True | Les éléments des clauses d’expression de requête doivent se trouver sur des lignes distinctes.  |
| False | Les éléments des clauses d’expression de requête doivent se trouver sur la même ligne.  |

#### <a name="applied"></a>Application :
```csharp
// csharp_new_line_within_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;
```

```csharp
// csharp_new_line_within_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_new_line_within_query_expression_clauses = true
``` 

## <a name="indent">Options de mise en retrait</a>
### <a name="indent_switch"> Mettre en retrait le contenu de `switch` case</a>
|  Nom de l’option | `csharp_indent_case_contents` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description 
| ------------- |:-------------|
| True | Mettre en retrait le contenu de `switch` case  |
| False | Ne pas mettre en retrait le contenu de `switch` case |

#### <a name="applied"></a>Application :
```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}
```

```csharp
// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
``` 

### <a name="label">Positionnement des étiquettes</a>
|  Nom de l’option | `csharp_indent_labels` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description 
| ------------- |:-------------|
| one_less | Les étiquettes sont positionnées d’un retrait à gauche par rapport au contexte actuel |
| no_change | Les étiquettes sont placées au même niveau de retrait que le contexte actuel |

#### <a name="applied"></a>Application :
```csharp
// csharp_indent_labels = one_less
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
error:
    throw new Exception(...);
}

```

```csharp
// csharp_indent_labels= no_change
private string MyMethod(...) 
{
    if (...) {
        goto error;
    }
    error:
    throw new Exception(...);
}
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_indent_labels = one_less
``` 

## <a name="spacing">Options d’espacement</a>
### <a name="space_after_cast"> Espace après un cast </a>
|  Nom de l’option | `csharp_space_after_cast` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué |
| ------------- |:-------------|:-------------|
| True | Un espace doit figurer entre un cast et la valeur  | **C# :** <br>`int y = (int) x;`
| False | Aucun espace ne doit figurer entre le cast et la valeur | **C# :** <br>`int y = (int)x;`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
``` 

### <a name="space_control_flow"> Espace après les mots clés dans les instructions de flux de contrôle </a>
|  Nom de l’option | `csharp_space_after_keywords_in_control_flow_statements` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué |
| ------------- |:-------------|:-------------|
| True | Un espace doit figurer après un mot clé | **C# :** <br>`for (int i;i<x;i++) { ... }`
| False | Aucun espace ne doit figurer après un mot clé | **C# :** <br>`for(int i;i<x;i++) { ... }`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_space_after_keywords_in_control_flow_statements = true
``` 

### <a name="space_parameter_list"> Espace entre les parenthèses de la liste des arguments de déclaration de méthode </a>
|  Nom de l’option | `csharp_space_between_method_declaration_parameter_list_parentheses` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué |
| ------------- |:-------------|:-------------|
| True | Un espace doit figurer après un mot clé | **C# :** <br>`void Bark( int x ) { ... }`
| False | Aucun espace ne doit figurer après un mot clé | **C# :** <br>`void Bark(int x) { ... }`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_declaration_parameter_list_parentheses = true
```

### <a name="space_method_call"> Espace dans les parenthèses de la liste d’arguments d’appel de méthode</a>
|  Nom de l’option | `csharp_space_between_method_call_parameter_list_parentheses` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué |
| ------------- |:-------------|:-------------|
| true | Placer un espace entre les parenthèses d’instructions de flux de contrôle | **C# :** <br>`MyMethod( argument );`
| false | Placer un espace entre les parenthèses d’expressions | **C# :** <br>`MyMethod(argument);`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_method_call_parameter_list_parentheses = control_flow_statements, type_casts
```  

### <a name="space_other"> Espace dans les parenthèses pour les autres options </a>
|  Nom de l’option | `csharp_space_between_parentheses` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué |
| ------------- |:-------------|:-------------|
| control_flow_statements | Placer un espace entre les parenthèses d’instructions de flux de contrôle | **C# :** <br>`for( int i;i<x;i++ ) { ... }`
| expressions | Placer un espace entre les parenthèses d’expressions | **C# :** <br>`var z = ( x * y ) - ( ( y - x ) * 3);`
| type_casts | Placer un espace entre les parenthèses dans les casts de type | **C# :**<br>`int y = ( int )x;`

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_space_between_parentheses = control_flow_statements, type_casts
``` 

## <a name="wrapping">Options d’inclusion dans un wrapper</a>
### <a name="wrapping_statement">Laisser les instructions et les déclarations de membre sur la même ligne</a>
|  Nom de l’option | `csharp_preserve_single_line_statements` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description |
| ------------- |:-------------|
| True | Laisser les instructions et les déclarations de membre sur la même ligne  | 
| False | Laisser les instructions et les déclarations de membre sur des lignes différentes | 

#### <a name="applied"></a>Appliqué
```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";
```

```csharp
//csharp_preserve_single_line_statements = false
int i = 0; 
string name = "John";
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
``` 

### <a name="wrapping_block">Laisser un bloc sur une seule ligne</a>
|  Nom de l’option | `csharp_preserve_single_line_blocks` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description |
| ------------- |:-------------|
| True | Laisser un bloc sur une seule ligne | 
| False | Laisser un bloc sur des lignes distinctes | 

#### <a name="applied"></a>Appliqué
```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }
```

```csharp
//csharp_preserve_single_line_blocks = false
public int MyProperty
{ 
    get; set;
}
```

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_blocks = true
``` 

# <a name="naming"> Conventions de nommage </a>
## <a name="overview"></a>Vue d'ensemble
**Format de la règle :**<br>
namingRuleTitle :<br>
`dotnet_naming_rule.<namingRuleTitle>.symbols = <symbolTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>`<br>
`dotnet_naming_rule.<namingRuleTitle>.severity = none|suggestion|warning|error`<br>
<br>
symbolTitle :<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_kinds = class, struct, interface, enum, property, method, field, event, namespace, delegate, type_parameter`<br>
`dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities = public, internal, private, protected, protected_internal`<br>
`dotnet_naming_symbols.<symbolTitle>.required_modifiers = abstract, async, const, readonly, static`<br>
<br>
styleTitle :<br>
`dotnet_naming_style.<styleTitle>.capitalization = pascal_case|camel_case|first_word_upper|all_upper|all_lower`<br>
`dotnet_naming_style.<styleTitle>.required_prefix = string`<br>
`dotnet_naming_style.<styleTitle>.required_suffix = string`<br>
`dotnet_naming_style.<styleTitle>.word_separator = string`<br>

## <a name="writing-a-naming-convention"></a>Écriture d’une convention de nommage
Pour les conventions de nommage, vous devez spécifier des **symboles**, un **style** et une **gravité**. Les conventions de nommage doivent être classées de la plus spécifique à la moins spécifique. La première règle applicable rencontrée est la seule règle appliquée. 

### <a name="severity"></a>Gravité
Les options valides pour la gravité d’une règle de style d’affectation de noms sont `none`, `silent`, `suggestion`, `warning` et `error`.

 `none` et `silent` sont synonymes et signifient qu’aucun genre d’indication ne doit être affiché à l’utilisateur. Cela a pour effet de désactiver cette règle.

 `suggestion` signifie que l’utilisateur voit ce qui suit dans la liste d’erreurs et dans l’IDE. La gravité `suggetion` permet l’exécution de la règle d’affectation de noms, mais n’entraîne pas l’arrêt de la build.

Gravité | effet
------------ | -------------
none/silent | Ne rien afficher à l’utilisateur quand ce style n’est pas suivi, quelle que soit la manière dont les fonctionnalités de génération de code seront générées dans ce style. 
suggestion | Quand ce style n’est pas suivi, l’afficher à l’utilisateur comme suggestion (points de soulignement sur les deux premiers caractères).
avertissement | Quand ce style n’est pas suivi, afficher un avertissement du compilateur.
erreur | Quand ce style n’est pas suivi, afficher une erreur du compilateur.

### <a name="symbol-specification"></a>Spécification de symboles
Identifiez à _quels_ symboles _avec quels_ modificateurs et _à quel_ niveau d’accessibilité la règle d’affectation de noms doit s’appliquer.

|  Nom de l’option | `dotnet_naming_rule.<namingRuleTitle>.symbols` |
| ------------- |:-------------:|
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_kinds`
|  | `dotnet_naming_symbols.<symbolTitle>.applicable_accessibilities`
|  | `dotnet_naming_symbols.<symbolTitle>.required_modifiers`

| Symbole | Accessibilité | Modificateurs
| ------------- |------------- |------------- |
| `*` | `*` |  `abstract` | 
| `class` | `public` |  `must_inherit` | `async` | 
| `struct` | `internal` (C#) /  | `const` | 
| `interface` | `friend` (Visual Basic) | `readonly` | 
| `enum` | `private`  | `static` | 
| `property` | `protected` | `shared` |
| `method` |`protected_internal` (C#) | |
| `field` | `protected_friend` (Visual Basic) | |
| `event` | | |
| `delegate` | | |

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols = any_async_methods

dotnet_naming_symbols.any_async_methods.applicable_kinds = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers = async
``` 

### <a name="style-specification"></a>Spécification de style
Identifiez le style d’affectation de noms à appliquer aux symboles.

|  Nom de l’option | `dotnet_naming_rule.<namingRuleTitle>.style = <styleTitle>` |
| ------------- |:-------------:|
|  | `dotnet_naming_style.<styleTitle>.capitalization`|
|  | `dotnet_naming_style.<styleTitle>.required_prefix`|
|  | `dotnet_naming_style.<styleTitle>.required_suffix`|
|  | `dotnet_naming_style.<styleTitle>.word_separator`|


| Style | Description |
| ------------- |:-------------:|
| Préfixe | Caractères qui doivent apparaître avant l’identificateur. |
| Suffixe | Caractères requis qui doivent apparaître après l’identificateur. |
| Séparateur de mots | Séparateur requis entre les mots dans l’identificateur. |
| Mise en majuscules |`pascal_case`, `camel_case`, `first_word_upper`, `all_upper`, `all_lower` | 

#### <a name="example-editorconfig-file"></a>Exemple de fichier editorconfig :
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.style = end_in_async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization = pascal_case
``` 

### <a name="example-naming-convention"></a>Exemple de convention d’affectation de noms
```
# CSharp formatting settings:
[*.cs]
dotnet_naming_rule.async_methods_end_in_async.symbols  = any_async_methods
dotnet_naming_rule.async_methods_end_in_async.style    = end_in_async
dotnet_naming_rule.async_methods_end_in_async.severity = suggestion

dotnet_naming_symbols.any_async_methods.applicable_kinds           = method
dotnet_naming_symbols.any_async_methods.applicable_accessibilities = *
dotnet_naming_symbols.any_async_methods.required_modifiers         = async

dotnet_naming_style.end_in_async.required_suffix = Async
dotnet_naming_style.end_in_async.capitalization  = pascal_case
``` 

