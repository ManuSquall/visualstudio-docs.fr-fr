---
title: "Modifications avec rupture dans Visual&#160;C++&#160;2015 Mise &#224; jour&#160;1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c0b1c2b-e1cf-4767-885b-b98df9b3730e
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "mithom"
manager: "ghogen"
---
# Modifications avec rupture dans Visual&#160;C++&#160;2015 Mise &#224; jour&#160;1
Lorsque vous effectuez une mise à niveau vers Visual C\+\+ 2015 Mise à jour 1, vous pouvez rencontrer des erreurs de compilation et\/ou d’exécution dans du code qui pouvait auparavant être compilé et exécuté correctement. Les modifications du comportement au moment de la compilation ou de l’exécution qui génèrent de tels problèmes sont appelées *modifications avec rupture* et elles sont généralement requises par des modifications apportées à la norme du langage C\+\+, aux signatures des fonctions ou à la disposition des objets en mémoire.  
  
 Le reste de cet article décrit des modifications avec rupture spécifiques dans Visual C\+\+ 2015 Mise à jour 1 et, dans cet article, les termes « nouveau comportement » ou « à présent » font référence à cette version. Les termes « ancien comportement » et « précédent » font référence à la version initiale de Visual Studio 2015 et aux versions antérieures. Pour plus d’informations sur les modifications avec rupture qui se sont produites entre Visual Studio 2013 et Visual Studio 2015, consultez [Modifications avec rupture dans Visual C\+\+ 2015](/visual-cpp/porting/visual-cpp-change-history-2003-20151).  
  
-   [Modifications avec rupture du compilateur](#BK_compiler)  
  
##  <a name="BK_compiler"></a> Compilateur Visual C\+\+  
  
-   **Classes de base virtuelles privées et héritage indirecte**  
  
     Les versions précédentes du compilateur autorisaient une classe dérivée à appeler des fonctions membres de ses classes de base `private virtual`*dérivées indirectement*.  Cet ancien comportement était incorrect et non conforme à la norme C\+\+. Le compilateur n’accepte plus de code écrit de cette façon. Il émet dans ce cas l’erreur du compilateur C2280.  
  
 **erreur C2280 : *’void \*S3::\_\_delDtor\(unsigned int\)’* : tentative de référencement d’une fonction supprimée**     Exemple \(avant\)  
  
    ```cpp  
    class base { protected: base(); ~base(); }; class middle: private virtual base {};class top: public virtual middle {}; void destroy(top *p) { delete p;  // }  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
    class base;  // as above class middle: protected virtual base {}; class top: public virtual middle {}; void destroy(top *p) { delete p; }  
    ```  
  
     ou  
  
    ```  
    class base;  // as above class middle: private virtual base {}; class top: public virtual middle, private virtual bottom {}; void destroy(top *p) { delete p; }  
    ```  
  
-   **Opérateurs new et delete surchargés**  
  
     Avec les versions précédentes du compilateur, vous pouviez déclarer un `operator new` non membre et un `operator delete` non membre comme static, et vous pouviez les déclarer dans des espaces de noms autres que l’espace de noms global.  Cet ancien comportement créé un risque que le programme n’appelle pas l’implémentation de l’opérateur `new` ou `delete` prévue par le programmeur, entraînant ainsi un comportement incorrect en mode silencieux. Le compilateur n’accepte plus de code écrit de cette façon. Au lieu de cela, il émet l’erreur du compilateur C2323.  
  
 **erreur C2323 : *’operator new’* : les fonctions d’opérateur non membre new ou delete ne peuvent pas être déclarées static ou dans un espace de noms autre que l’espace de noms global.**     Exemple \(avant\)  
  
    ```cpp  
  
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
  
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'  
    ```  
  
     De plus, bien que le compilateur ne donne pas de diagnostic spécifique, l’opérateur new inline est considéré comme incorrect.  
  
-   **Appel de ’operator *type*\(\)’ \(conversion définie par l’utilisateur\) sur des types autres que des types classe**  
  
     Les versions précédentes du compilateur autorisaient l’appel de ’operator *type*\(\)’ sur des types autres que des types classe et ignoraient cet appel en silence. Cet ancien comportement créait un risque de génération de code incorrect en mode silencieux qui provoquait un comportement imprévisible au moment de l’exécution. Le compilateur n’accepte plus de code écrit de cette façon. Au lieu de cela, il émet l’erreur du compilateur C2228.  
  
 **erreur C2228 : la partie gauche de ’.operator *type*’ doit avoir un class\/struct\/union**     Exemple \(avant\)  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column.operator index_t());  // error C2228 }  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
    typedef int index_t; void bounds_check(index_t index); void login(int column) { bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int' }  
    ```  
  
-   **Typename redondant dans les spécificateurs de type élaborés**  
  
     Les versions précédentes du compilateur autorisaient `typename` dans les spécificateurs de type élaborés. Le code écrit de cette manière est sémantiquement incorrect. Le compilateur n’accepte plus de code écrit de cette façon. Au lieu de cela, il émet l’erreur du compilateur C3406.  
  
 **erreur C3406 : impossible d’utiliser ’typename’ dans un spécificateur de type élaboré**     Exemple \(avant\)  
  
    ```cpp  
    template <typename class T> class container;  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case class container;  
    ```  
  
-   **Déduction de type des tableaux à partir d’une liste d’initialiseurs**  
  
     Les versions précédentes du compilateur ne prenaient pas en charge la déduction de type des tableaux à partir d’une liste d’initialiseurs. Le compilateur prend désormais en charge cette forme de déduction de type. Ainsi, les appels à des modèles de fonctions à l’aide de listes d’initialiseurs peuvent maintenant être ambigus ou une surcharge autre que dans les versions précédentes du compilateur peut être choisie. Pour résoudre ces problèmes, le programme doit maintenant spécifier explicitement la surcharge prévue par le programmeur.  
  
     Lorsque, à cause de ce nouveau comportement, la résolution de surcharge prend en compte un candidat supplémentaire qui est tout aussi efficace que le candidat historique, l’appel devient ambigu et le compilateur émet l’erreur C2668.  
  
 **erreur C2668: ’*fonction*’ : appel ambigu à une fonction surchargée.**     Exemple 1 : appel ambigu à une fonction surchargée \(avant\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...) template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // The compiler now considers this call ambiguous, and issues a compiler error  f({3});  error C2668: 'f' ambiguous call to overloaded function }  
    ```  
  
     Exemple 1 : appel ambigu à une fonction surchargée \(après\)  
  
    ```cpp  
    template <typename... Args> void f(int, Args...);  // template <int N, typename... Args> void f(const int (&)[N], Args...); int main() { // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it. f(3); }  
    ```  
  
     Lorsque, à cause de ce nouveau comportement, la résolution de surcharge prend en compte un candidat supplémentaire qui est une meilleure correspondance que le candidat historique, l’appel résout sans ambiguïté le nouveau candidat, ce qui provoque une modification du comportement du programme probablement différente de ce que le programmeur a prévu.  
  
     Exemple 2 : modification de la résolution de surcharge \(avant\)  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...) struct S { int i; int j; }; template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // The compiler now resolves this call to f(const int (&)[N], Args...) instead  f({1, 2}); }  
    ```  
  
     Exemple 2 : modification de la résolution de surcharge \(après\)  
  
    ```cpp  
    struct S;  // as before template <typename... Args> void f(S, Args...); template <int N, typename... Args> void f(const int *&)[N], Args...); int main() { // To call f(S, Args...), perform an explicit cast to S on the initializer list. f(S{1, 2}); }  
    ```  
  
-   **Restauration des avertissements d’instruction switch**  
  
     Une version précédente du compilateur supprimait les avertissements préexistants liés aux instructions `switch`. Ces avertissements ont été restaurés. Le compilateur émet désormais les avertissements restaurés, et les avertissements liés à des cas spécifiques \(notamment le cas par défaut\) sont désormais émis sur la ligne contenant le cas qui pose problème, plutôt que sur la dernière ligne de l’instruction switch. Comme ces avertissements ne sont plus émis sur les mêmes lignes qu’auparavant, les avertissements précédemment supprimés à l’aide de `#pragma warning(disable:####)` peuvent ne plus être supprimés comme prévu. Pour supprimer ces avertissements comme prévu, vous devrez peut\-être déplacer la directive `#pragma warning(disable:####)` vers une ligne au\-dessus du premier cas potentiellement incriminé. Voici les avertissements restaurés.  
  
 **avertissement C4060 : l’instruction switch ne contient aucune étiquette ’case’ ou ’default’ avertissement C4061 : l’énumérateur ’*bit1*’ dans le switch de l’enum ’*flags*’ n’est pas géré explicitement par une étiquette case avertissement C4062 : l’énumérateur ’*bit1*’ dans le switch de l’enum ’*flags*’ n’est pas géré avertissement C4063 : le cas ’*bit32*’ n’est pas une valeur valide pour le switch de l’enum ’*flags*’ avertissement C4064 : commutateur de l’enum incomplet ’*flags*’ avertissement C4065 : l’instruction switch contient ’default’ mais aucune étiquette ’case’ avertissement C4808 : ’*value*’ case n’est pas une valeur valide dans une condition switch de type ’*bool*’ avertissement C4809 : l’instruction switch a une étiquette ’default’ redondante ; toutes les étiquettes ’case’ possibles sont fournies**     Exemple d’avertissement C4063 \(avant\)  
  
    ```cpp  
    class settings { public: enum flags { bit0 = 0x1, bit1 = 0x2, ... }; ... }; int main() { auto val = settings::bit1; switch (val) { case settings::bit0: break; case settings::bit1: break;  case settings::bit0 | settings::bit1:  // warning C4063 break; } };  
    ```  
  
     Exemple d’avertissement C4063 \(après\)  
  
    ```cpp  
    class settings {...};  // as above int main() { // since C++11, use std::underlying_type to determine the underlying type of an enum typedef std::underlying_type<settings::flags>::type flags_t; auto val = settings::bit1; switch (static_cast<flags_t>(val)) { case settings::bit0: break; case settings::bit1: break; case settings::bit0 | settings::bit1:  // ok break; } };  
    ```  
  
     Des exemples des autres avertissements restaurés sont fournis dans leur documentation.  
  
-   **\#include : utilisation du spécificateur de répertoire parent ’..’ dans le chemin d’accès** \(affecte uniquement \/Wall \/WX\)  
  
     Les versions précédentes du compilateur ne détectaient pas l’utilisation du spécificateur de répertoire parent ’..’ dans le chemin d’accès des directives `#include`. Le code écrit de cette manière est généralement conçu pour inclure des en\-têtes qui existent en dehors du projet en utilisant de manière incorrecte des chemins d’accès relatifs au projet. Cet ancien comportement créait un risque que le programme puisse être compilé en incluant un fichier source différent de celui prévu par le programmeur, ou que ces chemins d’accès relatifs ne soient pas portables vers d’autres environnements de génération. Désormais, le compilateur détecte et informe le programmeur du code écrit de cette façon, et il émet un avertissement C4464 facultatif si cette fonctionnalité est activée.  
  
 **avertissement C4464 : le chemin d’accès include relatif contient ’..’**     Exemple \(avant\)  
  
    ```cpp  
    #include "..\headers\C4426.h"  // emits warning C4464  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories  
    ```  
  
     De plus, bien que le compilateur ne donne pas de diagnostic spécifique, nous vous recommandons également de ne pas utiliser le spécificateur de répertoire parent ".." pour spécifier les répertoires include de votre projet.  
  
-   **\#pragma optimize\(\) s’étend au\-delà de la fin du fichier d’en\-tête** \(affecte uniquement \/Wall \/WX\)  
  
     Les versions précédentes du compilateur ne détectaient pas les modifications apportées aux paramètres de l’indicateur d’optimisation qui échappent un fichier d’en\-tête inclus dans une unité de traduction. Désormais, le compilateur détecte et informe le programmeur du code écrit de cette façon, et il émet un avertissement C4426 facultatif à l’emplacement du `#include` incriminé, si cette fonctionnalité est activée. Cet avertissement est émis uniquement si le modifications entrent en conflit avec les indicateurs d’optimisation définis par des arguments de ligne de commande au compilateur.  
  
 **avertissement C4426 : indicateurs d’optimisation modifiés après l’ajout de l’en\-tête ; cela peut être dû à \#pragma optimize\(\)**     Exemple \(avant\)  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... // C4426.h ends // C4426.cpp #include "C4426.h"  // warning C4426  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
    // C4426.h #pragma optimize("g", off) ... #pragma optimize("", on)  // restores optimization flags set via command-line arguments // C4426.h ends // C4426.cpp #include "C4426.h"  
    ```  
  
-   **Incompatibilité de \#pragma warning\(push\)** et **\#pragma warning\(pop\)** \(affecte uniquement \/Wall \/WX\)  
  
     Les versions précédentes du compilateur ne détectaient pas les associations des modifications d’état `#pragma warning(push)` aux modifications d’état `#pragma warning(pop)` dans un autre fichier source, qui sont rarement souhaitées. Cet ancien comportement créait un risque que le programme soit compilé avec un autre ensemble d’avertissements activé que celui prévu par le programmeur, ce qui pouvait provoquer un comportement incorrect en mode silencieux. Désormais, le compilateur détecte et informe le programmeur du code écrit de cette façon, et il émet un avertissement C5031 facultatif à l’emplacement du `#pragma warning(pop)` correspondant, si cette fonctionnalité est activée. Cet avertissement comprend une note faisant référence à l’emplacement du \#pragma warning\(push\) correspondante.  
  
 **avertissement C5031 : \#pragma warning\(pop\) : incompatibilité probable, état d’avertissement envoyé dans un autre fichier**     Exemple \(avant\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h ... #pragma warning(pop)  // pops a warning state not pushed in this source file ... // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling' ... #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031 ...   
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
    // C5031_part1.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop)  // pops the warning state pushed in this source file // C5031_part1.h ends without #pragma warning(pop) // C5031_part2.h #pragma warning(push)  // pushes the warning state pushed in this source file #pragma warning(disable:####) ... #pragma warning(pop) // C5031_part1.h ends // C5031.cpp #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order. ... #include "C5031_part2.h" ...   
    ```  
  
     Bien qu’il soit rare, le code écrit de cette manière est parfois intentionnel. Le code écrit de cette manière est sensible aux modifications de l’ordre de `#include`. Dans la mesure du possible, nous conseillons que les fichiers de code source gèrent l’état d’avertissement de façon autonome.  
  
-   **\#pragma warning\(push\) sans correspondance** \(affecte uniquement \/Wall \/WX\)  
  
     Les versions précédentes du compilateur ne détectaient pas les modifications d’état `#pragma warning(push)` sans correspondance à la fin d’une unité de traduction. Désormais, le compilateur détecte et informe le programmeur du code écrit de cette façon, et il émet un avertissement C5032 facultatif à l’emplacement du \#pragma warning\(push\) sans correspondance, si cette fonctionnalité est activée. Cet avertissement est émis uniquement s’il n’y a aucune erreur de compilation dans l’unité de traduction.  
  
 **avertissement C5032 : \#pragma warning\(push\) détecté sans \#pragma warning\(pop\) correspondant**     Exemple \(avant\)  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... // C5032.h ends without #pragma warning(pop) // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
    // C5032.h #pragma warning(push) #pragma warning(disable:####) ... #pragma warning(pop) // matches #pragma warning (push) on line 1 // C5032.h ends // C5032.cpp #include "C5032.h" ... // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)  
    ```  
  
-   **Des avertissements supplémentaires peuvent être émis à la suite du suivi d’état d’avertissement \#pragma amélioré**  
  
     Les versions précédentes du compilateur ne suivaient pas les modifications de l’état d’avertissement \#pragma assez bien pour émettre tous les avertissements prévus. Ce comportement créait un risque que certains avertissements soient supprimés dans des circonstances autres que celles prévues par le programmeur. Le compilateur effectue maintenant le suivi de l’état d’avertissement \#pragma de manière plus robuste, tout particulièrement en ce qui concerne les modifications de l’état d’avertissement \#pragma dans les modèles, et il émet éventuellement de nouveaux avertissements C5031 et C5032 destinés à aider le programmeur à identifier les utilisations involontaires de `#pragma warning(push)` et `#pragma warning(pop)`.  
  
     Grâce à l’amélioration du suivi des modifications de l’état d’avertissement \#pragma, les avertissements qui étaient auparavant supprimés de manière incorrecte ou ceux liés à des problèmes anciennement mal diagnostiqués peuvent maintenant être émis.  
  
-   **Amélioration de l’identification du code inaccessible**  
  
     Les modifications apportées à la bibliothèque standard C\+\+ et la capacité améliorée à intégrer des appels de fonction par rapport aux versions précédentes du compilateur peuvent permettre au compilateur de prouver que du code est désormais inaccessible. Ce nouveau comportement peut provoquer des instances nouvelles et plus fréquentes de l’avertissement C4720.  
  
 **avertissement C4720 : impossible d’atteindre le code**     Dans de nombreux cas, cet avertissement peut être émis uniquement lors de la compilation avec les optimisations activées, car les optimisations peuvent intégrer plus d’appels de fonction, supprimer le code redondant ou permettre de déterminer que du code est inaccessible. Nous avons constaté que de nouvelles instances de l’avertissement C4720 étaient fréquentes dans des blocs try\/catch, en particulier en cas d’utilisation de [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).  
  
     Exemple \(avant\)  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // ok }  
    ```  
  
     Exemple \(après\)  
  
    ```cpp  
    try { auto iter = std::find(v.begin(), v.end(), 5); } catch(…) { do_something();  // warning C4702: unreachable code }  
    ```