---
title: Référence des vérificateurs C++ Core Guidelines
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 2c3e1ba77f3f78de3fc1fac4185121ecb42b1b5b
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271386"
---
# <a name="c-core-guidelines-checker-reference"></a>Référence des vérificateurs C++ Core Guidelines

Cette section répertorie les avertissements de l’outil de vérification des recommandations C++ Core. Pour plus d’informations sur l’analyse du code, consultez [/Analyze (analyse du code)](/cpp/build/reference/analyze-code-analysis) et [démarrage rapide :C++analyse du code pour C/](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Certains avertissements appartiennent à plusieurs groupes, et pas tous les avertissements sont marqués d’une rubrique de référence complète.

## <a name="owner_pointer-group"></a>Groupe de OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) Retourne un objet de portée à la place d’un segment de mémoire alloué s’il a un constructeur de déplacement. Consultez [ C++ instructions principales R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) Réinitialiser ou supprimer explicitement un\<propriétaire T > pointeur'% variable% '. Consultez [ C++ instructions principales R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) Ne supprimez pas un propriétaire\<T > qui peut être dans un État non valide. Consultez [ C++ instructions principales R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) N’attribuez pas à un propriétaire\<T > qui peut être dans un état valide. Consultez [ C++ instructions principales R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) N’assignez pas un pointeur brut à un propriétaire\<T >. Consultez [ C++ instructions principales R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) Préférer les objets délimités, pas de tas-Allocate inutilement. Consultez [ C++ instructions principales R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) Le symbole'% Symbol% 'n’est jamais testé pour la valeur null, il peut être marqué comme not_null. Consultez [ C++ les principales instructions F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Le symbole'% Symbol% 'n’a pas été testé pour la valeur NULL sur tous les chemins d’accès. Consultez [ C++ les principales instructions F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) Le type de l’expression'% expr% 'est déjà GSL :: not_null. Ne testez pas pour valeur null. Consultez [ C++ les principales instructions F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>Groupe de RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) N’assignez pas le résultat d’une allocation ou d’un appel de fonction avec un propriétaire\<T > valeur de retour à un pointeur brut ; Utilisez à la place le > owner\<T. Consultez [ C++ les instructions de base I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) Ne supprimez pas un pointeur brut qui n’est pas un propriétaire\<T >. Consultez [ C++ les instructions de base I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)  retourner un objet délimitée à la place d’un segment de mémoire alloué, s’il a un constructeur de déplacement. Consultez [ C++ instructions principales R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) Évitez malloc () et Free (), préférez la version nothrow de New with Delete. Consultez [ C++ instructions principales R. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) Évitez d’appeler New et Delete explicitement, utilisez std :: make_unique\<T > à la place. Consultez [ C++ les instructions principales R. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) Le symbole'% Symbol% 'n’est jamais testé pour la valeur null, il peut être marqué comme not_null. Consultez [ C++ les principales instructions F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Le symbole'% Symbol% 'n’a pas été testé pour la valeur NULL sur tous les chemins d’accès. Consultez [ C++ les principales instructions F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) Le type de l’expression'% expr% 'est déjà GSL :: not_null. Ne testez pas pour valeur null. Consultez [ C++ les principales instructions F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) N’utilisez pas l’arithmétique de pointeur. Utilisez span à la place. Consultez [ C++ principales instructions principales. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
L’expression '% expr %' : aucun groupe de DÉSINTÉGRATION de pointeur. Consultez [ C++ principales instructions principales. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>Groupe de UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) Le paramètre'% parameter% 'est une référence à `const` pointeur unique, utilisez const T * ou const T & à la place. Consultez [ C++ instructions principales R. 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) Le paramètre'% parameter% 'est une référence au pointeur unique et il n’est jamais réassigné ou réinitialisé. Utilisez T * ou T & à la place. Consultez [ C++ instructions principales R. 33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) Déplacez, copiez, réassignez ou réinitialisez un pointeur intelligent local'% Symbol% '. Consultez [ C++ instructions principales R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) Le paramètre de pointeur intelligent'% Symbol% 'est utilisé uniquement pour accéder au pointeur contenu. Utilisez T * ou T & à la place. Consultez [ C++ instructions principales R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>Groupe de SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) Déplacez, copiez, réassignez ou réinitialisez un pointeur intelligent local'% Symbol% '. Consultez [ C++ instructions principales R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) Le paramètre de pointeur intelligent'% Symbol% 'est utilisé uniquement pour accéder au pointeur contenu. Utilisez T * ou T & à la place. Consultez [ C++ instructions principales R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) Le paramètre de pointeur partagé'% Symbol% 'est passé par la référence rvalue. Passer par valeur à la place. Consultez [ C++ instructions principales R. 34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) Le paramètre de pointeur partagé'% Symbol% 'est passé par référence et n’est pas réinitialisé ou réassigné. Utilisez T * ou T & à la place. Consultez [ C++ les instructions principales R. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) Le paramètre de pointeur partagé'% Symbol% 'n’est pas copié ou déplacé. Utilisez T * ou T & à la place. Consultez [ C++ instructions principales R. 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>DÉCLARATION de groupe

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) L’initialiseur global appelle une fonction non constexpr'% Symbol% '. Consultez [ C++ les instructions de base I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) L’initialiseur global accède à l’objet extern'% Symbol% '. Consultez [ C++ les instructions de base I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) Évitez les objets sans nom avec une construction et une destruction personnalisées. Voir [es. 84 : ne pas (essayez) de déclarer une variable locale sans nom](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Groupe de classes

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) Si vous définissez ou supprimez une opération par défaut dans le type'% Symbol% ', définissez ou supprimez-les toutes. Consultez [ C++ les principales instructions C. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) La fonction'% Symbol% 'doit être marquée avec’override'. Consultez [C. 128 : les fonctions virtuelles doivent spécifier exactement une de virtuelle, override ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) La fonction'% symbol_1% 'masque une fonction non virtuelle'% symbol_2% '. Consultez [ C++ les principales instructions C. 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) La fonction'% Symbol% 'doit spécifier un seul’Virtual', 'override’ou’final'. Consultez [C. 128 : les fonctions virtuelles doivent spécifier exactement une de virtuelle, override ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

[C26436 NEED_VIRTUAL_DTOR](C26436.md) Le type'% Symbol% 'avec une fonction virtuelle a besoin d’un destructeur public virtuel ou non virtuel protégé. Consultez [ C++ les principales instructions C. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) Le destructeur de substitution ne doit pas utiliser de spécificateurs explicites’override’ou’Virtual'. Consultez [C. 128 : les fonctions virtuelles doivent spécifier exactement une de virtuelle, override ou final](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="type-group"></a>TYPE de groupe

[C26437 DONT_SLICE](C26437.md) Ne pas découper. Consultez [ C++ principales instructions es. 63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Groupe de styles

[C26438 NO_GOTO](C26438.md) Évitez les `goto`. Consultez [ C++ instructions principales es. 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Groupe de fonctions

[C26439 SPECIAL_NOEXCEPT](C26439.md) Ce genre de fonction ne peut pas être levée. Déclarez-le `noexcept`. Consultez [ C++ les principales instructions F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) La fonction'% Symbol% 'peut être déclarée `noexcept`. Consultez [ C++ les principales instructions F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) La fonction est déclarée **noexcept** mais appelle une fonction qui peut lever des exceptions.
Consultez [ C++ les instructions principales : F. 6 : Si votre fonction ne peut pas être levée, déclarez-la noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Groupe d’accès concurrentiel

[C26441 NO_UNNAMED_GUARDS](C26441.md) Les objets Guard doivent être nommés. Consultez [ C++ les principales instructions CP. 44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Groupe CONST

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) L’argument de référence'% argument% 'pour la fonction'% Function% 'peut être marqué comme `const`. Consultez [ C++ les instructions principales con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): l’argument de pointeur'% argument% 'pour la fonction'% Function% 'peut être marqué comme pointeur vers `const`. Consultez [ C++ les instructions principales con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) La valeur vers laquelle pointe'% variable% 'n’est assignée qu’une seule fois. Marquez-la comme pointeur vers `const`. Consultez [ C++ les instructions principales con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) Les éléments du tableau'% array% 'ne sont assignés qu’une seule fois, marquez les éléments `const`. Consultez [ C++ les instructions principales con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) Les valeurs pointées par les éléments du tableau'% array% 'ne sont assignées qu’une seule fois, marquez les éléments comme pointeur vers `const`. Consultez [ C++ les instructions principales con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) La variable'% variable% 'n’est assignée qu’une seule fois, marquez-la comme `const`. Consultez [ C++ les instructions principales con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) Cette fonction% function% peut être marquée `constexpr` si l’évaluation au moment de la compilation est souhaitée. Consultez [ C++ les principales instructions F. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) Cet appel de fonction% function% peut utiliser `constexpr` si l’évaluation au moment de la compilation est souhaitée. Consultez [ C++ les instructions principales con. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>TYPE de groupe

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) N’utilisez pas `const_cast` pour effectuer un cast `const`. `const_cast` n’est pas requis ; cast d’ou la volatilité n’est pas supprimée par cette conversion. Consultez [ C++ les instructions de base type. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) N’utilisez pas `static_cast` downcasts. Un cast d’un type polymorphe doit utiliser dynamic_cast. Consultez [ C++ les instructions de base type. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) N’utilisez pas `reinterpret_cast`. Un cast à partir de void * peut utiliser `static_cast`. Consultez [ C++ le type de recommandations principales. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) N’utilisez pas de `static_cast` pour les conversions arithmétiques. Utilisez des accolades, gsl::narrow_cast ou gsl::narow. Consultez [ C++ le type de recommandations principales. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) N’effectuez pas de cast entre les types pointeur où le type source et le type cible sont identiques. Consultez [ C++ le type de recommandations principales. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) N’effectuez pas de cast entre les types pointeur lorsque la conversion peut être implicite. Consultez [ C++ le type de recommandations principales. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) N’utilisez pas de casts de style de fonction. Consultez [ C++ principales instructions es. 49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) N’utilisez pas `reinterpret_cast`. Consultez [ C++ le type de recommandations principales. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) N’utilisez pas `static_cast` downcasts. Consultez [ C++ les instructions de base type. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) N’utilisez pas `const_cast` pour effectuer un cast `const`. Consultez [ C++ les instructions de base type. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) N’utilisez pas de casts de style C. Consultez [ C++ les instructions de base type. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) La variable'% variable% 'n’est pas initialisée. Initialisez toujours un objet. Consultez [ C++ les instructions de base type. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) La variable'% variable% 'n’est pas initialisée. Initialisez toujours une variable membre. Consultez [ C++ les instructions de base type. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Groupe de limites

[C26446 USE_GSL_AT](c26446.md) Préférez utiliser `gsl::at()` à la place de l’opérateur d’indice non vérifié. Consultez [ C++ principales instructions : Bounds. 4 : n’utilisez pas les fonctions et les types de bibliothèque standard qui ne sont pas des limites-Checked](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
N’utilisez pas opérations arithmétiques de pointeur. Utilisez span à la place. Consultez [ C++ principales instructions principales. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) Indexez uniquement les tableaux à l’aide d’expressions constantes. Consultez [ C++ principales instructions principales. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) La valeur% value% est en dehors des limites (0,% Bound%) de la variable'% variable% '. Uniquement des index à l’aide d’expressions constantes situées dans les limites du tableau de tableaux. Consultez [ C++ principales instructions principales. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) Expression'% expr% ' : dégradation de tableau à pointeur. Consultez [ C++ principales instructions principales. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Groupe de GSL

[C26445 NO_SPAN_REF](c26445.md) Une référence à `gsl::span` ou `std::string_view` peut indiquer un problème de durée de vie.
Consultez [ C++ les principales instructions GSL. View : views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) Préférez utiliser `gsl::at()` à la place de l’opérateur d’indice non vérifié. Consultez [ C++ principales instructions : Bounds. 4 : n’utilisez pas les fonctions et les types de bibliothèque standard qui ne sont pas des limites-Checked](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY](c26448.md) Envisagez d’utiliser `gsl::finally` si l’action finale est prévue. Consultez [ C++ les instructions principales : GSL. util : Utilities](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md)
`gsl::span` ou `std::string_view` créées à partir d’un temporaire ne sont pas valides lorsque le temporaire est invalidé. Consultez [ C++ les instructions principales : GSL. View : views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).

## <a name="deprecated-warnings"></a>Avertissements déconseillées

Les avertissements suivants sont présents dans un ensemble de règles expérimentale anticipée de l’outil de vérification d’instructions de core, mais sont désormais déconseillés et peuvent être ignorés en toute sécurité. Les avertissements sont remplacés par les avertissements dans la liste ci-dessus.

- DEREF_INVALID_POINTER 26412
- DEREF_NULLPTR 26413
- ASSIGN_NONOWNER_TO_EXPLICIT_OWNER 26420
- ASSIGN_VALID_OWNER 26421
- VALID_OWNER_LEAVING_SCOPE 26422
- ALLOCATION_NOT_ASSIGNED_TO_OWNER 26423
- VALID_ALLOCATION_LEAVING_SCOPE 26424
- ASSIGNING_TO_STATIC 26425
- NO_LIFETIME_TRACKING 26499

## <a name="see-also"></a>Voir aussi
[Utilisation des C++ contrôleurs d’instructions de base](using-the-cpp-core-guidelines-checkers.md)
