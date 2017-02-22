---
title: "Meilleures pratiques et exemples (SAL) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Meilleures pratiques et exemples (SAL)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Voici quelques façons d'obtenir le meilleur parti du langage d'annotation du code source \(SAL\) et d'éviter des problèmes courants.  
  
## \_In\_  
 Si la fonction est censée écrire dans l'élément, utilisez `_Inout_` au lieu de `_In_`.  Ceci est particulièrement adapté en cas de conversion automatisée des anciennes macros vers des SAL.  Avant le SAL, de nombreux programmeurs utilisaient des macros comme macros\-commentaires qui ont été appelées `IN`, `OUT`, `IN_OUT`, ou des variantes de ces noms.  Bien que nous recommandions que vous convertissiez ces macros vers SAL, nous vous invitons également à être prudent lorsque vous les convertissez parce que le code peut avoir changé depuis que le prototype d'origine a été écrit et l'ancienne macro ne peut plus refléter ce que le code fait.  Soyez particulièrement prudent sur la macro de commentaire `OPTIONAL` car elle est souvent placée incorrectement, par exemple, du mauvais côté d'une virgule.  
  
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
  
## \_opt\_  
 Si l'appelant n'est pas autorisée à s'exécuter dans un pointeur null, utilisez `_In_` ou `_Out_` au lieu de `_In_opt_` ou de `_Out_opt_`.  Cela s'applique même à une fonction qui vérifie ses paramètres et retourne une erreur si elle a la valeur NULL lorsqu'elle ne doit pas l'être.  Bien qu'ayant une fonction de vérification de son paramètre pour les cas inattendus NULL et qu'un retour correct soit une bonne pratique défensive en matière de codage, il ne signifie pas que l'annotation de paramètre peut être d'un type facultatif \(\_*Xxx*\_opt\_\).  
  
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
  
## \_Pre\_defensive\_ et \_Post\_defensive\_  
 Si une fonction apparaît à la limite de l'approbation, il est recommandé d'utiliser l'annotation `_Pre_defensive_`.  Le modificateur « défensif » modifie certaines annotations pour indiquer que, au point de l'appel, l'interface doit être vérifiée strictement, mais au corps d'implémentation elle doit supposer que des paramètres incorrects puissent être passés.  Dans ce cas, `_In_ _Pre_defensive_` est préférable à une limite d'approbation pour indiquer que, même si un appelant obtient une erreur si elle tente de passer NULL, le corps de la fonction est analysé comme si le paramètre pouvait être NULL, et toute tentative de déréférence du pointeur sans l'examen préalable pour rechercher la valeur NULL sont marqués d'un indicateur.  Une annotation `_Post_defensive_` existe également pour une utilisation dans les rappels, où il est supposé que la partie approuvée est l'appelant et code non fiable correspond au code appelé.  
  
## \_Out\_writes\_  
 L'exemple suivant illustre une utilisation courante `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 L'annotation `_Out_writes_` signifie que vous avez une mémoire tampon.  Elle fait allouer des octets `cb`, avec le premier octet initialisé sur la sortie.  Cette annotation n'est pas strictement erronées et il est utile d'exprimer la taille allouée.  Toutefois, il n'indique pas le nombre d'éléments qui sont initialisés par la fonction.  
  
 Le code de l'exemple montre trois méthodes nécessaires pour entièrement spécifier la taille exacte de la partie initialisée de la mémoire tampon.  
  
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
  
## \_Out\_ PSTR  
 L'utilisation de `_Out_ PSTR` est presque toujours erronées.  Cela est interprété comme ayant un paramètre de sortie qui pointe vers une mémoire tampon de caractères et c'est NULL\-terminé.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Une annotation comme `_In_ PCSTR` est courante et utile.  Elle indique une chaîne d'entrée qui a une terminaison NULL car le précondition de `_In_` permet la reconnaissance d'une chaîne terminée par le caractère NULL.  
  
## \_In\_ WCHAR\* p  
 `_In_ WCHAR* p` signifie qu'il y a un pointeur en entrée `p` qui pointe sur un caractère.  Toutefois, dans la plupart des cas, ce n'est probablement pas la spécification qui est attendu.  À la place, ce qui est probablement attendu est la spécification d'un tableau se terminant par NULL ; pour ce faire, utilisez `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 L'oubli de la spécification approprié de la terminaison NULL est courant.  Utilisez la version appropriée `STR` pour remplacer le type, comme le montre l'exemple suivant.  
  
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
  
## \_Out\_range\_  
 Si le paramètre est un pointeur et que vous souhaitez exprimer la plage de la valeur de l'élément qui est pointé par le pointeur, utilisez `_Deref_out_range_` au lieu de `_Out_range_`.  Dans l'exemple suivant, la plage de \*pcbFilled est exprimé, pas pcbFilled.  
  
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
  
 `_Deref_out_range_(0, cbSize)` n'est pas strictement requis pour certains outils car il peut être déduit de `_Out_writes_to_(cbSize,*pcbFilled)`, mais il est indiqué ici à des fins de précision.  
  
## Contexte incorrect dans \_When\_  
 Une autre erreur courante consiste à utiliser l'évaluation postétat des préconditions.  Dans l'exemple suivant, `_Requires_lock_held_` représente une précondition.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 L'expression `result` fait référence à une valeur postétat qui n'est pas disponible en préétat.  
  
## TRUE dans \_Success\_  
 Si la fonction réussit lorsque la valeur de retour est différente de zéro, utilisez `return != 0` comme condition de succès au lieu de `return == TRUE`.  Une valeur différente de zéro ne signifie pas nécessairement l'équivalence à la valeur réelle que le compilateur fournit pour `TRUE`.  Le paramètre `_Success_` est une expression ; les expressions suivantes sont considérées comme équivalentes : `return != 0`, `return != false`, `return != FALSE`, et `return` sans paramètres ni comparaisons.  
  
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
  
## Variable de référence  
 Pour une variable de référence, la version antérieure du SAL a utilisé le pointeur implicite comme cible d'annotation et nécessitait l'ajout de `__deref` aux annotations qui se sont liées à une variable de référence.  Cette version utilise l'objet lui\-même et ne requiert pas de `_Deref_`supplémentaire.  
  
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
  
## Annotations sur les valeurs de retour  
 L'exemple suivant présente un problème fréquent dans les valeurs de retour des annotations.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 Dans cet exemple, `_Out_opt_` indique que le pointeur peut être NULL dans le cadre d'une précondition.  Toutefois, les préconditions ne peuvent pas être appliquées à la valeur de retour.  Dans ce cas, l'annotation correcte est `_Ret_maybenull_`.  
  
## Voir aussi  
 [Utilisation d’annotations SAL pour réduire les défauts du code C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation de paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)   
 [Structs et classes d’annotation](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécification du moment où une annotation est applicable et dans quel cas](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)