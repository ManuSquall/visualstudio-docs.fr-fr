---
title: C/C++ assertions | Microsoft Docs
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
ms.openlocfilehash: 154abe3d73fa71ac897f0442697196cd859f32bd
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72435895"
---
# <a name="cc-assertions"></a>Assertions C/C++
Une instruction d’assertion spécifie une condition qui devrait être vraie à un point de votre programme. Si cette condition n’est pas remplie, l’assertion échoue, l’exécution de votre programme est interrompue et la [boîte de dialogue échec](../debugger/assertion-failed-dialog-box.md) de l’assertion s’affiche.

Visual Studio prend C++ en charge les instructions d’assertion basées sur les constructions suivantes :

- Assertions MFC pour les programmes MFC.

- [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) pour les programmes qui utilisent ATL.

- Assertions CRT pour les programmes qui utilisent la bibliothèque Runtime C.

- La [fonction ANSI Assert](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) pour les autresC++ programmes C/.

  Vous pouvez utiliser des assertions pour intercepter des erreurs de logique, vérifier les résultats d’une opération et tester des conditions d’erreur qui auraient dû être gérées.

## <a name="BKMK_In_this_topic"></a> Dans cette rubrique
[Fonctionnement des assertions](#BKMK_How_assertions_work)

[Assertions dans les versions Debug et Release](#BKMK_Assertions_in_Debug_and_Release_builds)

[Effets secondaires de l’utilisation d’assertions](#BKMK_Side_effects_of_using_assertions)

[Assertions CRT](#BKMK_CRT_assertions)

[Assertions MFC](#BKMK_MFC_assertions)

- [MFC ASSERT_VALID et CObject :: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [Limitations de AssertValid](#BKMK_Limitations_of_AssertValid)

  [Utilisation d’assertions](#BKMK_Using_assertions)

- [Interception des erreurs de logique](#BKMK_Catching_logic_errors)

- [Vérification des résultats](#BKMK_Checking_results_)

- [Recherche d’erreurs non gérées](#BKMK_Testing_error_conditions_)

## <a name="BKMK_How_assertions_work"></a>Fonctionnement des assertions
Quand le débogueur s’arrête en raison d’une assertion de bibliothèque Runtime MFC ou C, si la source est disponible, le débogueur accède au point du fichier source où l’assertion s’est produite. Le message d’assertion s’affiche à la fois dans la [fenêtre Sortie](../ide/reference/output-window.md) et dans la boîte de dialogue échec de l' **assertion** . Vous pouvez copier le message d’assertion de la fenêtre **sortie** vers une fenêtre de texte si vous souhaitez l’enregistrer pour référence ultérieure. La fenêtre **sortie** peut également contenir d’autres messages d’erreur. Examinez attentivement ces messages, car ils fournissent des indices sur la cause de l’échec de l’assertion.

Utilisez des assertions pour détecter les erreurs au cours du développement. En règle générale, utilisez une assertion pour chaque hypothèse. Par exemple, si vous supposez qu’un argument n’est pas NULL, utilisez une assertion pour tester cette hypothèse.

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a>Assertions dans les versions Debug et Release
Les instructions d’assertion se compilent uniquement si `_DEBUG` est défini. Sinon, le compilateur traite les assertions comme des instructions null. Par conséquent, les instructions d’assertion n’imposent aucune surcharge ni aucun coût de performance dans votre programme de version finale, et vous permettent d’éviter d’utiliser des directives `#ifdef`.

## <a name="BKMK_Side_effects_of_using_assertions"></a>Effets secondaires de l’utilisation d’assertions
Lorsque vous ajoutez des assertions à votre code, assurez-vous que les assertions n’ont pas d’effets secondaires. Par exemple, considérez l’assertion suivante qui modifie la valeur `nM` :

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

Étant donné que l’expression `ASSERT` n’est pas évaluée dans la version Release de votre programme, `nM` aura des valeurs différentes dans les versions Debug et Release. Pour éviter ce problème dans MFC, vous pouvez utiliser la macro [verify](/cpp/mfc/reference/diagnostic-services#verify) au lieu de `ASSERT`. `VERIFY` évalue l’expression dans toutes les versions, mais ne vérifie pas le résultat dans la version Release.

Soyez particulièrement vigilant lors de l’utilisation d’appels de fonction dans les instructions d’assertion, car l’évaluation d’une fonction peut avoir des effets secondaires inattendus.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY` appelle `myFnctn` à la fois dans les versions Debug et Release, de sorte qu’il est acceptable d’utiliser. Toutefois, l’utilisation de `VERIFY` impose la surcharge d’un appel de fonction inutile dans la version Release.

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="BKMK_CRT_assertions"></a>Assertions CRT
CRTDBG. Fichier d’en-tête H définit les macros _ Assert [et _ ASserte](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) pour la vérification des assertions.

| Macro | Résultat |
|------------| - |
| `_ASSERT` | Si l’expression spécifiée prend la valeur FALSe, le nom de fichier et le numéro de ligne du `_ASSERT`. |
| `_ASSERTE` | Identique à `_ASSERT`, plus une représentation sous forme de chaîne de l’expression qui a été déclarée. |

`_ASSERTE` est plus puissant, car il signale l’expression déclarée qui s’est avérée fausse. Cela peut être suffisant pour identifier le problème sans faire référence au code source. Toutefois, la version Debug de votre application contient une constante de chaîne pour chaque expression déclarée à l’aide de `_ASSERTE`. Si vous utilisez plusieurs macros `_ASSERTE`, ces expressions de chaîne occupent une quantité significative de mémoire. Si cela s’avère être un problème, utilisez `_ASSERT` pour économiser de la mémoire.

Lorsque `_DEBUG` est défini, la macro `_ASSERTE` est définie comme suit :

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

Si l’expression déclarée prend la valeur FALSe, _ [CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) est appelé pour signaler l’échec de l’assertion (à l’aide d’une boîte de dialogue de message par défaut). Si vous choisissez **Réessayer** dans la boîte de dialogue de message, `_CrtDbgReport` retourne 1 et `_CrtDbgBreak` appelle le débogueur à l’aide de `DebugBreak`.

### <a name="checking-for-heap-corruption"></a>Vérification de l’altération du tas
L’exemple suivant utilise [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) pour vérifier l’altération du tas :

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>Vérification de la validité du pointeur
L’exemple suivant utilise [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) pour vérifier qu’une plage de mémoire donnée est valide pour la lecture ou l’écriture.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

L’exemple suivant utilise [_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) pour vérifier qu’un pointeur pointe vers la mémoire dans le tas local (le tas créé et géré par cette instance de la bibliothèque Runtime C). une dll peut avoir sa propre instance de la bibliothèque, et donc son propre tas, en dehors du tas de l’application). Cette assertion intercepte non seulement des adresses null ou hors limites, mais également des pointeurs vers des variables statiques, des variables de pile et toute autre mémoire non locale.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>Vérification d’un bloc de mémoire
L’exemple suivant utilise [_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) pour vérifier qu’un bloc de mémoire se trouve dans le tas local et qu’il a un type de bloc valide.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="BKMK_MFC_assertions"></a>Assertions MFC
MFC définit la macro Assert pour la vérification des [assertions](https://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) . Il définit également les méthodes `MFC ASSERT_VALID` et `CObject::AssertValid` pour vérifier l’état interne d’un objet dérivé de `CObject`.

Si l’argument de la macro MFC `ASSERT` prend la valeur zéro ou false, la macro interrompt l’exécution du programme et avertit l’utilisateur ; dans le cas contraire, l’exécution se poursuit.

En cas d’échec d’une assertion, une boîte de dialogue de message affiche le nom du fichier source et le numéro de ligne de l’assertion. Si vous choisissez réessayer dans la boîte de dialogue, un appel à [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) provoque l’arrêt de l’exécution vers le débogueur. À ce stade, vous pouvez examiner la pile des appels et utiliser d’autres fonctionnalités du débogueur pour déterminer la raison de l’échec de l’assertion. Si vous avez activé le [débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)et que le débogueur n’était pas déjà en cours d’exécution, la boîte de dialogue peut lancer le débogueur.

L’exemple suivant montre comment utiliser `ASSERT` pour vérifier la valeur de retour d’une fonction :

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

Vous pouvez utiliser Assert avec la fonction [IsKindOf](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#iskindof) pour fournir une vérification de type des arguments de fonction :

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

La macro `ASSERT` ne produit aucun code dans la version Release. Si vous devez évaluer l’expression dans la version Release, utilisez la macro [verify](https://msdn.microsoft.com/library/s8c29sw2.aspx#verify) au lieu de la méthode Assert.

### <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a>MFC ASSERT_VALID et CObject :: AssertValid
La méthode [CObject :: AssertValid](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#assertvalid) fournit des contrôles au moment de l’exécution de l’état interne d’un objet. Bien que vous n’ayez pas besoin de substituer `AssertValid` lorsque vous dérivez votre classe de `CObject`, vous pouvez rendre votre classe plus fiable en procédant ainsi. `AssertValid` doit effectuer des assertions sur toutes les variables membres de l’objet pour vérifier qu’elles contiennent des valeurs valides. Par exemple, il doit vérifier que les variables de membre de pointeur ne sont pas NULL.

L’exemple suivant montre comment déclarer une fonction `AssertValid` :

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

Lorsque vous substituez `AssertValid`, appelez la version de la classe de base de `AssertValid` avant d’effectuer vos propres vérifications. Utilisez ensuite la macro Assert pour vérifier les membres propres à votre classe dérivée, comme illustré ici :

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

Si l’une de vos variables de membre stocke des objets, vous pouvez utiliser la macro `ASSERT_VALID` pour tester leur validité interne (si leurs classes remplacent `AssertValid`).

Par exemple, considérez une classe `CMyData`, qui stocke un [CObList](/cpp/mfc/reference/coblist-class) dans l’une de ses variables membres. La variable `CObList`, `m_DataList`, stocke une collection d’objets `CPerson`. Une déclaration abrégée de `CMyData` ressemble à ceci :

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

La substitution `AssertValid` dans `CMyData` ressemble à ceci :

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

`CMyData` utilise le mécanisme `AssertValid` pour tester la validité des objets stockés dans ses membres de données. La substitution `AssertValid` de `CMyData` appelle la macro `ASSERT_VALID` pour sa propre variable membre m_pDataList.

Le test de validité ne s’arrête pas à ce niveau, car la classe `CObList` remplace également `AssertValid`. Ce remplacement effectue des tests de validité supplémentaires sur l’état interne de la liste. Ainsi, un test de validité sur un objet `CMyData` entraîne des tests de validité supplémentaires pour les États internes de l’objet de liste `CObList` stocké.

Avec un peu plus de travail, vous pouvez également ajouter des tests de validité pour les objets `CPerson` stockés dans la liste. Vous pouvez dériver une classe `CPersonList` de `CObList` et remplacer `AssertValid`. Dans la substitution, vous appelez `CObject::AssertValid`, puis itérez au sein de la liste, en appelant `AssertValid` sur chaque objet `CPerson` stocké dans la liste. La classe `CPerson` présentée au début de cette rubrique remplace déjà `AssertValid`.

Il s’agit d’un mécanisme puissant quand vous générez pour le débogage. Lorsque vous générez ensuite pour la mise en version, le mécanisme est désactivé automatiquement.

### <a name="BKMK_Limitations_of_AssertValid"></a>Limitations de AssertValid
Une assertion déclenchée indique que l’objet est incorrect et que l’exécution s’arrête. Toutefois, un manque d’assertion indique uniquement qu’aucun problème n’a été trouvé, mais il n’est pas garanti que l’objet soit correct.

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="BKMK_Using_assertions"></a>Utilisation d’assertions

### <a name="BKMK_Catching_logic_errors"></a>Interception des erreurs de logique
Vous pouvez définir une assertion sur une condition qui doit être vraie selon la logique de votre programme. L’assertion n’a aucun effet, à moins qu’une erreur logique ne se produise.

Supposons, par exemple, que vous simuliez des molécules de gaz dans un conteneur et que la variable `numMols` représente le nombre total de molécules. Ce nombre ne peut pas être inférieur à zéro. vous pouvez donc inclure une instruction d’assertion MFC telle que la suivante :

```cpp
ASSERT(numMols >= 0);
```

Vous pouvez également inclure une assertion CRT comme suit :

```cpp
_ASSERT(numMols >= 0);
```

Ces instructions ne font rien si votre programme fonctionne correctement. En cas d’erreur de logique, `numMols` est inférieur à zéro. Toutefois, l’assertion interrompt l’exécution de votre programme et affiche la [boîte de dialogue échec](../debugger/assertion-failed-dialog-box.md)de l’assertion.

[Dans cette rubrique](#BKMK_In_this_topic)

### <a name="BKMK_Checking_results_"></a>Vérification des résultats
Les assertions sont précieuses pour les opérations de test dont les résultats ne sont pas évidents à partir d’une inspection visuelle rapide.

Par exemple, considérez le code suivant, qui met à jour la variable `iMols` en fonction du contenu de la liste liée vers laquelle pointe `mols` :

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

Le nombre de molécules comptées par `iMols` doit toujours être inférieur ou égal au nombre total de molécules, `numMols`. L’inspection visuelle de la boucle n’indique pas que cela sera nécessairement le cas, de sorte qu’une instruction d’assertion est utilisée après la boucle pour tester cette condition.

[Dans cette rubrique](#BKMK_In_this_topic)

### <a name="BKMK_Testing_error_conditions_"></a>Recherche d’erreurs non gérées
Vous pouvez utiliser des assertions pour tester les conditions d’erreur à un point de votre code où des erreurs doivent être traitées. Dans l’exemple suivant, une routine graphique retourne un code d’erreur ou zéro pour la réussite.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

Si le code de gestion des erreurs fonctionne correctement, l’erreur doit être gérée et `myErr` réinitialisé à zéro pour que l’assertion soit atteinte. Si `myErr` a une autre valeur, l’assertion échoue, le programme s’arrête et la [boîte de dialogue échec](../debugger/assertion-failed-dialog-box.md) de l’assertion s’affiche.

Toutefois, les instructions d’assertion ne remplacent pas le code de gestion des erreurs. L’exemple suivant illustre une instruction d’assertion qui peut entraîner des problèmes dans le code de la version finale :

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

Ce code repose sur l’instruction d’assertion pour gérer la condition d’erreur. Par conséquent, tout code d’erreur retourné par `myGraphRoutine` sera non géré dans le code de la version finale.

[Dans cette rubrique](#BKMK_In_this_topic)

## <a name="see-also"></a>Voir aussi

- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
- [Assertions dans du code managé](../debugger/assertions-in-managed-code.md)