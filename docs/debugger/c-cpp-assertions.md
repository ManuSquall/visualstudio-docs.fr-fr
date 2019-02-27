---
title: Assertions C/C++ | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: c103448ae1471e2d9806a1d1cd2f8510c607f844
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628323"
---
# <a name="cc-assertions"></a>Assertions C/C++
Une instruction d’assertion spécifie une condition que vous prévoyez d’avoir la valeur true à un point dans votre programme. Si cette condition n’est pas remplie, l’assertion échoue, l’exécution de votre programme est interrompue et le [boîte de dialogue Échec de l’Assertion](../debugger/assertion-failed-dialog-box.md) s’affiche.

Visual C++ prend en charge les instructions d’assertion qui reposent sur les constructions suivantes :

- Assertions MFC pour les programmes MFC.

- [ATLASSERT ;](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) pour les programmes qui utilisent ATL.

- Assertions CRT pour les programmes qui utilisent la bibliothèque Runtime C.

- L’ANSI [la fonction d’assertion](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) pour d’autres programmes C/C++.

  Vous pouvez utiliser des assertions pour intercepter les erreurs de logique, vérifiez les résultats d’une opération et tester des conditions d’erreur qui devraient avoir été gérées.

## <a name="BKMK_In_this_topic"></a> Dans cette rubrique
[Fonctionnement des assertions](#BKMK_How_assertions_work)

[Assertions dans les versions Debug et Release](#BKMK_Assertions_in_Debug_and_Release_builds)

[Effets de l’utilisation d’assertions](#BKMK_Side_effects_of_using_assertions)

[Assertions CRT](#BKMK_CRT_assertions)

[Assertions MFC](#BKMK_MFC_assertions)

- [MFC ASSERT_VALID et CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [Limitations de AssertValid](#BKMK_Limitations_of_AssertValid)

  [À l’aide d’assertions](#BKMK_Using_assertions)

- [Interception des erreurs de logique](#BKMK_Catching_logic_errors)

- [Vérification des résultats](#BKMK_Checking_results_)

- [Erreurs de recherche non prise en charge](#BKMK_Testing_error_conditions_)

## <a name="BKMK_How_assertions_work"></a> Fonctionnement des assertions
Lorsque le débogueur s’arrête en raison d’une assertion de bibliothèque du run-time MFC ou C, puis si la source est disponible, le débogueur accède au point dans le fichier source où l’assertion s’est produite. Le message d’assertion s’affiche à la fois dans le [fenêtre sortie](../ide/reference/output-window.md) et **Échec de l’Assertion** boîte de dialogue. Vous pouvez copier le message d’assertion à partir de la **sortie** fenêtre dans une fenêtre texte si vous souhaitez l’enregistrer pour référence ultérieure. Le **sortie** fenêtre peut contenir d’autres messages d’erreur. Examinez ces messages avec précaution, car ils fournissent des indications sur la cause de l’échec d’assertion.

Utiliser des assertions pour détecter les erreurs au cours du développement. En règle générale, utilisez une assertion pour chaque hypothèse. Par exemple, si vous supposez qu’un argument n’est pas NULL, vous pouvez utiliser une assertion pour tester cette hypothèse.

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Assertions dans les versions Debug et Release
Instructions d’assertion compiler uniquement si `_DEBUG` est défini. Sinon, le compilateur traite les assertions comme des instructions null. Par conséquent, les instructions d’assertion n’imposent aucune surcharge ou de performances dans votre programme de mise en production finale des coûts et vous permettent d’éviter d’utiliser `#ifdef` directives.

## <a name="BKMK_Side_effects_of_using_assertions"></a> Effets de l’utilisation d’assertions
Lorsque vous ajoutez des assertions à votre code, assurez-vous que les assertions n’ont pas d’effets secondaires. Par exemple, considérez l’assertion suivante modifie le `nM` valeur :

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

Étant donné que le `ASSERT` expression n’est pas évaluée dans la version Release de votre programme, `nM` auront des valeurs différentes dans les versions Debug et Release. Pour éviter ce problème dans MFC, vous pouvez utiliser la [Vérifiez](/cpp/mfc/reference/diagnostic-services#verify) macro au lieu de `ASSERT`. `VERIFY` évalue l’expression dans toutes les versions, mais ne vérifie pas le résultat dans la version Release.

Veillez particulièrement sur l’utilisation d’appels de fonction dans les instructions d’assertion, car l’évaluation d’une fonction peut avoir des effets secondaires inattendus.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY` appels `myFnctn` dans les versions Debug et Release, par conséquent, il est acceptable d’utiliser. Toutefois, l’utilisation `VERIFY` impose la surcharge d’un appel de fonction inutile dans la version Release.

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="BKMK_CRT_assertions"></a> Assertions CRT
Le CRTDBG. H définit les [macros Assert et _ASSERTE](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) pour la vérification des assertions.


| Macro | Résultat |
|------------| - |
| `_ASSERT` | Si l’expression spécifiée a la valeur FALSE, le fichier nom et numéro de ligne de la `_ASSERT`. |
| `_ASSERTE` | Identique à `_ASSERT`, ainsi que d’une représentation sous forme de chaîne de l’expression qui a été déclarée. |

`_ASSERTE` est la plus puissante, car elle indique l’expression affirmée avérée pour être FALSE. Cela peut être suffisant pour identifier le problème sans faire référence au code source. Toutefois, la version Debug de votre application contiendra une constante de chaîne pour chaque expression déclaré à l’aide de `_ASSERTE`. Si vous utilisez de nombreux `_ASSERTE` macros, ces expressions de chaîne occupent une quantité importante de mémoire. Si cela pose un problème, utilisez `_ASSERT` pour économiser de la mémoire.

Lorsque `_DEBUG` est défini, le `_ASSERTE` macro est définie comme suit :

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

Si l’expression affirmée prend la valeur FALSE, [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) est appelée pour signaler l’échec d’assertion (à l’aide d’une boîte de dialogue de message par défaut). Si vous choisissez **de nouvelle tentative** dans la boîte de dialogue de message, `_CrtDbgReport` retourne 1 et `_CrtDbgBreak` appelle le débogueur via `DebugBreak`.

### <a name="checking-for-heap-corruption"></a>Vérification de l’endommagement du tas
L’exemple suivant utilise [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) pour vérifier l’altération du tas :

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>Vérification de la validité du pointeur
L’exemple suivant utilise [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) pour vérifier qu’une plage mémoire donnée est valide pour la lecture ou écriture.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

L’exemple suivant utilise [_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) pour vérifier un pointeur pointe vers la mémoire dans le tas local (le tas créé et géré par cette instance de la bibliothèque Runtime C — une DLL peut avoir sa propre instance de la bibliothèque, et Par conséquent, son propre tas, en dehors du tas de l’application). Cette assertion n’intercepte pas uniquement null ou hors limites adresses, mais également des pointeurs vers des variables statiques, des variables de pile et toute autre mémoire non locale.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>La vérification d’un bloc de mémoire
L’exemple suivant utilise [_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) pour vérifier qu’un bloc de mémoire se trouve dans le tas local et a un type de bloc valide.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="BKMK_MFC_assertions"></a> Assertions MFC
MFC définit le [ASSERT](https://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) macro pour la vérification des assertions. Il définit également la `MFC ASSERT_VALID` et `CObject::AssertValid` méthodes pour vérifier l’état interne d’un `CObject`-objet dérivé.

Si l’argument de la bibliothèque MFC `ASSERT` macro prend la valeur zéro ou false, la macro s’arrête l’exécution du programme et avertit l’utilisateur ; sinon, l’exécution se poursuit.

Lorsqu’une assertion échoue, une boîte de dialogue de message affiche le nom du fichier source et le numéro de ligne de l’assertion. Si vous choisissez de nouvelle tentative dans la boîte de dialogue zone, un appel à [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) provoque l’arrêt dans le débogueur de l’exécution. À ce stade, vous pouvez examiner la pile des appels et utiliser les autres options de débogage pour déterminer pourquoi l’assertion a échoué. Si vous avez activé [juste-à-temps débogage](../debugger/just-in-time-debugging-in-visual-studio.md)et le débogueur n’a pas déjà en cours d’exécution, la boîte de dialogue peut lancer le débogueur.

L’exemple suivant montre comment utiliser `ASSERT` pour vérifier la valeur de retour d’une fonction :

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

Vous pouvez utiliser ASSERT avec la [IsKindOf](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#iskindof) fonction pour fournir des arguments de fonction de vérification de type :

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

Le `ASSERT` macro génère pas de code dans la version Release. Si vous avez besoin évaluer l’expression dans la version Release, utilisez la [Vérifiez](https://msdn.microsoft.com/library/s8c29sw2.aspx#verify) macro au lieu d’ASSERT.

### <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID et CObject::AssertValid
Le [CObject::AssertValid](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#assertvalid) méthode fournit des vérifications à l’exécution de l’état interne d’un objet. Bien que vous n’êtes pas obligé de substituer `AssertValid` lorsque vous dérivez votre classe de `CObject`, vous pouvez rendre votre classe plus fiable en procédant comme cela. `AssertValid` doit exécuter des assertions sur toutes les variables de membre de l’objet pour vérifier qu’ils contiennent des valeurs valides. Par exemple, elle doit vérifier que les variables de membre de pointeur ne sont pas NULL.

L’exemple suivant montre comment déclarer un `AssertValid` (fonction) :

```cpp
class CPerson : public CObject
{
protected:
    CString m_strName;
    float   m_salary;
public:
#ifdef _DEBUG
    // Override
    virtual void AssertValid() const;
#endif
    // ...
};
```

Lorsque vous substituez `AssertValid`, appelez la version de la classe de base de `AssertValid` avant d’effectuer vos propres vérifications. Puis utilisez la macro ASSERT pour vérifier les membres propres à votre classe dérivée, comme illustré ici :

```cpp
#ifdef _DEBUG
void CPerson::AssertValid() const
{
    // Call inherited AssertValid first.
    CObject::AssertValid();

    // Check CPerson members...
    // Must have a name.
    ASSERT( !m_strName.IsEmpty());
    // Must have an income.
    ASSERT( m_salary > 0 );
}
#endif
```

Si une de vos variables de membre stocke des objets, vous pouvez utiliser la `ASSERT_VALID` macro pour tester leur validité interne (si leurs classes substituent `AssertValid`).

Par exemple, considérez une classe `CMyData`, qui stocke un [CObList](/cpp/mfc/reference/coblist-class) dans un de ses variables membres. Le `CObList` variable, `m_DataList`, stocke une collection de `CPerson` objets. Une déclaration abrégée de `CMyData` ressemble à ceci :

```cpp
class CMyData : public CObject
{
    // Constructor and other members ...
    protected:
        CObList* m_pDataList;
    // Other declarations ...
    public:
#ifdef _DEBUG
        // Override:
        virtual void AssertValid( ) const;
#endif
    // And so on ...
};
```

Le `AssertValid` remplacer dans `CMyData` ressemble à ceci :

```cpp
#ifdef _DEBUG
void CMyData::AssertValid( ) const
{
    // Call inherited AssertValid.
    CObject::AssertValid( );
    // Check validity of CMyData members.
    ASSERT_VALID( m_pDataList );
    // ...
}
#endif
```

`CMyData` utilise le `AssertValid` mécanisme pour tester la validité des objets stockés dans ses données membres. La substitution de `AssertValid` de `CMyData` appelle le `ASSERT_VALID` macro pour son propre membre m_pDataList.

Tests de validité ne s’arrête pas à ce niveau, car la classe `CObList` substitue également `AssertValid`. Ce remplacement effectue des tests sur l’état interne de la liste de validité supplémentaires. Par conséquent, une validité tester sur un `CMyData` objet conduit à des tests de validité supplémentaires pour les états internes de stocké `CObList` objet de liste.

Avec plus de travail, vous pouvez ajouter des tests de validité pour la `CPerson` également stockées dans la liste des objets. Vous pouvez dériver une classe `CPersonList` de `CObList` et remplacer `AssertValid`. Dans la substitution, vous appelleriez `CObject::AssertValid` , puis itérer la liste, l’appel `AssertValid` sur chaque `CPerson` objet stocké dans la liste. Le `CPerson` classe indiqué au début de cette rubrique substitue `AssertValid`.

Il s’agit d’un mécanisme puissant lorsque vous générez pour le débogage. Lorsque vous créez par la suite pour la mise en production, le mécanisme est automatiquement désactivé.

### <a name="BKMK_Limitations_of_AssertValid"></a> Limitations de AssertValid
Une assertion déclenchée indique que l’objet est sans aucun doute défectueux et l’exécution s’arrête. Toutefois, une absence d’assertion indique uniquement qu’aucun problème a été trouvé, mais n’est pas garanti que l’objet a été vérifié.

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="BKMK_Using_assertions"></a> À l’aide d’assertions

### <a name="BKMK_Catching_logic_errors"></a> Interception des erreurs de logique
Vous pouvez définir une assertion sur une condition qui doit être remplie en fonction de la logique de votre programme. L’assertion n’a aucun effet, sauf si une erreur logique se produit.

Par exemple, supposons que vous simulez des molécules de gaz dans un conteneur et la variable `numMols` représente le nombre total de molécules. Ce nombre ne peut pas être inférieure à zéro, donc vous pouvez inclure une instruction d’assertion MFC comme suit :

```cpp
ASSERT(numMols >= 0);
```

Ou vous pouvez inclure une assertion CRT comme suit :

```cpp
_ASSERT(numMols >= 0);
```

Ces instructions ne rien faire si votre programme fonctionne correctement. Si une erreur logique provoque `numMols` pour être inférieure à zéro, toutefois, l’assertion interrompt l’exécution de votre programme et peut afficher le [la boîte de dialogue Échec d’Assertion](../debugger/assertion-failed-dialog-box.md).

[Dans cette rubrique](#BKMK_In_this_topic)

### <a name="BKMK_Checking_results_"></a> Vérification des résultats
Assertions sont utiles pour les opérations dont les résultats ne sont pas évidents à partir d’un examen visuel rapide de test.

Par exemple, considérez le code suivant, qui met à jour la variable `iMols` en fonction du contenu de la liste liée désignée par `mols`:

```cpp
/* This code assumes that type has overloaded the != operator
 with const char *
It also assumes that H2O is somewhere in that linked list.
Otherwise we'll get an access violation... */
while (mols->type != "H2O")
{
    iMols += mols->num;
    mols = mols->next;
}
ASSERT(iMols<=numMols); // MFC version
_ASSERT(iMols<=numMols); // CRT version
```

Le nombre de molécules calculé par `iMols` doit toujours être inférieur ou égal au nombre total de molécules, `numMols`. L’examen visuel de la boucle n’affiche pas que cela nécessairement sera le cas, une instruction d’assertion est donc utilisée après la boucle pour tester cette condition.

[Dans cette rubrique](#BKMK_In_this_topic)

### <a name="BKMK_Testing_error_conditions_"></a> Erreurs de recherche non prise en charge
Vous pouvez utiliser des assertions pour tester les conditions d’erreur à un point dans votre code où toutes les erreurs devraient avoir été gérées. Dans l’exemple suivant, une routine graphique retourne un code d’erreur ou zéro pour la réussite.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

Si le code de gestion des erreurs fonctionne correctement, l’erreur devrait être gérée et `myErr` réinitialisé avant que l’assertion est atteinte. Si `myErr` a une autre valeur, l’assertion échoue, le programme s’arrête et le [la boîte de dialogue Échec d’Assertion](../debugger/assertion-failed-dialog-box.md) s’affiche.

Instructions d’assertion ne sont pas se substituer au code de gestion des erreurs, toutefois. L’exemple suivant montre une instruction d’assertion qui peut entraîner des problèmes dans le code de version finale :

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

Ce code s’appuie sur l’instruction d’assertion pour gérer la condition d’erreur. Par conséquent, tout code d’erreur retourné par `myGraphRoutine` sera non géré dans le code de version finale.

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="see-also"></a>Voir aussi

- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
- [Assertions dans du code managé](../debugger/assertions-in-managed-code.md)