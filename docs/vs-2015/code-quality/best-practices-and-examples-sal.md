---
title: Meilleures pratiques et exemples (SAL) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 14
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9391be90516dcd7549124d7992777fd52d3134d2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508495"
---
# <a name="best-practices-and-examples-sal"></a>Meilleures pratiques et exemples (SAL)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [meilleures pratiques et exemples (SAL)](https://docs.microsoft.com/visualstudio/code-quality/best-practices-and-examples-sal).  
  
Voici quelques méthodes permettant de tirer le meilleur hors de la langue Annotation du Code Source (SAL) et éviter certains problèmes courants.  
  
## <a name="in"></a>_In\_  
 Si la fonction est censée pour écrire à l’élément, utilisez `_Inout_` au lieu de `_In_`. Cela est particulièrement utile en cas de conversion automatique à partir des anciennes macros, à SAL. Avant de SAL, les programmeurs utilisaient des macros sous forme de commentaires, macros qui étaient nommés `IN`, `OUT`, `IN_OUT`, ou des variantes de ces noms. Bien que nous vous conseillons de convertir ces macros à SAL, nous également vous recommande d’être prudent lorsque vous les convertissez, car le code peut ont été modifiés depuis le prototype d’origine a été écrite et l’ancienne macro peut ne plus refléter ce que fait le code. Soyez particulièrement vigilant le `OPTIONAL` macro de commentaire, car il est fréquemment placé de manière incorrecte, par exemple, sur l’autre côté d’une virgule.  
  
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
  
## <a name="opt"></a>_opt\_  
 Si l’appelant n’est pas autorisé à passer un pointeur null, utilisez `_In_` ou `_Out_` au lieu de `_In_opt_` ou `_Out_opt_`. Cela s’applique même à une fonction qui vérifie ses paramètres et retourne une erreur si elle a la valeur NULL lorsqu’il ne doit pas être. Bien qu’une fonction recherchez son paramètre une valeur NULL inattendue et revenir normalement est une bonne pratique de codage défensive, cela ne signifie pas que l’annotation du paramètre peut être d’un type facultatif (_*Xxx*_opt\_).  
  
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
  
## <a name="predefensive-and-postdefensive"></a>_Pre_defensive\_ et _Post_defensive\_  
 Si une fonction s’affiche sur une limite d’approbation, nous vous recommandons d’utiliser le `_Pre_defensive_` annotation.  Le modificateur « défensif » modifie certaines annotations pour indiquer que, au moment de l’appel, l’interface doit être strictement vérifiée, mais dans le corps de l’implémentation, il doit supposer que les paramètres incorrects peuvent être passés. Dans ce cas, `_In_ _Pre_defensive_` est préférable à une limite d’approbation pour indiquer que, bien que l’appelant obtiendra une erreur si elle tente de passer la valeur NULL, le corps de fonction est analysé comme si le paramètre peut être NULL et toute tentative de suppression de la référence du pointeur sans d’abord vérifier l’absence de valeur NULL sera signalé.  Un `_Post_defensive_` annotation est également disponible pour une utilisation dans les rappels où la partie de confiance est supposée pour être l’appelant et le code non fiable est le code appelé.  
  
## <a name="outwrites"></a>_Out_writes\_  
 L’exemple suivant montre une utilisation abusive courantes de `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 L’annotation `_Out_writes_` signifie que vous disposez d’une mémoire tampon. Il a `cb` octets alloués par le premier octet initialisé à la sortie. Cette annotation n’est pas strictement incorrecte et il est utile exprimer la taille allouée. Toutefois, elle n’indique pas le nombre d’éléments est initialisé par la fonction.  
  
 L’exemple suivant montre trois façons correctes pour spécifier complètement la taille exacte de la partie initialisée de la mémoire tampon.  
  
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
  
## <a name="out-pstr"></a>_Out\_ PSTR  
 L’utilisation de `_Out_ PSTR` est quasiment toujours incorrect. Ceci est interprété comme ayant un paramètre de sortie qui pointe vers une mémoire tampon de caractères et il est nul.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Comme une annotation `_In_ PCSTR` est commun et utile. Il pointe vers une chaîne d’entrée qui a de fin NULL, car la condition préalable de `_In_` permet la reconnaissance d’une chaîne se terminant par NULL.  
  
## <a name="in-wchar-p"></a>_In\_ WCHAR * p  
 `_In_ WCHAR* p` Indique qu’il existe un pointeur d’entrée `p` qui pointe vers un seul caractère. Toutefois, dans la plupart des cas, cela n’est probablement pas la spécification est destinée. Au lieu de cela, ce qui est probablement prévu est la spécification d’un tableau se terminant par NULL ; Pour cela, utilisez `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 Il est courant de la spécification correcte de fin NULL manquante. Utilisez la commande appropriée `STR` version pour remplacer le type, comme illustré dans l’exemple suivant.  
  
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
  
## <a name="outrange"></a>_Out_range\_  
 Si le paramètre est un pointeur et que vous souhaitez exprimer la plage de la valeur de l’élément qui est désignée par le pointeur, utilisez `_Deref_out_range_` au lieu de `_Out_range_`. Dans l’exemple suivant, la plage de * pcbFilled est exprimée, pcbFilled pas.  
  
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
  
 `_Deref_out_range_(0, cbSize)` n’est pas strictement obligatoire pour certains outils, car il peut être déduit à partir de `_Out_writes_to_(cbSize,*pcbFilled)`, mais il est affiché ici par souci d’exhaustivité.  
  
## <a name="wrong-context-in-when"></a>Contexte incorrect dans _quand\_  
 Une autre erreur fréquente consiste à utiliser l’évaluation de l’état après les conditions préalables. Dans l’exemple suivant, `_Requires_lock_held_` est une condition préalable.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 L’expression `result` fait référence à une valeur après l’état qui n’est pas disponible dans un état préalable.  
  
## <a name="true-in-success"></a>TRUE dans _Success\_  
 Si la fonction réussit lorsque la valeur de retour est différent de zéro, utilisez `return != 0` en tant que la condition de réussite à la place de `return == TRUE`. Valeur différente de zéro ne signifie pas nécessairement équivalence à la valeur réelle que le compilateur fournit pour `TRUE`. Le paramètre `_Success_` est une expression, et les expressions suivantes sont évaluées comme équivalents : `return != 0`, `return != false`, `return != FALSE`, et `return` sans paramètres ou les comparaisons.  
  
```cpp  
  
// Incorrect  
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
// Correct  
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))  
BOOL WINAPI TryEnterCriticalSection(  
  _Inout_ LPCRITICAL_SECTION lpCriticalSection  
);  
  
```  
  
## <a name="reference-variable"></a>Variable de référence  
 Pour une variable de référence, la version précédente de SAL utilisé le pointeur implicite comme la cible de l’annotation et requis de l’ajout d’un `__deref` aux annotations attaché à une variable de référence. Cette version utilise l’objet lui-même et ne nécessite pas supplémentaires `_Deref_`.  
  
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
 L’exemple suivant montre un problème courant dans les annotations de valeur de retour.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 Dans cet exemple, `_Out_opt_` indique que le pointeur peut être NULL dans le cadre de la condition préalable. Toutefois, les conditions préalables ne peut pas être appliqués à la valeur de retour. Dans ce cas, l’annotation correcte est `_Ret_maybenull_`.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation des paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)   
 [Annoter les Classes et Structs](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécifiant le moment où une Annotation est applicable et](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)



