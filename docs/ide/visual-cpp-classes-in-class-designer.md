---
title: "Visual C++ Classes in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritancelinelabel"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], classes"
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Classes in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le Concepteur de classes prend en charge des classes C\+\+ et visualise les classes C\+\+ natives de la même façon que les formes de classe Visual Basic et Visual C\#, mais les classes C\+\+ peuvent avoir des relations d'héritage multiples.  Vous pouvez développer la forme de classe pour afficher plus de champs et de méthodes dans la classe ou la réduire pour économiser l'espace.  
  
> [!NOTE]
>  Le Concepteur de classes ne prend pas en charge les unions \(un type spécial de classe dans laquelle la mémoire allouée est uniquement suffisante pour la plus grande donnée membre de l'union\).  
  
## Héritage simple  
 Lorsque vous faites glisser plusieurs classes sur un diagramme de classes et que les classes ont une relation d'héritage de classe, une flèche les connecte.  La flèche pointe dans la direction de la classe de base.  Par exemple, lorsque les classes suivantes sont affichées dans un diagramme de classes, une flèche les connecte en pointant de B à A :  
  
```  
class A {};  
class B : A {};  
```  
  
 Vous pouvez également faire glisser uniquement la classe B sur le diagramme de classes, cliquer avec le bouton droit sur la forme de classe pour B, puis cliquer sur **Afficher les classes de base**.  Cela affiche sa classe de base: A.  
  
## Héritage multiple  
 Le Concepteur de classes prend en charge la visualisation de relations d'héritage de classes multiples.  L'*héritage multiple* est utilisé lorsqu'une classe dérivée a des attributs de plusieurs classes de base.  Voici un exemple d'héritage multiple :  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 Lorsque vous faites glisser plusieurs classes sur le diagramme de classes et que les classes ont une relation d'héritage de classes multiples, une flèche les connecte.  La flèche pointe dans la direction des classes de base.  
  
 Cliquez avec le bouton droit sur une forme de classe, puis cliquez sur **Afficher les classes de base** pour afficher les classes de base pour la classe adoptée.  
  
> [!NOTE]
>  La commande **Show Derived Classes** n'est pas prise en charge pour le code C\+\+.  Pour afficher des classes dérivées, allez à l'Affichage de classes, développez le nœud type, développez le sous\-dossier **Types dérivés** et faites glisser ensuite ces types sur le diagramme de classes.  
  
 Pour plus d'informations sur l'héritage de classes multiples, consultez [\(NOTINBUILD\) Multiple Inheritance](http://msdn.microsoft.com/fr-fr/3b74185e-2beb-4e29-8684-441e51d2a2ca) et [Plusieurs classes de base](/visual-cpp/cpp/multiple-base-classes).  
  
## Classes abstraites  
 Le Concepteur de classes prend en charge les classes abstraites \(également appelées "classes de base abstraites"\).  Il s'agit de classes que vous n'instanciez jamais, mais desquels vous pouvez dériver d'autres classes.  Dans le cadre de l'exemple "Héritage multiple" présenté précédemment dans ce document, vous pourriez instancier la classe `Bird` en tant qu'objets individuels comme suit :  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 Toutefois, dans certains cas, vous pouvez ne pas vouloir instancier la classe `Swimmer` en tant qu'objets individuels.  Par exemple, vous pourriez l'utiliser uniquement pour dériver d'autres types de classes d'animaux, comme `Penguin`, `Whale` et `Fish`.  Dans ce cas, vous déclarez la classe `Swimmer` en tant que classe de base abstraite.  
  
 Pour déclarer une classe abstraite, vous pouvez utiliser le mot clé `abstract`.  Les membres marqués comme abstraits, ou inclus dans une classe abstraite, sont virtuels et doivent être implémentés par des classes qui dérivent de la classe abstraite.  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 Vous pouvez également déclarer une classe abstraite en incluant au moins une fonction virtuelle pure :  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 Lorsque vous affichez ces déclarations dans un diagramme de classes, le nom de classe `Swimmer` et sa fonction virtuelle pure `swim` s'affichent en italique dans une forme de classe abstraite et sont accompagnés de la notation **Classe abstraite**.  Notez que la forme de type de classe abstraite est identique à celle d'une classe normale, sauf que sa bordure est pointillée.  
  
 Pour pouvoir être instanciée, une classe dérivée d'une classe de base abstraite doit substituer chaque fonction virtuelle pure dans la classe de base.  Ainsi, par exemple, si vous dérivez une classe `Fish` à partir de la classe `Swimmer`, `Fish` doit substituer la méthode `swim` :  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 Lorsque vous affichez ce code dans un diagramme de classes, le Concepteur de classes trace une ligne d'héritage entre `Fish` et `Swimmer`.  
  
## Classes anonymes  
 Le Concepteur de classes prend en charge des classes anonymes.  Les *types de classe anonymes* sont des classes déclarées sans un identificateur.  Elles ne peuvent pas avoir de constructeur ou de destructeur, ne peuvent pas être passées en tant qu'arguments aux fonctions et ne peuvent pas être retournées en tant que valeurs de retour de fonctions.  Vous pouvez utiliser une classe anonyme pour remplacer un nom de classe par un nom de typedef, comme dans l'exemple suivant :  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 Les structures peuvent également être anonymes.  Le Concepteur de classes affiche des classes et des structures anonymes de la même façon qu'il affiche le type respectif.  Bien que vous puissiez déclarer et afficher des classes et des structures anonymes, le Concepteur de classes n'utilise pas le nom de balise que vous spécifiez.  Il utilise le nom généré par l'Affichage de classes.  La classe ou la structure apparaît dans l'Affichage de classes et Concepteur de classes comme un élément appelé **\_\_unnamed**.  
  
 Pour plus d'informations sur les classes anonymes, consultez [Types de classe anonymes](/visual-cpp/cpp/anonymous-class-types).  
  
## Classes de modèle  
 Le Concepteur de classes prend en charge la visualisation de classes de modèle.  Les déclarations imbriquées sont prises en charge.  La table suivante présente des déclarations typiques.  
  
|Élément de code|Affichage Concepteur de classes|  
|---------------------|-------------------------------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Classe de modèle|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Classe de modèle|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Classe de modèle|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Classe de modèle|  
  
 La table suivante présente quelques exemples de spécialisation partielle.  
  
|Élément de code|Affichage Concepteur de classes|  
|---------------------|-------------------------------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Classe de modèle|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Classe de modèle|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Classe de modèle|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Classe de modèle|  
  
 La table suivante présente quelques exemples d'héritage en spécialisation partielle.  
  
|Élément de code|Affichage Concepteur de classes|  
|---------------------|-------------------------------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Classe de modèle<br /><br /> `B`<br /><br /> Classe<br /><br /> \(pointe vers la Classe A\)<br /><br /> `C`<br /><br /> Classe<br /><br /> \(pointe vers la Classe A\)|  
  
 La table suivante présente quelques exemples de fonctions du modèle de spécialisation partielle.  
  
|Élément de code|Affichage Concepteur de classes|  
|---------------------|-------------------------------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> func\<T, U\> \(\+ 1 surcharge\)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Classe de modèle<br /><br /> `B<T2>`<br /><br /> Classe de modèle<br /><br /> \(B est contenu dans la classe A sous **Types imbriqués**\)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Classe<br /><br /> \-\> C\<int\><br /><br /> `C<T>`<br /><br /> Classe de modèle|  
  
 La table suivante présente quelques exemples d'héritage de modèle.  
  
|Élément de code|Affichage Concepteur de classes|  
|---------------------|-------------------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Classe<br /><br /> \-\>B<br /><br /> `C<int>`<br /><br /> Classe<br /><br /> \(B est contenu dans la classe C sous **Types imbriqués**\)<br /><br /> `C<T>`<br /><br /> Classe de modèle|  
  
 La table suivante présente quelques exemples de connexion de classe spécialisée canonique.  
  
|Élément de code|Affichage Concepteur de classes|  
|---------------------|-------------------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Classe<br /><br /> \-\>C\<int\><br /><br /> `C<int>`<br /><br /> Classe<br /><br /> `C<T>`<br /><br /> Classe de modèle<br /><br /> `D`<br /><br /> Classe<br /><br /> \-\>C\<float\>|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T\>|  
  
## Voir aussi  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Classes et structs](/visual-cpp/cpp/classes-and-structs-cpp)   
 [Types de classe anonymes](/visual-cpp/cpp/anonymous-class-types)   
 [\(NOTINBUILD\) Multiple Inheritance](http://msdn.microsoft.com/fr-fr/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [Plusieurs classes de base](/visual-cpp/cpp/multiple-base-classes)   
 [Modèles](/visual-cpp/cpp/templates-cpp)