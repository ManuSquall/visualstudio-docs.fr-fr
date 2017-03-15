---
title: "Modifications de derni&#232;re minute dans Visual C++&#160;2015 Update&#160;2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5545ce3f-d8da-4007-88b7-8dba7dcd4d10
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mithom"
---
# Modifications de derni&#232;re minute dans Visual C++&#160;2015 Update&#160;2
Quand vous effectuez une mise à niveau vers Visual C\+\+ 2015 Update 2 CTP, vous pouvez rencontrer des erreurs de compilation et\/ou d’exécution dans du code qui pouvait auparavant être compilé et exécuté correctement. Les modifications du comportement au moment de la compilation ou de l’exécution qui génèrent de tels problèmes sont appelées *modifications avec rupture* et elles sont généralement requises par des modifications apportées à la norme du langage C\+\+, aux signatures des fonctions ou à la disposition des objets en mémoire.  
  
 Le reste de cet article décrit des modifications de dernière minute spécifiques dans Visual C\+\+ 2015 Update 2 CTP et, dans cet article, les termes « nouveau comportement » ou « à présent » font référence à cette version. Les termes « ancien comportement » et « avant » font référence à Visual C\+\+ 2015 Update 1 et aux versions antérieures. Pour plus d’informations sur les modifications de dernière minute qui se sont produites entre la version initiale de Visual C\+\+ 2015 et Visual C\+\+ 2015 Update 1, consultez [Modifications avec rupture dans Mise à jour 1](../misc/breaking-changes-in-visual-cpp-2015-update-1.md). Pour plus d’informations sur les modifications de dernière minute qui se sont produites entre Visual C\+\+ 2013 et Visual C\+\+ 2015, consultez [Modifications avec rupture dans Visual C\+\+ 2015](/visual-cpp/porting/visual-cpp-change-history-2003-20151).  
  
-   [Modifications avec rupture du compilateur](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Compilateur Visual C\+\+  
  
-   **Des erreurs et avertissements supplémentaires peuvent être générés en raison de la prise en charge partielle de l’expression SFINAE.**  
  
     Dans les versions précédentes du compilateur, certains types d’expressions au sein des spécificateurs `decltype` n’étaient pas analysés en raison de l’absence de prise en charge de l’expression SFINAE. Cet ancien comportement était incorrect et non conforme à la norme C\+\+. À présent, le compilateur analyse ces expressions et offre une prise en charge partielle de l’expression SFINAE grâce à certaines améliorations récentes de la conformité. Par conséquent, le compilateur génère maintenant des avertissements et des erreurs détectés dans des expressions qui n’étaient pas analysées dans les versions précédentes du compilateur.  
  
     Quand ce nouveau comportement analyse une expression `decltype` comportant un type qui n’a pas encore été déclaré, le compilateur génère l’erreur de compilateur C2039.  
  
 **erreur C2039 : *'type'*: n’est pas membre de *'espace de noms global'*.**     Exemple 1 : utilisation d’un type non déclaré \(avant\)  
  
    ```cpp  
    struct s1  
    {  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  // error C2039  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     Exemple 1 \(après\)  
  
    ```cpp  
    struct s1  
    {  
      template <typename>  // forward declare s2struct s2;  
  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     Quand ce nouveau comportement analyse une expression `decltype` dans laquelle il manque le mot clé `typename` obligatoire pour spécifier qu’un nom dépendant est un type, le compilateur génère l’avertissement de compilateur C4346 en même temps que l’erreur de compilateur C2923.  
  
 **avertissement C4346 : le nom dépendant *'S2\<T\>::Type'*: n’est pas un type. erreur C2923 : *'s1'*: *'S2\<T\>::Type'*: n’est pas un argument de type de modèle valide pour le paramètre *'T'*.**     Exemple 2 : le nom dépendant n’est pas un type \(avant\)  
  
    ```cpp  
    template <typename T>  
    struct s1  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    struct s2  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923  
    };  
    ```  
  
     Exemple 2 \(après\)  
  
    ```cpp  
    template <typename T> struct s1 {...};  // as above  
    template <typename T> struct s2 {...};  // as above  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));  
    };  
    ```  
  
-   Les variables de membre `volatile`  **n’autorisent pas les constructeurs et les opérateurs d’assignation définis implicitement**.  
  
     Dans les versions précédentes du compilateur, il était possible de générer automatiquement les constructeurs de copie\/déplacement par défaut et les opérateurs d’assignation de copie\/déplacement par défaut pour une classe contenant des variables de membre `volatile`. Cet ancien comportement était incorrect et non conforme à la norme C\+\+. À présent, le compilateur considère qu’une classe avec des variables de membre volatiles a des opérateurs de construction et d’assignation non triviaux, ce qui empêche la génération automatique des implémentations par défaut de ces opérateurs.  Quand une telle classe est membre d’une union \(ou d’une union anonyme au sein d’une classe\), les constructeurs de copie\/déplacement et les opérateurs d’assignation de copie\/déplacement de l’union \(ou de la classe contenant l’union anonyme\) sont implicitement définis comme étant supprimés. Toute tentative de construction ou de copie de l’union \(ou de la classe contenant l’union anonyme\) sans avoir défini explicitement les constructeurs ou opérateurs est considérée comme une erreur. Le compilateur génère alors l’erreur de compilateur C2280.  
  
 **erreur C2280 : *'B::B\(const B &\)'* : tentative de référencement d’une fonction supprimée.**     Exemple \(avant\)  
  
    ```cpp  
    struct A  
    {  
      volatile int i;  
      volatile int j;  
    };  
  
    extern A* pa;  
  
    struct B  
    {  
      union  
      {  
        A a;  
        int i;  
      };  
    };  
  
    B b1 {*pa};  
    B b2 (b1);  // error C2280  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
    struct A  
    {  
      int i;int j;  
    };  
  
    extern volatile A* pa;  
  
    A getA()  // returns an A instance copied from contents of pa  
    {  
      A a;  
      a.i = pa->i;  
      a.j = pa->j;  
      return a;  
    }  
  
    struct B;  // as above  
  
    B b1 {GetA()};  
    B b2 (b1);  // error C2280  
    ```  
  
-   **Les fonctions membres statiques ne prennent pas en charge les qualificateurs cv.**  
  
     Dans les versions précédentes de Visual C\+\+ 2015, les fonctions membres statiques pouvaient contenir des qualificateurs cv. Ce comportement est dû à une régression effectuée dans Visual C\+\+ 2015 et dans Visual C\+\+ 2015 Update 1. Le code écrit de cette manière est refusé dans Visual C\+\+ 2013 et les versions antérieures de Visual C\+\+. Le comportement de Visual C\+\+ 2015 et de Visual C\+\+ 2015 Update 1 est incorrect, et n’est pas conforme à la norme C\+\+.  Visual Studio 2015 Update 2 refuse le code écrit de cette façon et génère l’erreur de compilateur C2511.  
  
 **erreur C2511 : 'void A::func\(void\) const': impossible de trouver la fonction membre surchargée dans 'A'.**     Exemple \(avant\)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     Exemple \(après\)  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **La déclaration anticipée d’enum n’est pas autorisée dans le code de WinRT** \(concerne \/ZW uniquement\).  
  
     Le code compilé pour le Windows Runtime \(WinRT\) n’autorise pas la déclaration anticipée des types `enum`, comme lors de la compilation de code C\+\+ managé pour le .Net Framework à l’aide du commutateur du compilateur \/clr. Ce comportement garantit que la taille d’une énumération est toujours connue et qu’elle peut être projetée correctement vers le système de type WinRT. Le compilateur refuse le code écrit de cette façon et génère l’erreur de compilateur C2599 ainsi que l’erreur de compilateur C3197.  
  
 **erreur C2599 : *'CustomEnum'*: la déclaration anticipée d’un enum WinRT n’est pas autorisée. erreur C3197 : *'public'*: peut uniquement être utilisé dans les définitions.**     Exemple \(avant\)  
  
    ```cpp  
    namespace A {  
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197  
    }  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
  
              // forward declaration of CustomEnum removed  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
-   **L’opérateur non membre surchargé new et l’opérateur delete ne peuvent pas être déclarés inline**. Niveau 1 \(\/W1\) activé par défaut.  
  
     Les versions précédentes du compilateur ne génèrent pas d’avertissement quand les fonctions d’opérateur non membre new et d’opérateur delete sont déclarées inline. Le code écrit de cette manière est incorrect \(aucun diagnostic requis\) et peut provoquer des problèmes de mémoire en raison de l’incompatibilité entre les opérateurs new et delete \(en particulier, s’ils sont associés à la désallocation dimensionnée\), qui peut être difficile à diagnostiquer.   À présent, le compilateur génère l’avertissement C4595 pour faciliter l’identification du code écrit de cette manière.  
  
 **avertissement C4595 : *'operator new'*: les fonctions d’opérateurs non membres new ou delete ne peuvent pas être déclarées inline.**     Exemple \(avant\)  
  
    ```cpp  
  
              inline void* operator new(size_t sz)  // warning C4595  
    {  
      ...  
    }  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
  
              void* operator new(size_t sz)  // removed inline  
    {  
      ...  
    }  
    ```  
  
     Pour corriger le code écrit de cette manière, vous devrez peut\-être déplacer les définitions d’opérateur du fichier d’en\-tête vers le fichier source correspondant.