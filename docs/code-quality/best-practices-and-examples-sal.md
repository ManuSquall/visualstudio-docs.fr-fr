---
title: Meilleures pratiques et exemples (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: eb95e793421ecede6d4583d8d7f4730eb56df1a0
ms.sourcegitcommit: 58000baf528da220fdf7a999d8c407a4e86c1278
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72789782"
---
# <a name="best-practices-and-examples-sal"></a>Meilleures pratiques et exemples (SAL)
Voici quelques méthodes pour tirer le meilleur parti du langage SAL (code source annotation Language) et éviter certains problèmes courants.

## <a name="_in_"></a>\_In\_

Si la fonction est supposée écrire dans l’élément, utilisez `_Inout_` au lieu de `_In_`. Cela s’avère particulièrement utile en cas de conversion automatisée de macros plus anciennes en SAL. Avant SAL, de nombreux programmeurs utilisaient des macros comme commentaires, c’est-à-dire des macros nommées `IN`, `OUT`, `IN_OUT`ou des variantes de ces noms. Bien que nous vous déconseillons de convertir ces macros en SAL, nous vous invitons également à être vigilants lorsque vous les convertissez, car le code peut avoir changé depuis l’écriture du prototype d’origine et l’ancienne macro peut ne plus refléter ce que fait le code. Soyez particulièrement vigilant avec la macro de commentaire `OPTIONAL`, car elle est souvent placée de manière incorrecte, par exemple, du côté incorrect d’une virgule.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="_opt_"></a>\_opt\_

Si l’appelant n’est pas autorisé à passer un pointeur null, utilisez `_In_` ou `_Out_` au lieu de `_In_opt_` ou `_Out_opt_`. Cela s’applique même à une fonction qui vérifie ses paramètres et retourne une erreur si elle est NULL alors qu’elle ne doit pas l’être. Bien qu’une fonction vérifie son paramètre pour une valeur NULL inattendue et que le retour approprié soit une bonne pratique de codage défensive, cela ne signifie pas que l’annotation de paramètre peut être d’un type facultatif (`_*Xxx*_opt_`).

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}
```

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_\_\_ défensive et \_\_défensive

Si une fonction s’affiche dans une limite d’approbation, nous vous recommandons d’utiliser l’annotation `_Pre_defensive_`.  Le modificateur « défensive » modifie certaines annotations pour indiquer que, au moment de l’appel, l’interface doit être vérifiée strictement, mais dans le corps de l’implémentation, elle doit supposer que des paramètres incorrects peuvent être passés. Dans ce cas, `_In_ _Pre_defensive_` est préférable à une limite d’approbation pour indiquer que même si un appelant recevra une erreur s’il tente de passer la valeur NULL, le corps de la fonction sera analysé comme si le paramètre avait la valeur NULL, et toute tentative de déréférencer le pointeur sans la première la vérification de la valeur NULL sera signalée.  Une annotation `_Post_defensive_` est également disponible, pour une utilisation dans les rappels où le tiers de confiance est supposé être l’appelant et le code non fiable est le code appelé.

## <a name="_out_writes_"></a>\_\_les écritures\_

L’exemple suivant illustre une utilisation incorrecte courante de `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

L’annotation `_Out_writes_` signifie que vous disposez d’une mémoire tampon. Il a `cb` octets alloués, avec le premier octet initialisé à la sortie. Cette annotation n’est pas strictement erronée et il est utile d’exprimer la taille allouée. Toutefois, il n’indique pas le nombre d’éléments initialisés par la fonction.

L’exemple suivant montre trois méthodes correctes pour spécifier entièrement la taille exacte de la partie initialisée de la mémoire tampon.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);
```

## <a name="_out_-pstr"></a>\_\_ PSTR

L’utilisation de `_Out_ PSTR` est presque toujours incorrecte. Cela est interprété comme ayant un paramètre de sortie qui pointe vers une mémoire tampon de caractères et qui se termine par un caractère NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Une annotation comme `_In_ PCSTR` est courante et utile. Il pointe vers une chaîne d’entrée qui a une terminaison NULL, car la condition préalable de `_In_` permet la reconnaissance d’une chaîne terminée par le caractère NULL.

## <a name="_in_-wchar-p"></a>\_dans\_ WCHAR * p

`_In_ WCHAR* p` indique qu’il existe un pointeur d’entrée `p` qui pointe vers un caractère. Toutefois, dans la plupart des cas, il ne s’agit probablement pas de la spécification qui est prévue. Au lieu de cela, ce qui est probablement prévu est la spécification d’un tableau terminé par le caractère NULL ; pour ce faire, utilisez `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Il manque la spécification correcte de la terminaison NULL. Utilisez la version `STR` appropriée pour remplacer le type, comme indiqué dans l’exemple suivant.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}
```

## <a name="_out_range_"></a>\_\_plage\_

Si le paramètre est un pointeur et que vous souhaitez exprimer la plage de la valeur de l’élément vers lequel pointe le pointeur, utilisez `_Deref_out_range_` au lieu de `_Out_range_`. Dans l’exemple suivant, la plage de * pcbFilled est exprimée, et non pcbFilled.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);
```

`_Deref_out_range_(0, cbSize)` n’est pas strictement requis pour certains outils, car il peut être déduit à partir de `_Out_writes_to_(cbSize,*pcbFilled)`, mais il est affiché ici pour des raisons d’exhaustivité.

## <a name="wrong-context-in-_when_"></a>Contexte incorrect dans \_lorsque\_

Une autre erreur courante consiste à utiliser l’évaluation postérieure à l’État pour les conditions préalables. Dans l’exemple suivant, `_Requires_lock_held_` est une condition préalable.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

L’expression `result` fait référence à une valeur postérieure à l’État qui n’est pas disponible dans un état antérieur.

## <a name="true-in-_success_"></a>TRUE dans \_réussite\_

Si la fonction réussit lorsque la valeur de retour est différente de zéro, utilisez `return != 0` comme condition de réussite au lieu de `return == TRUE`. Une valeur différente de zéro ne signifie pas nécessairement l’équivalence de la valeur réelle que le compilateur fournit pour `TRUE`. Le paramètre à `_Success_` est une expression, et les expressions suivantes sont évaluées comme équivalentes : `return != 0`, `return != false`, `return != FALSE`et `return` sans paramètres ni comparaisons.

```cpp
// Incorrect
_Success_(return == TRUE) _Acquires_lock_(*lpCriticalSection)
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0) _Acquires_lock_(*lpCriticalSection)
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);
```

## <a name="reference-variable"></a>Variable de référence

Pour une variable de référence, la version précédente de SAL utilisait le pointeur implicite comme cible d’annotation et nécessitait l’ajout d’un `__deref` aux annotations attachées à une variable de référence. Cette version utilise l’objet lui-même et ne requiert pas les `_Deref_`supplémentaires.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);
```

## <a name="annotations-on-return-values"></a>Annotations sur les valeurs de retour

L’exemple suivant illustre un problème courant dans les annotations de valeur de retour.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

Dans cet exemple, `_Out_opt_` indique que le pointeur peut être NULL dans le cadre de la condition préalable. Toutefois, les conditions préalables ne peuvent pas être appliquées à la valeur de retour. Dans ce cas, l’annotation correcte est `_Ret_maybenull_`.

## <a name="see-also"></a>Voir aussi

[Utilisation d’annotations SAL pour réduire les défauts du code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[Présentation de SAL](../code-quality/understanding-sal.md)  
[Annotation des paramètres de fonction et des valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)  
[Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)  
[Annotations des structs et des classes](../code-quality/annotating-structs-and-classes.md)  
[Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)  
[Spécification du moment et de l’endroit où une annotation s’applique](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[Fonctions intrinsèques](../code-quality/intrinsic-functions.md)
