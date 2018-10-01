---
title: Expressions dans le débogueur | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: hero-article
f1_keywords:
- vs.debug.expressions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VBScript
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b8350356b82b6d2cefc3fda725d90dccea75e55
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493719"
---
# <a name="expressions-in-the-debugger"></a>Expressions dans le débogueur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Expressions dans le débogueur](https://docs.microsoft.com/visualstudio/debugger/expressions-in-the-debugger).  
  
Le débogueur Visual Studio inclut des évaluateurs d’expression qui fonctionnent lorsque vous entrez une expression dans la boîte de dialogue **Espion express** , la fenêtre **Espion** ou la fenêtre **Exécution** . Les évaluateurs d’expression travaillent également dans la fenêtre **Points d’arrêt** et à beaucoup d’autres emplacements du débogueur.  
  
 Les sections suivantes fournissent plus d’informations sur les expressions dans différents langages.  
  
## <a name="f-expressions-are-not-supported"></a>Les expressions F# ne sont pas prises en charge.  
 Les expressions F# ne sont pas reconnues Si vous déboguez du code F#, vous devez traduire vos expressions en syntaxe C# avant d’introduire les expressions dans une boîte de dialogue ou fenêtre de débogueur. Quand vous traduisez des expressions de F# en C#, gardez à l’esprit que C# utilise l’opérateur `==` pour tester l’égalité, tandis que F# utilise un seul `=`.  
  
## <a name="c-expressions"></a>Expressions en C++  
 Pour plus d’informations sur l’utilisation des opérateurs de contexte avec des expressions en C++, consultez [Context Operator (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>Expressions non prises en charge en C++  
  
#### <a name="constructors-destructors-and-conversions"></a>Constructeurs, destructeurs et conversions  
 Vous ne pouvez pas appeler un constructeur ni un destructeur pour un objet, explicitement ou implicitement. Par exemple, l’expression suivante appelle explicitement un constructeur et est à l’origine d’un message d’erreur :  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Vous ne pouvez pas appeler une fonction de conversion si la destination de la conversion est une classe. Une telle conversion entraîne la construction d’un objet. Par exemple, si `myFraction` est une instance de `CFraction`, qui définit l’opérateur de fonction de conversion `FixedPoint`, l’expression suivante génère une erreur :  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 Vous ne pouvez pas appeler l’opérateur new ou delete. Par exemple, l’expression suivante n’est pas prise en charge :  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Macros de préprocesseur  
 Les macros de préprocesseur ne sont pas prises en charge dans le débogueur. Par exemple, si une constante `VALUE` est déclarée en tant que `#define VALUE 3`, vous ne pouvez pas utiliser `VALUE` dans la fenêtre **Espion** . Pour éviter cette limitation, vous devez remplacer les éléments `#define`par des énumérations et des fonctions chaque fois que possible.  
  
### <a name="using-namespace-declarations"></a>Déclarations d’espaces de noms using  
 Vous ne pouvez pas utiliser de déclarations `using namespace` .  Pour accéder à un nom de type ou une variable en dehors de l’espace de noms actuel, vous devez utiliser le nom qualifié complet.  
  
### <a name="anonymous-namespaces"></a>Espaces de noms anonymes  
 Les espaces de noms anonymes ne sont pas pris en charge. Si vous avez le code suivant, vous ne pouvez pas ajouter `test` à la fenêtre Espion :  
  
```cpp  
namespace mars   
{   
    namespace  
    {  
        int test = 0;   
    }   
}   
int main()   
{   
    // Adding a watch on test does not work.   
    mars::test++;   
    return 0;   
}  
  
```  
  
###  <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Utilisation de fonctions intrinsèques du débogueur pour maintenir l’état  
 Les fonctions intrinsèques du débogueur vous permettent d’appeler certaines fonctions C/C++ dans les expressions sans modifier l’état de l’application.  
  
 Fonctions intrinsèques du débogueur :  
  
-   Garanties comme sécurisées : l’exécution d’une fonction intrinsèque du débogueur n’endommagera pas le processus qui est en cours de débogage.  
  
-   Autorisées dans toutes les expressions, même dans les scénarios où les effets secondaires et l’évaluation de fonction ne sont pas autorisés.  
  
-   Fonctionnent dans les scénarios où les appels de fonction normaux sont impossibles, tels que le débogage d’un minidump.  
  
 Les fonctions intrinsèques du débogueur peuvent également rendre l’évaluation des expressions plus pratique. Par exemple, il est beaucoup plus facile d’écrire `strncmp(str, “asd”)` dans une condition de point d’arrêt que `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`. )  
  
|Domaine|Fonctions intrinsèques|  
|----------|-------------------------|  
|**Longueur de la chaîne**|strlen, wcslen, strnlen, wcsnlen|  
|**Comparaison de chaînes**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Recherche de chaîne**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Ces fonctions requièrent que le processus en cours de débogage s’exécute sur Windows 8. Le débogage des fichiers dump générés à partir d’un appareil Windows 8 requiert également que l’ordinateur Visual Studio exécute Windows 8. Toutefois, si vous déboguez un appareil Windows 8 à distance, l’ordinateur Visual Studio peut exécuter Windows 7.|  
|**Divers**|__log2<br /><br /> Retourne le logarithme base 2 d’un entier spécifié, arrondi à l’entier inférieur le plus proche.|  
  
## <a name="ccli---unsupported-expressions"></a>Expressions non prises en charge en C++/CLI  
  
-   Les casts qui utilisent des pointeurs, ou casts définis par l’utilisateur, ne sont pas pris en charge.  
  
-   La comparaison et l’assignation d’objet ne sont pas prises en charge.  
  
-   Les opérateurs surchargés et les fonctions surchargées ne sont pas pris en charge.  
  
-   La conversion boxing et unboxing n’est pas prise en charge.  
  
-   L’opérateur`Sizeof` n’est pas pris en charge.  
  
## <a name="c---unsupported-expressions"></a>Expressions non prises en charge en C#  
  
### <a name="dynamic-objects"></a>Objets dynamiques  
 Vous pouvez utiliser des variables dans les expressions du débogueur qui sont typées statiquement comme dynamiques. Lorsque des objets qui implémentent le <xref:System.Dynamic.IDynamicMetaObjectProvider> sont évalués dans la fenêtre Espion, un nœud Affichage dynamique est ajouté. Le nœud Affichage dynamique affiche les membres de l’objet, mais n’autorise pas la modification des valeurs des membres.  
  
 Les fonctionnalités suivantes des objets dynamiques ne sont pas prises en charge :  
  
-   Opérateurs composés `+=`, `-=`, `%=`, `/=`et `*=`  
  
-   De nombreux casts, notamment les casts numériques et casts d’argument de type  
  
-   Appels de méthode avec plus de deux arguments  
  
-   Accesseurs Get de propriété comportant plus de deux arguments  
  
-   Accesseurs Set de propriété comportant des arguments  
  
-   Assignation à un indexeur  
  
-   Opérateurs booléens `&&` et `||`  
  
### <a name="anonymous-methods"></a>Méthodes anonymes  
 La création de méthodes anonymes n’est pas prise en charge.  
  
## <a name="visual-basic---unsupported-expressions"></a>Expressions non prises en charge en Visual Basic  
  
### <a name="dynamic-objects"></a>Objets dynamiques  
 Vous pouvez utiliser des variables dans les expressions du débogueur qui sont typées statiquement comme dynamiques. Lorsque des objets qui implémentent le <xref:System.Dynamic.IDynamicMetaObjectProvider> sont évalués dans la fenêtre Espion, un nœud Affichage dynamique est ajouté. Le nœud Affichage dynamique affiche les membres de l’objet, mais n’autorise pas la modification des valeurs des membres.  
  
 Les fonctionnalités suivantes des objets dynamiques ne sont pas prises en charge :  
  
-   Opérateurs composés `+=`, `-=`, `%=`, `/=`et `*=`  
  
-   De nombreux casts, notamment les casts numériques et casts d’argument de type  
  
-   Appels de méthode avec plus de deux arguments  
  
-   Accesseurs Get de propriété comportant plus de deux arguments  
  
-   Accesseurs Set de propriété comportant des arguments  
  
-   Assignation à un indexeur  
  
-   Opérateurs booléens `&&` et `||`  
  
### <a name="local-constants"></a>Constantes locales  
 Les constantes locales ne sont pas prises en charge.  
  
### <a name="import-aliases"></a>Alias d’importation  
 Les alias d’importation ne sont pas pris en charge.  
  
### <a name="variable-declarations"></a>Déclarations de variable  
 Vous ne pouvez pas déclarer de nouvelles variables explicites dans les fenêtres du débogueur. Toutefois, vous pouvez assigner de nouvelles variables implicites dans la fenêtre **Exécution** . La portée de ces variables implicites est celle de la session de débogage. Elles ne sont pas accessibles à l’extérieur du débogueur. Par exemple, l’instruction `o = 5` crée implicitement une variable `o` et lui assigne la valeur 5. De telles variables implicites sont de type **objet** , sauf si le type peut être déduit par le débogueur.  
  
### <a name="unsupported-keywords"></a>Mots clés non pris en charge  
  
-   `AddressOf`  
  
-   `End`  
  
-   `Error`  
  
-   `Exit`  
  
-   `Goto`  
  
-   `On Error`  
  
-   `Resume`  
  
-   `Return`  
  
-   `Select/Case`  
  
-   `Stop`  
  
-   `SyncLock`  
  
-   `Throw`  
  
-   `Try/Catch/Finally`  
  
-   `With`  
  
-   Mots clés de niveau espace de noms ou module, comme `End Sub` ou `Module`.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécificateurs de format en C++](../debugger/format-specifiers-in-cpp.md)   
 [Opérateur de contexte (C++)](../debugger/context-operator-cpp.md)   
 [Spécificateurs de format en c#](../debugger/format-specifiers-in-csharp.md)   
 [Pseudo-variables](../debugger/pseudovariables.md)





