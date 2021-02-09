---
title: Expressions dans le débogueur | Microsoft Docs
description: Découvrez les expressions de langage qui ne sont pas prises en charge par les évaluateurs d’expression dans le débogueur Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cc17892697e16c24e3bb1fae5aa956123ee4e7bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870790"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Expressions dans le débogueur Visual Studio
Le débogueur Visual Studio inclut des évaluateurs d’expression qui fonctionnent lorsque vous entrez une expression dans la boîte de dialogue **Espion express** , la fenêtre **Espion** ou la fenêtre **Exécution** . Les évaluateurs d’expression travaillent également dans la fenêtre **Points d’arrêt** et à beaucoup d’autres emplacements du débogueur.

Les sections suivantes décrivent les limitations de l’évaluation des expressions pour les langages pris en charge par Visual Studio.

## <a name="f-expressions-are-not-supported"></a>Les expressions F# ne sont pas prises en charge.
Les expressions F# ne sont pas reconnues Si vous déboguez du code F#, vous devez traduire vos expressions en syntaxe C# avant d’introduire les expressions dans une boîte de dialogue ou fenêtre de débogueur. Quand vous traduisez des expressions de F# en C#, gardez à l’esprit que C# utilise l’opérateur `==` pour tester l’égalité, tandis que F# utilise un seul `=`.

## <a name="c-expressions"></a>Expressions en C++
Pour plus d’informations sur l’utilisation des opérateurs de contexte avec des expressions en C++, consultez [Context Operator (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>Expressions non prises en charge en C++

#### <a name="constructors-destructors-and-conversions"></a>Constructeurs, destructeurs et conversions
Vous ne pouvez pas appeler un constructeur ni un destructeur pour un objet, explicitement ou implicitement. Par exemple, l’expression suivante appelle explicitement un constructeur et est à l’origine d’un message d’erreur :

```C++
my_date( 2, 3, 1985 )
```

Vous ne pouvez pas appeler une fonction de conversion si la destination de la conversion est une classe. Une telle conversion entraîne la construction d’un objet. Par exemple, si `myFraction` est une instance de `CFraction`, qui définit l’opérateur de fonction de conversion `FixedPoint`, l’expression suivante génère une erreur :

```C++
(FixedPoint)myFraction
```

Vous ne pouvez pas appeler l’opérateur new ou delete. Par exemple, l’expression suivante n’est pas prise en charge :

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Macros de préprocesseur
Les macros de préprocesseur ne sont pas prises en charge dans le débogueur. Par exemple, si une constante `VALUE` est déclarée en tant que `#define VALUE 3`, vous ne pouvez pas utiliser `VALUE` dans la fenêtre **Espion** . Pour éviter cette limitation, vous devez remplacer les éléments `#define`par des énumérations et des fonctions chaque fois que possible.

### <a name="using-namespace-declarations"></a>Déclarations d’espaces de noms using
Vous ne pouvez pas utiliser de déclarations `using namespace` .  Pour accéder à un nom de type ou une variable en dehors de l’espace de noms actuel, vous devez utiliser le nom qualifié complet.

### <a name="anonymous-namespaces"></a>Espaces de noms anonymes
Les espaces de noms anonymes ne sont pas pris en charge. Si vous avez le code suivant, vous ne pouvez pas ajouter `test` à la fenêtre Espion :

```C++
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

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Utilisation de fonctions intrinsèques du débogueur pour maintenir l’État
Les fonctions intrinsèques du débogueur vous permettent d’appeler certaines fonctions C/C++ dans les expressions sans modifier l’état de l’application.

Fonctions intrinsèques du débogueur :

- Garanties comme sécurisées : l’exécution d’une fonction intrinsèque du débogueur n’endommagera pas le processus qui est en cours de débogage.

- Autorisées dans toutes les expressions, même dans les scénarios où les effets secondaires et l’évaluation de fonction ne sont pas autorisés.

- Fonctionnent dans les scénarios où les appels de fonction normaux sont impossibles, tels que le débogage d’un minidump.

  Les fonctions intrinsèques du débogueur peuvent également rendre l’évaluation des expressions plus pratique. Par exemple, il est beaucoup plus facile d’écrire `strncmp(str, "asd")` dans une condition de point d’arrêt que `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`. )

|Domaine|Fonctions intrinsèques|
|----------|-------------------------|
|**Longueur de la chaîne**|[strlen, wcslen](/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Comparaison de chaînes**|[strcmp, wcscmp](/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsicmp](/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnicmp, wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Recherche de chaîne**|[strchr, wcschr](/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy](/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy), [DecodePointer](/previous-versions/bb432242(v=vs.85)), [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace](/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [WindowsCompareStringOrdinal](/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal), [WindowsGetStringLen](/windows/win32/api/winstring/nf-winstring-windowsgetstringlen), [WindowsGetStringRawBuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Ces fonctions requièrent que le processus en cours de débogage s’exécute sur Windows 8. Le débogage des fichiers dump générés à partir d’un appareil Windows 8 requiert également que l’ordinateur Visual Studio exécute Windows 8. Toutefois, si vous déboguez un appareil Windows 8 à distance, l’ordinateur Visual Studio peut exécuter Windows 7.|
|**Divers**|__log2//retourne le logarithme base 2 d’un entier spécifié, arrondi à l’entier inférieur le plus proche.<br /><br />__findNonNull, DecodeHString, DecodeWinRTRestrictedException, DynamicCast, DynamicMemberLookup, GetEnvBlockLength<br /><br />Stdext_HashMap_Int_OperatorBracket_idx, Std_UnorderedMap_Int_OperatorBracket_idx<br /><br />ConcurrencyArray_OperatorBracket_idx//Concurrency :: Array<> :: Operator [index<>] et Operator (index<>)<br /><br />ConcurrencyArray_OperatorBracket_int//Concurrency :: Array<> ::, opérateur (int, int,...)<br /><br />ConcurrencyArray_OperatorBracket_tidx//Concurrency :: Array<> :: Operator [tiled_index<>] et Operator (tiled_index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_idx//concurrence :: array_view<> :: Operator [index<>] et Operator (index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_int//Concurrency :: array_view<> ::, opérateur (int, int,...)<br /><br />ConcurrencyArrayView_OperatorBracket_tidx//concurrence :: array_view<> :: Operator [tiled_index<>] et Operator (tiled_index<>)<br /><br />TreeTraverse_Init//Initialise une nouvelle traversée d’arborescence<br /><br />TreeTraverse_Next//retourne des nœuds dans une arborescence<br /><br />TreeTraverse_Skip//ignore les nœuds dans un parcours d’arborescence en attente'|

## <a name="ccli---unsupported-expressions"></a>Expressions non prises en charge en C++/CLI

- Les casts qui utilisent des pointeurs, ou casts définis par l’utilisateur, ne sont pas pris en charge.

- La comparaison et l’assignation d’objet ne sont pas prises en charge.

- Les opérateurs surchargés et les fonctions surchargées ne sont pas pris en charge.

- La conversion boxing et unboxing n’est pas prise en charge.

- L’opérateur`Sizeof` n’est pas pris en charge.

## <a name="c---unsupported-expressions"></a>Expressions non prises en charge en C#

### <a name="dynamic-objects"></a>Objets dynamiques
Vous pouvez utiliser des variables dans les expressions du débogueur qui sont typées statiquement comme dynamiques. Quand des objets qui implémentent <xref:System.Dynamic.IDynamicMetaObjectProvider> sont évalués dans la fenêtre Espion, un nœud d’affichage dynamique est ajouté. Le nœud Affichage dynamique affiche les membres de l’objet, mais n’autorise pas la modification des valeurs des membres.

Les fonctionnalités suivantes des objets dynamiques ne sont pas prises en charge :

- Opérateurs composés `+=`, `-=`, `%=`, `/=`et `*=`

- De nombreux casts, notamment les casts numériques et casts d’argument de type

- Appels de méthode avec plus de deux arguments

- Accesseurs Get de propriété comportant plus de deux arguments

- Accesseurs Set de propriété comportant des arguments

- Assignation à un indexeur

- Opérateurs booléens `&&` et `||`

### <a name="anonymous-methods"></a>Méthodes anonymes
La création de méthodes anonymes n’est pas prise en charge.

## <a name="visual-basic---unsupported-expressions"></a>Expressions non prises en charge en Visual Basic

### <a name="dynamic-objects"></a>Objets dynamiques
Vous pouvez utiliser des variables dans les expressions du débogueur qui sont typées statiquement comme dynamiques. Quand des objets qui implémentent l’interface <xref:System.Dynamic.IDynamicMetaObjectProvider> sont évalués dans la fenêtre Espion, un nœud Affichage dynamique est ajouté. Le nœud Affichage dynamique affiche les membres de l’objet, mais n’autorise pas la modification des valeurs des membres.

Les fonctionnalités suivantes des objets dynamiques ne sont pas prises en charge :

- Opérateurs composés `+=`, `-=`, `%=`, `/=`et `*=`

- De nombreux casts, notamment les casts numériques et casts d’argument de type

- Appels de méthode avec plus de deux arguments

- Accesseurs Get de propriété comportant plus de deux arguments

- Accesseurs Set de propriété comportant des arguments

- Assignation à un indexeur

- Opérateurs booléens `&&` et `||`

### <a name="local-constants"></a>Constantes locales
Les constantes locales ne sont pas prises en charge.

### <a name="import-aliases"></a>Alias d’importation
Les alias d’importation ne sont pas pris en charge.

### <a name="variable-declarations"></a>Déclarations de variable
Vous ne pouvez pas déclarer de nouvelles variables explicites dans les fenêtres du débogueur. Toutefois, vous pouvez assigner de nouvelles variables implicites dans la fenêtre **Exécution** . La portée de ces variables implicites est celle de la session de débogage. Elles ne sont pas accessibles à l’extérieur du débogueur. Par exemple, l’instruction `o = 5` crée implicitement une variable `o` et lui assigne la valeur 5. De telles variables implicites sont de type **objet** , sauf si le type peut être déduit par le débogueur.

### <a name="unsupported-keywords"></a>Mots clés non pris en charge

- `AddressOf`

- `End`

- `Error`

- `Exit`

- `Goto`

- `On Error`

- `Resume`

- `Return`

- `Select/Case`

- `Stop`

- `SyncLock`

- `Throw`

- `Try/Catch/Finally`

- `With`

- Mots clés de niveau espace de noms ou module, comme `End Sub` ou `Module`.

## <a name="see-also"></a>Voir aussi
- [Spécificateurs de format en C++](../debugger/format-specifiers-in-cpp.md)
- [Context, opérateur (C++)](../debugger/context-operator-cpp.md)
- [Spécificateurs de format en C #](../debugger/format-specifiers-in-csharp.md)
- [Pseudo-variables](../debugger/pseudovariables.md)