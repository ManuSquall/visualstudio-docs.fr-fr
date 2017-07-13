---
title: "Paramètres de style de code .NET pour EditorConfig | Microsoft Docs"
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
caps.latest.revision: 01
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 288595f50555bd8314d0ad60cd2e1ce8121a8ab0
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---

# Paramètres de style de code .NET pour EditorConfig
<a id="net-code-style-settings-for-editorconfig" class="xliff"></a>

## Valeurs possibles 
<a id="possible-values" class="xliff"></a>

`options_name = false|true : none|suggestion|warning|error`

Pour l’option de style de code, vous devez spécifier **true** (préférez cette option) ou **false** (option déconseillée), un signe deux-points (`:`) et un niveau de gravité (`none`, `suggestion`, `warning` ou `error`). La gravité correspond au niveau d’application de ce style souhaité dans votre base de code.

Gravité | effect
------------ | -------------
aucun | Ne rien afficher à l’utilisateur quand ce style n’est pas suivi, quelle que soit la manière dont les fonctionnalités de génération de code seront générées dans ce style. 
suggestion | Quand ce style n’est pas suivi, l’afficher à l’utilisateur comme suggestion (points de soulignement sur les deux premiers caractères).
avertissement | Quand ce style n’est pas suivi, afficher un avertissement du compilateur.
erreur | Quand ce style n’est pas suivi, afficher une erreur du compilateur.

## Options de style de code .NET
<a id="net-code-style-options" class="xliff"></a>

- [Paramètres de style de code dotnet](#this_and_me)
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
- [Paramètres de style de code CSharp](#csharp_codestyle)
    - [« var »](#var)
        - [« var » pour les types intégrés](#var_built_in)
        - [« var » quand le type est visible](#var_apparent)
        - [« var » ailleurs](#var_elsewhere)
    - [Membres expression-bodied](#expression_bodied_members)
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
    - [Préférences de vérification « null »](#null_checking)
        - [Expressions-throw](#null_checking_throw_expressions)
        - [Appels de délégué conditionnels](#null_checking_conditional_delegate_calls)

## <a name="this_and_me">« This. » et « Me. » Qualification</a>

### <a name="this_and_me_fields">Champs</a>

|  Nom de l’option | `dotnet_style_qualification_for_field` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Dans l’idéal, faire précéder tous les champs non statiques utilisés dans les méthodes non statiques par `this.` en C# ou `Me.` en Visual Basic. | **C# :** <br>`this.capacity = 0;` <br><br> **Visual Basic :** `Me.capacity = 0`
| False | Dans l’idéal, ne pas faire précéder les champs non statiques utilisés dans les méthodes non statiques par `this.` en C# ou `Me.` en Visual Basic. | **C# :** <br>`capacity = 0;` <br><br> **Visual Basic :** `capacity = 0`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_field = false:suggestion
```

### <a name="this_and_me_properties">Propriétés</a>

|  Nom de l’option | `dotnet_style_qualification_for_property` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Dans l’idéal, faire précéder toutes les propriétés non statiques utilisées dans les méthodes non statiques par `this.` en C# ou `Me.` en Visual Basic.| **C# :** <br>`this.ID = 0;` <br><br> **Visual Basic :** `Me.ID = 0`
| False | Dans l’idéal, ne *pas* faire précéder les propriétés non statiques utilisées dans les méthodes non statiques par `this.` en C# ou `Me.` en Visual Basic. | **C# :** <br>`ID = 0;` <br><br> **Visual Basic :** `ID = 0`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs,*.vb]
dotnet_style_qualification_for_property = false:suggestion
```


### <a name="this_and_me_methods">Méthodes</a>
|  Nom de l’option | `dotnet_style_qualification_for_method` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Dans l’idéal, faire précéder toutes les méthodes non statiques appelées à partir de méthodes non statiques par `this.` en C# ou `Me.` en VB.| **C# :** <br>`this.Display();` <br><br> **Visual Basic :** `Me.Display()`
| False | Dans l’idéal, ne *pas* faire précéder toutes les méthodes non statiques appelées à partir de méthodes non statiques par `this.` en C# ou `Me.` en VB. | **C# :** <br>`Display();` <br><br> **Visual Basic :** `Display()`


#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_method = false:suggestion
```

### <a name="this_and_me_events">Événements</a>
|  Nom de l’option | `dotnet_style_qualification_for_event` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Dans l’idéal, faire précéder tous les événements non statiques référencés à partir de méthodes non statiques par `this.` en C# ou `Me.` en VB.| **C# :** <br>`this.Elapsed += Handler;` <br><br> **Visual Basic :** `AddHandler Me.Elapsed, AddressOf Handler`
| False | Dans l’idéal, ne *pa*s faire précéder tous les événements non statiques référencés à partir de méthodes non statiques par `this.` en C# ou `Me.` en VB. | **C# :** <br>`Elapsed += Handler;` <br><br> **Visual Basic :** `AddHandler Elapsed, AddressOf Handler`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_qualification_for_event = false:suggestion
```

## <a name="language_keywords">Mots clés de langage (int, string, etc.) vs type de framework pour les références de type </a>
### <a name="language_keywords_variables">Variables locales, paramètres et membres</a>
|  Nom de l’option | `dotnet_style_predefined_type_for_locals_parameters_members` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Pour les variables locales, les paramètres et les membres de type, faire en sorte que les types qui ont un mot clé de langage pour les représenter (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) utilisent le mot clé au lieu du nom de type (`Int32`, `Int64`, etc.).| **C# :** <br>`private int _member;` <br><br> **Visual Basic :** `Private _member As Integer`
| False | Pour les variables locales, les paramètres et les membres de type, faire en sorte que les types qui ont un mot clé de langage pour les représenter (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`) utilisent le nom de type (`Int32`, `Int64`, etc.) au lieu du mot clé.  | **C# :** <br>`private Int32 _member;` <br><br> **Visual Basic :** `Private _member As Int32`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
``` 

### <a name="language_keywords_member_access">Expressions d’accès au membre</a>
|  Nom de l’option | `dotnet_style_predefined_type_for_member_access` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer le mot clé chaque fois qu’une expression d’accès au membre est utilisée sur un type avec une représentation sous forme de mot clé (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`).| **C# :** <br>`var local = int.MaxValue;` <br><br> **Visual Basic :** `Dim local = Integer.MaxValue`
| False | Préférer le nom de type chaque fois qu’une expression d’accès au membre est utilisée sur un type avec une représentation sous forme de mot clé (`int`, `double`, `float`, `short`, `long`, `decimal`, `string`). | **C# :** <br>`var local = Int32.MaxValue;` <br><br> **Visual Basic :** `Dim local = Int32.MaxValue`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_predefined_type_for_member_access = true:suggestion
``` 

## <a name="expression_level">Préférences au niveau de l’expression</a>
### <a name="expression_level_object_initializers">Initialiseurs d’objets</a>
|  Nom de l’option | `dotnet_style_object_initializer` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’initialisation des objets à l’aide d’initialiseurs d’objets dans la mesure du possible.| **C# :** <br>`var c = new Customer(){ Age = 21 };` <br><br> **Visual Basic :** `Dim c = New Customer() With { .Age = 21 }`
| False | Faire en sorte que les objets ne soient *pas* initialisés à l’aide d’initialiseurs d’objets. | **C# :** <br>`var c = new Customer();`<br>`c.Age = 21;` <br><br> **Visual Basic :** <br>`Dim c = new Customer() `<br>`c.Age = 21`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_object_initializer = true:suggestion
``` 

### <a name="expression_level_collection_initializers">Initialiseurs de collection</a>
|  Nom de l’option | `dotnet_style_collection_initializer` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’initialisation des collections à l’aide d’initialiseurs de collection dans la mesure du possible.| **C# :** <br>`var list = new List<int>{ 1, 2, 3 };` <br><br> **Visual Basic :** <br> `Dim list = new List(Of Integer) From { 1, 2, 3}`
| False | Faire en sorte que les objets ne soient *pas* initialisés à l’aide d’initialiseurs de collection. | **C# :** <br>`var list = new List<int>();`<br>`list.Add(1);`<br>`list.Add(2);`<br>`list.Add(3);` <br><br> **Visual Basic :** <br>`Dim list = new List(Of Integer)`<br>`list.Add(1)`<br>`list.Add(2)`<br>`list.Add(3)`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_collection_initializer = true:suggestion
```

### <a name="expression_level_tuple_names">Noms de tuples explicites</a>
|  Nom de l’option | `dotnet_style_explicit_tuple_names` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les noms de tuple aux propriétés ItemX.| **C# :** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.name;` <br><br> **Visual Basic :** <br> `Dim customer As (name As String, age As Integer) = GetCustomer()`<br>`Dim name = customer.name`
| False | Préférer les propriétés ItemX aux noms de tuple. | **C# :** <br>`(string name, int age) customer = GetCustomer();`<br>`var name = customer.Item1;` <br><br> **Visual Basic :** <br>`Dim customer As (name As String, age As Integer) = GetCustomer()`<br> `Dim name = customer.Item1`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_explicit_tuple_names = true:suggestion
``` 

### <a name="expression_level_null_checking">Expressions de fusion lors de la vérification « null »</a>
|  Nom de l’option | `dotnet_style_coalesce_expression` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’expression de fusion null à la vérification d’opérateur ternaire.| **C# :** <br>`var v = x ?? y;` <br><br> **Visual Basic :** <br> `Dim v = If(x, y)`
| False | Préférer la vérification d’opérateur ternaire à l’expression de fusion null. | **C# :** <br>`var v = x != null ? x : y; // or`<br>`var v = x == null ? y : x;` <br><br> **Visual Basic :** <br>`Dim v = If(x Is Nothing, y, x) ' or`<br> `Dim v = If(x IsNot Nothing, x, y)`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_coalesce_expression = true:suggestion
``` 

### <a name="expression_level_null_propogation">Propagation de NULL lors de la vérification « null »</a>
|  Nom de l’option | `dotnet_style_null_propagation` |
| ------------- |:-------------:|
| **Langages applicables** | C# et Visual Basic

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’utilisation de l’opérateur de condition null dans la mesure du possible.| **C# :** <br>`var v = o?.ToString();` <br><br> **Visual Basic :** <br> `Dim v = o?.ToString()`
| False | Préférer la vérification de la valeur null ternaire dans la mesure du possible. | **C# :** <br>`var v = o == null ? null : o.ToString(); // or`<br>`var v = o != null ? o.String() : null;` <br><br> **Visual Basic :** <br>`Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or`<br> `Dim v = If(o IsNot Nothing, o.ToString(), Nothing)`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp and VisualBasic code style settings:
[*.cs, *.vb]
dotnet_style_null_propagation = true:suggestion
``` 

# <a name="csharp_codestyle">Paramètres de style de code CSharp</a>
## <a name="var">« var »</a>
### <a name="var_built_in">« var » pour les types intégrés</a>
|  Nom de l’option | `csharp_style_var_for_built_in_types` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’utilisation de `var` pour les types système intégrés tels que `int`.| **C# :** <br>`var x = 5;`
| False | Ne pas utiliser `var` pour les types système intégrés tels que `int`. | **C# :** <br>`int x = 5;`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
``` 

### <a name="var_apparent">« var » quand le type est visible</a>
|  Nom de l’option | `csharp_style_var_when_type_is_apparent` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer `var` quand le type est déjà mentionné dans la partie droite d’une expression de déclaration.| **C# :** <br>`var obj = new C();`
| False | Ne pas utiliser `var` quand le type est déjà mentionné dans la partie droite d’une expression de déclaration. | **C# :** <br>`C obj = new C();`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_var_when_type_is_apparent = true:suggestion
``` 

### <a name="var_elsewhere">« var » ailleurs</a>
|  Nom de l’option | `csharp_style_var_elsewhere` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer `var` dans tous les cas sauf substitution par une autre règle de style de code.| **C# :** <br>`var f = this.Init();`
| False | Ne pas utiliser var dans tous les cas, sauf substitution par une autre règle de style de code.| **C# :** <br>`bool f = this.Init();`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_var_elsewhere = true:suggestion
``` 

### <a name="expression_bodied_members">Méthodes</a>
|  Nom de l’option | `csharp_style_expression_bodied_methods` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les méthodes.| **C# :** <br>`public int GetAge() => this.Age;`
| False | Ne pas préférer les membres expression-bodied pour les méthodes.| **C# :** <br>`public int GetAge() { return this.Age; }`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:none
``` 

### <a name="expression_bodied_members_constructors">Constructeurs</a>
|  Nom de l’option | `csharp_style_expression_bodied_constructors` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les constructeurs.| **C# :** <br>`public Customer(int age) => Age = age;`
| False | Ne pas préférer les membres expression-bodied pour les constructeurs.| **C# :** <br>`public Customer(int age) { Age = age; }`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_constructors = false:none
``` 

### <a name="expression_bodied_members_operators">Opérateurs</a>
|  Nom de l’option | `csharp_style_expression_bodied_operators` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les opérateurs.| **C# :** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`=> new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);`
| False | Ne pas préférer les membres expression-bodied pour les opérateurs.| **C# :** <br>`public static ComplexNumber operator +(ComplexNumber c1, ComplexNumber c2)`<br>`{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_operators = false:none
``` 

### <a name="expression_bodied_members_properties">Propriétés</a>
|  Nom de l’option | `csharp_style_expression_bodied_properties` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les propriétés.| **C# :** <br>`public int Age => _age;`
| False | Ne pas préférer les membres expression-bodied pour les propriétés.| **C# :** <br>`public int Age { get { return _age; }}`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_properties = false:none
``` 

### <a name="expression_bodied_members_indexers">Indexeurs</a>
|  Nom de l’option | `csharp_style_expression_bodied_indexers` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les indexeurs.| **C# :** <br>`public T this[int i] => _value[i];`
| False | Ne pas préférer les membres expression-bodied pour les indexeurs.| **C# :** <br>`public T this[int i] { get { return _values[i]; } }`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_indexers = false:none
``` 

### <a name="expression_bodied_members_accessors">Accesseurs</a>
|  Nom de l’option | `csharp_style_expression_bodied_accessors` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les membres expression-bodied pour les accesseurs.| **C# :** <br>`public int Age { get => _age; set => _age = value; }`
| False | Ne pas préférer les membres expression-bodied pour les accesseurs.| **C# :** <br>`public int Age { get { return _age; } set { _age = value; } }`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_accessors = false:none
``` 

## <a name="pattern_matching">Critères spéciaux</a>
### <a name="pattern_matching_is_cast">« is » avec vérification « cast »</a>
|  Nom de l’option | `csharp_style_pattern_matching_over_is_with_cast_check` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les critères spéciaux plutôt que les expressions `is` avec des casts de type.| **C# :** <br>`if (o is int i) {...}`
| False | Préférer les expressions `is` avec des casts de type plutôt que les critères spéciaux.| **C# :** <br>`if (o is int) {var i = (int)o; ... }`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
```

### <a name="pattern_matching_as_null">« as » avec vérification « null »</a>
|  Nom de l’option | `csharp_style_pattern_matching_over_as_with_null_check` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer les critères spéciaux plutôt que les expressions `as` avec vérifications « null » pour déterminer si un élément est d’un type particulier.| **C# :** <br>`if (o is string s) {...}`
| False | Préférer les expressions `as` avec vérifications « null » plutôt que les critères spéciaux pour déterminer si un élément est d’un type particulier.| **C# :** <br>`var s = o as string; if (s != null) {...}`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

### <a name="inlined_variable_declarations">Déclarations de variables inline</a>
|  Nom de l’option | `csharp_style_inlined_variable_declaration` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer la déclaration inline des variables `out` dans la mesure du possible. | **C# :** <br>`if (int.TryParse(value, out int i) {...}`
| False | Préférer la déclaration explicite des variables `out`.| **C# :** <br>`int i; if (int.TryParse(value, out i) {...}`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

## <a name="null_checking">Préférences de vérification « null »</a>
### <a name="null_checking_throw_expressions">Expressions-throw</a>
|  Nom de l’option | `csharp_style_throw_expression` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’utilisation d’expressions throw plutôt que d’instructions throw. | **C# :** <br>`this.s = ss ?? throw new ArgumentNullException(nameof(s));`
| False | Préférer l’utilisation d’instructions throw plutôt que d’expressions throw.| **C# :** <br>`if (s==null) {throw new ArgumentNullException(nameof(s));} this.s = s;`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
```

### <a name="null_checking_conditional_delegate_calls">Préférer les appels de délégué conditionnels</a>
|  Nom de l’option | `csharp_style_conditional_delegate_call` |
| ------------- |:-------------:|
| **Langages applicables** | C#

| Valeur | Description | Appliqué 
| ------------- |:-------------|:-------------|
| True | Préférer l’utilisation de l’opérateur de fusion conditionnelle (`?.`) lors de l’appel d’une expression lambda, plutôt que d’effectuer une vérification de valeur null. | **C# :** <br>`func?.Invoke(args);`
| False | Préférer l’exécution d’une vérification de valeur null avant d’appeler une expression lambda, plutôt que d’utiliser l’opérateur de fusion conditionnelle (`?.`).| **C# :** <br>`if (func!=null) { func(args); }`

#### Exemple de fichier editorconfig :
<a id="example-editorconfig-file" class="xliff"></a>
```
# CSharp code style settings:
[*.cs]
csharp_style_conditional_delegate_call = false:suggestion
```

