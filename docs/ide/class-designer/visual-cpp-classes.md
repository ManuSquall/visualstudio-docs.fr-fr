---
title: Classes C++ dans Concepteur de classes
description: Découvrez les classes C++ et comment elles sont prises en charge et peut avoir plusieurs relations d’héritage dans Concepteur de classes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: e1a1e075d2ac8d06320c46f8d2bb86992814ae24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963365"
---
# <a name="c-classes-in-class-designer"></a>Classes C++ dans Concepteur de classes

Le **Concepteur de classes** prend en charge les classes C++ et visualise les classes C++ natives de la même façon que les formes de classe Visual Basic et C#, à la différence près que les classes C++ peuvent avoir plusieurs relations d’héritage. Vous pouvez développer la forme de classe pour afficher plus de champs et de méthodes dans la classe, ou la réduire pour économiser l’espace.

> [!NOTE]
> **Concepteur de classes** ne prend pas en charge les unions (un type spécial de classe dans laquelle la mémoire allouée est uniquement la quantité nécessaire pour le membre de données le plus volumineux de l’Union).

## <a name="simple-inheritance"></a>Héritage simple

Quand vous faites glisser plusieurs classes sur un diagramme de classes et que les classes ont une relation d’héritage de classe, une flèche les connecte. La flèche pointe dans la direction de la classe de base. Par exemple, quand les classes suivantes sont affichées dans un diagramme de classes, une flèche les connecte en pointant de B vers A :

```cpp
class A {};
class B : A {};
```

Vous pouvez également faire glisser uniquement la classe B sur le diagramme de classes, cliquer avec le bouton droit sur la forme de classe pour B, puis cliquer sur **Afficher les classes de base**. Cela affiche sa classe de base : A.

## <a name="multiple-inheritance"></a>Héritage multiple

**Concepteur de classes** prend en charge la visualisation de relations d’héritage de classes multiples. L’*héritage multiple* est utilisé quand une classe dérivée a des attributs de plusieurs classes de base. Voici un exemple d’héritage multiple :

```cpp
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

Quand vous faites glisser plusieurs classes sur le diagramme de classes et que les classes ont une relation d’héritage de classes multiples, une flèche les connecte. La flèche pointe dans la direction des classes de base.

Pour afficher les classes de base correspondant à la classe adoptée, cliquez avec le bouton droit sur une forme de classe, puis cliquez sur **Afficher les classes de base**.

> [!NOTE]
> La commande **Afficher les classes dérivées** n’est pas prise en charge pour le code C++. Pour afficher les classes dérivées, accédez à **affichage de classes**, développez le nœud type, développez le sous-dossier **types dérivés** , puis faites glisser ces types sur le diagramme de classes.

Pour plus d’informations sur l’héritage de classes multiples, consultez [Héritage multiple](/previous-versions/6td5yws2(v=vs.140)) et [Plusieurs classes de base](/cpp/cpp/multiple-base-classes).

## <a name="abstract-classes"></a>Classes abstraites

**Concepteur de classes** prend en charge les classes abstraites (également appelées « classes de base abstraites »). Il s’agit de classes que vous n’instanciez jamais, mais desquelles vous pouvez dériver d’autres classes. Dans le cadre de l’exemple "Héritage multiple" présenté précédemment dans ce document, vous pouvez instancier la classe `Bird` comme objets individuels, comme suit :

```cpp
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

Toutefois, dans certains cas, vous pouvez ne pas souhaiter instancier la classe `Swimmer` en tant qu’objets individuels. Vous pouvez vouloir uniquement en dériver d’autres types de classes d’animaux, comme `Penguin`, `Whale` et `Fish`. Dans ce cas, vous déclarez la classe `Swimmer` comme classe de base abstraite.

Pour déclarer une classe abstraite, vous pouvez utiliser le mot clé `abstract`. Les membres marqués comme abstraits, ou inclus dans une classe abstraite, sont virtuels et doivent être implémentés par des classes qui dérivent de la classe abstraite.

```cpp
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

Vous pouvez également déclarer une classe comme abstraite en incluant au moins une fonction virtuelle pure :

```cpp
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

Quand vous affichez ces déclarations dans un diagramme de classes, le nom de classe `Swimmer` et sa fonction virtuelle pure `swim` s’affichent en italique dans une forme de classe abstraite et sont accompagnés de la notation **Classe abstraite**. Notez que la forme de type de classe abstraite est identique à celle d’une classe normale, sauf que sa bordure est une ligne pointillée.

Pour pouvoir être instanciée, une classe dérivée d’une classe de base abstraite doit substituer chaque fonction virtuelle pure dans la classe de base. Ainsi, si vous dérivez une classe `Fish` à partir de la classe `Swimmer`, par exemple, `Fish` doit substituer la méthode `swim` :

```cpp
class Fish : public Swimmer
{
   void swim(int speed);
};

int main()
{
   Fish guppy;
}
```

Quand vous affichez ce code dans un diagramme de classes, **Concepteur de classes** dessine une ligne d’héritage de `Fish` à `Swimmer` .

## <a name="anonymous-classes"></a>Classes anonymes

**Concepteur de classes** prend en charge les classes anonymes. Les *types de classes anonymes* sont des classes déclarées sans identificateur. Elles ne peuvent pas avoir de constructeur ou de destructeur, ne peuvent pas être passées comme arguments aux fonctions et ne peuvent pas être retournées en tant que valeurs de retour de fonctions. Vous pouvez utiliser une classe anonyme pour remplacer un nom de classe par un nom de typedef, comme dans l’exemple suivant :

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

Les structures peuvent également être anonymes. **Concepteur de classes** affiche les classes et les structures anonymes de la même façon qu’il affiche le type respectif. Bien que vous puissiez déclarer et afficher des classes et des structures anonymes, **Concepteur de classes** n’utilise pas le nom de balise que vous spécifiez. Il utilise le nom généré par l’affichage de classes. La classe ou la structure apparaît dans Affichage de classes et **Concepteur de classes** sous la forme d’un élément appelé **__unnamed**.

Pour plus d’informations sur les classes anonymes, consultez [Types de classe anonymes](/cpp/cpp/anonymous-class-types).

## <a name="template-classes"></a>Classes de modèle

**Concepteur de classes** prend en charge la visualisation des classes de modèles. Les déclarations imbriquées sont prises en charge. Le tableau suivant présente des déclarations classiques.

| Élément de code | Vue Concepteur de classes |
| - | - |
| `template <class T>`<br /><br /> `class A {};` | `A<T>`<br /><br /> Classe de modèle |
| `template <class T, class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Classe de modèle |
| `template <class T, int i>`<br /><br /> `class A {};` | `A<T, i>`<br /><br /> Classe de modèle |
| `template <class T, template <class K> class U>`<br /><br /> `class A {};` | `A<T, U>`<br /><br /> Classe de modèle |

Le tableau suivant présente quelques exemples de spécialisation partielle.

|Élément de code|Vue Concepteur de classes|
|------------------| - |
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Classe de modèle|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Classe de modèle|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Classe de modèle|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Classe de modèle|

Le tableau suivant présente quelques exemples d’héritage dans la spécialisation partielle.

|Élément de code|Vue Concepteur de classes|
|------------------| - |
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Classe de modèle<br /><br /> `B`<br /><br /> Class<br /><br /> (pointe vers la classe A)<br /><br /> `C`<br /><br /> Class<br /><br /> (pointe vers la classe A)|

Le tableau suivant présente quelques exemples de fonctions de modèle de spécialisation partielle.

|Élément de code|Vue Concepteur de classes|
|------------------| - |
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> Func \<T, U> (+ 1 surcharge)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Classe de modèle<br /><br /> `B<T2>`<br /><br /> Classe de modèle<br /><br /> (B est contenu dans la classe A sous **Types imbriqués**)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Class<br /><br /> -> C\<int><br /><br /> `C<T>`<br /><br /> Classe de modèle|

Le tableau suivant présente quelques exemples d’héritage de modèle.

|Élément de code|Vue Concepteur de classes|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Class<br /><br /> ->B<br /><br /> `C<int>`<br /><br /> Class<br /><br /> (B est contenu dans la classe C sous **Types imbriqués**)<br /><br /> `C<T>`<br /><br /> Classe de modèle|

Le tableau suivant présente des exemples de connexion de classes spécialisées canoniques.

|Élément de code|Vue Concepteur de classes|
|------------------| - |
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Class<br /><br /> ->C\<int><br /><br /> `C<int>`<br /><br /> Class<br /><br /> `C<T>`<br /><br /> Classe de modèle<br /><br /> `D`<br /><br /> Class<br /><br /> ->C\<float>|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T>|

## <a name="see-also"></a>Voir aussi

- [Utilisation du code C++](working-with-visual-cpp-code.md)
- [Classes et structs](/cpp/cpp/classes-and-structs-cpp)
- [Types de classes anonymes](/cpp/cpp/anonymous-class-types)
- [Héritage multiple](/previous-versions/6td5yws2(v=vs.140))
- [Plusieurs classes de base](/cpp/cpp/multiple-base-classes)
- [Modèles](/cpp/cpp/templates-cpp)