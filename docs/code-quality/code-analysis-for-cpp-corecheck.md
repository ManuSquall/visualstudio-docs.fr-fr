---
title: Référence de Visual Studio C++ Core instructions vérificateur
ms.date: 03/22/2018
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 6d68ed1d7002ac0e92d3a8c3e32226cb3a38c3f0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="c-core-guidelines-checker-reference"></a>Référence de l’outil d’analyse les instructions C++ Core

Cette section répertorie les avertissements du vérificateur d’instructions C++ Core. Pour plus d’informations sur l’analyse du Code, consultez [/Analyze (analyse du Code)](/cpp/build/reference/analyze-code-analysis) et [démarrage rapide : analyse du Code pour C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Des avertissements appartiennent à plusieurs groupes, et pas tous les avertissements ont une rubrique de référence complète.

## <a name="ownerpointer-group"></a>Groupe de OWNER_POINTER

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) renvoyer un objet de portée au lieu d’un segment de mémoire allouée si elle a un constructeur de déplacement. Consultez [C++ Core instructions R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) réinitialiser ou supprimer de manière explicite un propriétaire\<T > pointeur '%variable%'. Consultez [C++ Core instructions R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) ne pas supprimer un propriétaire\<T > qui peut être dans un état non valide. Consultez [C++ Core instructions R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) n’affectez pas à un propriétaire\<T > qui peut être dans un état valide. Consultez [C++ Core instructions R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) n’affectez pas un pointeur brut à un propriétaire\<T >. Consultez [C++ Core instructions R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) préfèrent les objets avec étendue, ne segment de mémoire à allouer inutilement. Consultez [C++ Core instructions R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) symbole 'symbole %' n’est jamais testé pour absence, il peut être marqué comme not_null. Consultez [C++ Core instructions F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) symbole 'symbole %' n’est pas testé pour absence sur tous les chemins. Consultez [C++ Core instructions F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) le type d’expression « expr % » est déjà gsl::not_null. Ne testez pas pour absence. Consultez [C++ Core instructions F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="rawpointer-group"></a>Groupe de RAW_POINTER

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) n’affectez pas le résultat d’une allocation ou un appel de fonction avec un propriétaire\<T > valeur de retour à un pointeur brut ; utilisez propriétaire\<T > à la place. Consultez [C++ Core instructions I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) ne supprimez pas un pointeur brut n’est pas un propriétaire\<T >. Consultez [C++ Core instructions I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   renvoyer un objet de portée au lieu d’un segment de mémoire allouée si elle a un constructeur de déplacement. Consultez [C++ Core instructions R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) éviter malloc() et free(), préférez la version nothrow de nouveau avec la suppression. Consultez [C++ Core instructions R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) éviter d’appeler de nouveau et supprimer explicitement, utilisez std::make_unique\<T > à la place. Consultez [C++ Core instructions R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) symbole 'symbole %' n’est jamais testé pour absence, il peut être marqué comme not_null. Consultez [C++ Core instructions F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) symbole 'symbole %' n’est pas testé pour absence sur tous les chemins. Consultez [C++ Core instructions F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) le type d’expression « expr % » est déjà gsl::not_null. Ne testez pas pour absence. Consultez [C++ Core instructions F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) ne pas utiliser l’opération arithmétique de pointeur. Utilisez étendue à la place. Consultez [Bounds.1 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
L’expression 'expr %' : aucun tableau pour l’atténuation de pointeur. Consultez [Bounds.3 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="uniquepointer-group"></a>Groupe de UNIQUE_POINTER

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) le paramètre « paramètre % » est une référence à `const` pointeur unique, utiliser const T * ou const T & à la place. Consultez [C++ Core instructions R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) le paramètre « paramètre % » est une référence au pointeur unique et il n’est jamais réaffecté ou réinitialisé, utilisez T * ou T & à la place. Consultez [C++ Core instructions R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) déplacer, copier, réaffecter ou réinitialiser un pointeur intelligent local '% symbole %'. Consultez [C++ Core instructions R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) le paramètre de pointeur intelligent « symbole % » est utilisé uniquement pour accéder aux contenus de pointeur. Utilisez T * ou T & à la place. Consultez [C++ Core instructions R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="sharedpointer-group"></a>Groupe de SHARED_POINTER

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) déplacer, copier, réaffecter ou réinitialiser un pointeur intelligent local '% symbole %'. Consultez [C++ Core instructions R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) le paramètre de pointeur intelligent « symbole % » est utilisé uniquement pour accéder aux contenus de pointeur. Utilisez T * ou T & à la place. Consultez [C++ Core instructions R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) le paramètre de pointeur partagé « symbole % » est passé par référence rvalue. Passer par valeur à la place. Consultez [C++ Core instructions R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) paramètre de pointeur partagé « symbole % » est passé par référence et pas réinitialiser ou réaffecté. Utilisez T * ou T & à la place. Consultez [C++ Core instructions R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) le paramètre de pointeur partagé 'symbole %' n’est pas copié ou déplacé. Utilisez T * ou T & à la place. Consultez [C++ Core instructions R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>DÉCLARATION de groupe

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) initialiseur Global appelle une fonction n’est pas constexpr 'symbole %'. Consultez [C++ Core instructions I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) initialiseur Global accède à l’objet extern « symbole % ». Consultez [C++ Core instructions I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) Évitez sans nom des objets avec la construction personnalisée et la destruction. Consultez [ES.84 : ne pas (tentez) déclarer une variable locale sans nom](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>CLASSE de groupe

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) si vous définissez ou supprimez toute opération par défaut dans le type '% symbole %', définir ou voulez-vous les supprimer. Consultez [C++ Core instructions C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) fonction '% symbole %' doit être marquée avec 'override'. Consultez [C.128 : fonctions virtuelles doivent spécifier un seul finale ou virtuelle, override,](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) fonction '% symbol_1 %' masque une fonction non virtuelle '% symbol_2 %'. Consultez [C++ Core instructions C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) fonction « symbole % » doit spécifier un seul de 'virtual', 'override' ou 'final'. Consultez [C.128 : fonctions virtuelles doivent spécifier un seul finale ou virtuelle, override,](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


[C26436 NEED_VIRTUAL_DTOR](C26436.md) le type '% symbole % avec une fonction virtuelle a besoin d’un destructeur non virtuel public virtuel ou protégé. Consultez [C++ Core instructions C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) destructeur de remplacement ne devez pas utiliser explicite 'substitution' ou 'virtual' spécificateurs. Consultez [C.128 : fonctions virtuelles doivent spécifier un seul finale ou virtuelle, override,](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>TYPE de groupe

[C26437 DONT_SLICE](C26437.md) ne pas découper. Consultez [C++ Core instructions ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Groupe de styles

[C26438 NO_GOTO](C26438.md) éviter `goto`. Consultez [C++ Core instructions ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Groupe de fonctions

[C26439 SPECIAL_NOEXCEPT](C26439.md) ce type de fonction ne peut pas lever. Déclarer `noexcept`. Consultez [C++ Core instructions F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) fonction '% symbole %' peut être déclarée `noexcept`. Consultez [C++ Core instructions F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) la fonction est déclarée **noexcept** mais appelle une fonction qui peut lever des exceptions.
Consultez [C++ principales recommandations : F.6 : Si votre fonction ne peut pas lever, déclarez-le noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Groupe d’accès concurrentiel

[C26441 NO_UNNAMED_GUARDS](C26441.md) les objets de protection doivent être nommés. Consultez [C++ de base des recommandations cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>Groupe CONST

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) l’argument de référence '% argument %' pour la fonction 'fonction %' peut être marquée comme `const`. Consultez [C++ de base des recommandations con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): l’argument de pointeur 'argument %' pour la fonction 'fonction %' peut être marquée comme un pointeur vers `const`. Consultez [C++ de base des recommandations con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) la valeur pointée par '%variable%' attribuée qu’une seule fois, la marquer comme étant un pointeur vers `const`. Consultez [C++ de base des recommandations con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) les éléments du tableau 'tableau %' assignés qu’une seule fois, les éléments de marque `const`. Consultez [C++ de base des recommandations con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) les valeurs désignées par des éléments du tableau 'tableau %' sont affectées qu’une seule fois, marque les éléments comme pointeur vers `const`. Consultez [C++ de base des recommandations con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) la variable 'variable %' attribuée qu’une seule fois, marquez-le comme `const`. Consultez [C++ de base des recommandations con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) cet fonction % de fonction peut être marqué `constexpr` si vous le souhaitez évaluation au moment de la compilation. Consultez [C++ Core instructions F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) cet fonction fonction appel % peut utiliser `constexpr` si vous le souhaitez évaluation au moment de la compilation. Consultez [C++ de base des recommandations con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>TYPE de groupe

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) n’utilisez pas `const_cast` pour caster `const`. `const_cast` n’est pas obligatoire ; constness ou la volatilité n'est pas supprimée par cette conversion. Consultez [Type.3 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) n’utilisez pas `static_cast` downcasts. Un cast d’un type polymorphe doit utiliser dynamic_cast. Consultez [Type.2 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) n’utilisez pas `reinterpret_cast`. Un cast de void * peut utiliser `static_cast`. Consultez [Type.1 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) n’utilisez pas un `static_cast` pour les conversions arithmétiques. Utiliser des accolades, gsl::narrow_cast ou gsl::narow. Consultez [Type.1 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) ne pas effectuer un cast entre types pointeur où le type source et le type de cible sont identiques. Consultez [Type.1 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) ne pas effectuer un cast entre types pointeur lorsque la conversion peut être implicite. Consultez [Type.1 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) n’utilisez pas de style de la fonction C-casts. Consultez [C++ Core instructions ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md) n’utilisez pas `reinterpret_cast`. Consultez [Type.1 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) n’utilisez pas `static_cast` downcasts. Consultez [Type.2 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) n’utilisez pas `const_cast` pour caster `const`. Consultez [Type.3 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) ne pas utiliser de casts de style C. Consultez [Type.4 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md) Variable 'variable %' n’est pas initialisée. Toujours initialiser un objet. Consultez [Type.5 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) Variable 'variable %' n’est pas initialisée. Toujours initialiser une variable membre. Consultez [Type.6 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Groupe de limites

[C26446 USE_GSL_AT](c26446.md) préfèrent utiliser `gsl::at()` au lieu de l’opérateur d’indice est désactivée. Consultez [C++ principales recommandations : Bounds.4 : n’utilisez pas les types qui ne sont pas vérifiés de limites et les fonctions de bibliothèque standard](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
N’utilisez pas opération arithmétique de pointeur. Utilisez étendue à la place. Consultez [Bounds.1 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) d’index uniquement dans les tableaux à l’aide d’expressions constantes. Consultez [Bounds.2 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) valeur % de valeur est en dehors des limites (0, liée %) de la variable « variable % ». Uniquement les index dans les tableaux à l’aide d’expressions de constante qui se trouvent dans les limites du tableau. Consultez [Bounds.2 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) Expression 'expr %' : aucun tableau pour l’atténuation de pointeur. Consultez [Bounds.3 des instructions C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>Groupe de GSL

[C26445 NO_SPAN_REF](c26445.md) une référence à `gsl::span` ou `std::string_view` peut indiquer un problème de durée de vie.
Consultez [C++ Core instructions GSL.view : vues](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) préfèrent utiliser `gsl::at()` au lieu de l’opérateur d’indice est désactivée. Consultez [C++ principales recommandations : Bounds.4 : n’utilisez pas les types qui ne sont pas vérifiés de limites et les fonctions de bibliothèque standard](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY ](c26448.md) utilisez `gsl::finally` si la dernière action est destinée. Consultez [C++ principales recommandations : GSL.util : utilitaires](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` ou `std::string_view` créé à partir d’une valeur temporaire n’est pas valide lorsque la fichier temporaire est invalidée. Consultez [C++ principales recommandations : GSL.view : vues](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).


## <a name="deprecated-warnings"></a>Avertissements déconseillées

Les avertissements suivants sont présents dans un ensemble de règles d’expérimentale anticipée de l’outil d’analyse des recommandations principales, mais sont désormais déconseillées et peuvent être ignorés en toute sécurité. Les avertissements sont remplacés par les avertissements dans la liste ci-dessus.

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
[À l’aide des outils d’analyse de recommandations C++ Core](using-the-cpp-core-guidelines-checkers.md)
