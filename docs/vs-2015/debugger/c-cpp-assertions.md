---
title: Assertions c-C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c26cc17d00881a72928806089a4c2880fdbce2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702341"
---
# <a name="cc-assertions"></a>Assertions C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une instruction d’assertion spécifie une condition qui devrait être vraie à un point de votre programme. Si cette condition n’est pas remplie, l’assertion échoue, l’exécution de votre programme est interrompue et la [boîte de dialogue échec](../debugger/assertion-failed-dialog-box.md) de l’assertion s’affiche.  

 Visual C++ prend en charge les instructions d’assertion basées sur les constructions suivantes :  

- Assertions MFC pour les programmes MFC.  

- [ATLASSERT](https://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3) pour les programmes qui utilisent ATL.  

- Assertions CRT pour les programmes qui utilisent la bibliothèque Runtime C.  

- La [fonction ANSI Assert](https://msdn.microsoft.com/library/a9ca031a-648b-47a6-bdf1-65fc7399dd40) pour les autres programmes C/C++.  

  Vous pouvez utiliser des assertions pour intercepter des erreurs de logique, vérifier les résultats d’une opération et tester des conditions d’erreur qui auraient dû être gérées.  

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Dans cette rubrique  
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

## <a name="how-assertions-work"></a><a name="BKMK_How_assertions_work"></a> Fonctionnement des assertions  
 Quand le débogueur s’arrête en raison d’une assertion de bibliothèque Runtime MFC ou C, si la source est disponible, le débogueur accède au point du fichier source où l’assertion s’est produite. Le message d’assertion s’affiche à la fois dans la [fenêtre Sortie](../ide/reference/output-window.md) et dans la boîte de dialogue échec de l' **assertion** . Vous pouvez copier le message d’assertion de la fenêtre **sortie** vers une fenêtre de texte si vous souhaitez l’enregistrer pour référence ultérieure. La fenêtre **sortie** peut également contenir d’autres messages d’erreur. Examinez attentivement ces messages, car ils fournissent des indices sur la cause de l’échec de l’assertion.  

 Utilisez des assertions pour détecter les erreurs au cours du développement. En règle générale, utilisez une assertion pour chaque hypothèse. Par exemple, si vous supposez qu’un argument n’est pas NULL, utilisez une assertion pour tester cette hypothèse.  

 [Dans cette rubrique](#BKMK_In_this_topic)  

## <a name="assertions-in-debug-and-release-builds"></a><a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Assertions dans les versions Debug et Release  
 Les instructions d’assertion se compilent uniquement si `_DEBUG` est défini. Sinon, le compilateur traite les assertions comme des instructions null. Par conséquent, les instructions d’assertion n’imposent aucune surcharge ni aucun coût de performance dans votre programme de version finale, et vous permettent d’éviter d’utiliser des `#ifdef` directives.  

## <a name="side-effects-of-using-assertions"></a><a name="BKMK_Side_effects_of_using_assertions"></a> Effets secondaires de l’utilisation d’assertions  
 Lorsque vous ajoutez des assertions à votre code, assurez-vous que les assertions n’ont pas d’effets secondaires. Par exemple, considérez l’assertion suivante qui modifie la `nM` valeur :  

```  
ASSERT(nM++ > 0); // Don't do this!  

```  

 Étant donné que l' `ASSERT` expression n’est pas évaluée dans la version Release de votre programme, `nM` aura des valeurs différentes dans les versions Debug et Release. Pour éviter ce problème dans MFC, vous pouvez utiliser la macro [verify](https://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) au lieu de `ASSERT` .  `VERIFY` évalue l’expression dans toutes les versions, mais ne vérifie pas le résultat dans la version Release.  

 Soyez particulièrement vigilant lors de l’utilisation d’appels de fonction dans les instructions d’assertion, car l’évaluation d’une fonction peut avoir des effets secondaires inattendus.  

```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  

 `VERIFY``myFnctn`les appels à la fois dans les versions Debug et Release, il est acceptable d’utiliser. Toutefois, l’utilisation `VERIFY` de impose la surcharge d’un appel de fonction inutile dans la version Release.  

 [Dans cette rubrique](#BKMK_In_this_topic)  

## <a name="crt-assertions"></a><a name="BKMK_CRT_assertions"></a> Assertions CRT  
 CRTDBG. Fichier d’en-tête H définit le [_ASSERT et les macros _ASSERTE](https://msdn.microsoft.com/library/e98fd2a6-7f5e-4aa8-8fe8-e93490deba36) pour la vérification des assertions.  

|   Macro    |                                             Résultats                                              |
|------------|-------------------------------------------------------------------------------------------------|
| `_ASSERT`  | Si l’expression spécifiée prend la valeur FALSe, le nom de fichier et le numéro de ligne du `_ASSERT` . |
| `_ASSERTE` |      Identique à `_ASSERT` , plus une représentation sous forme de chaîne de l’expression qui a été déclarée.       |

 `_ASSERTE` est plus puissant, car il signale l’expression déclarée qui s’est avérée fausse. Cela peut être suffisant pour identifier le problème sans faire référence au code source. Toutefois, la version Debug de votre application contient une constante de chaîne pour chaque expression déclarée à l’aide de `_ASSERTE` . Si vous utilisez `_ASSERTE` de nombreuses macros, ces expressions de chaîne occupent une quantité importante de mémoire. Si cela s’avère être un problème, utilisez `_ASSERT` pour économiser de la mémoire.  

 Lorsque `_DEBUG` est défini, la `_ASSERTE` macro est définie comme suit :  

```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  

 Si l’expression déclarée prend la valeur FALSe, [_CrtDbgReport](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) est appelé pour signaler l’échec de l’assertion (à l’aide d’une boîte de dialogue de message par défaut). Si vous choisissez **Réessayer** dans la boîte de dialogue de message, `_CrtDbgReport` retourne 1 et `_CrtDbgBreak` appelle le débogueur via `DebugBreak` .  

### <a name="checking-for-heap-corruption"></a>Vérification de l’altération du tas  
 L’exemple suivant utilise [_CrtCheckMemory](https://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765) pour vérifier l’altération du tas :  

```  
_ASSERTE(_CrtCheckMemory());  
```  

### <a name="checking-pointer-validity"></a>Vérification de la validité du pointeur  
 L’exemple suivant utilise [_CrtIsValidPointer](https://msdn.microsoft.com/library/91c35590-ea5e-450f-a15d-ad8d62ade1fa) pour vérifier qu’une plage de mémoire donnée est valide pour la lecture ou l’écriture.  

```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  

 L’exemple suivant utilise [_CrtIsValidHeapPointer](https://msdn.microsoft.com/library/caf597ce-1b05-4764-9f37-0197a982bec5) pour vérifier qu’un pointeur pointe vers la mémoire dans le tas local (le tas créé et géré par cette instance de la bibliothèque Runtime C). une dll peut avoir sa propre instance de la bibliothèque, et donc son propre tas, en dehors du tas de l’application. Cette assertion intercepte non seulement des adresses null ou hors limites, mais également des pointeurs vers des variables statiques, des variables de pile et toute autre mémoire non locale.  

```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  

### <a name="checking-a-memory-block"></a>Vérification d’un bloc de mémoire  
 L’exemple suivant utilise [_CrtIsMemoryBlock](https://msdn.microsoft.com/library/f7cbbc60-3690-4da0-a07b-68fd7f250273) pour vérifier qu’un bloc de mémoire se trouve dans le tas local et qu’il a un type de bloc valide.  

```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  

 [Dans cette rubrique](#BKMK_In_this_topic)  

## <a name="mfc-assertions"></a><a name="BKMK_MFC_assertions"></a> Assertions MFC  
 MFC définit la macro Assert pour la vérification des [assertions](https://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) . Il définit également les `MFC ASSERT_VALID` `CObject::AssertValid` méthodes et pour vérifier l’état interne d’un `CObject` objet dérivé de.  

 Si l’argument de la macro MFC prend la valeur `ASSERT` zéro ou false, la macro interrompt l’exécution du programme et avertit l’utilisateur ; dans le cas contraire, l’exécution continue.  

 En cas d’échec d’une assertion, une boîte de dialogue de message affiche le nom du fichier source et le numéro de ligne de l’assertion. Si vous choisissez réessayer dans la boîte de dialogue, un appel à [AfxDebugBreak](https://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) provoque l’arrêt de l’exécution vers le débogueur. À ce stade, vous pouvez examiner la pile des appels et utiliser d’autres fonctionnalités du débogueur pour déterminer la raison de l’échec de l’assertion. Si vous avez activé le [débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)et que le débogueur n’était pas déjà en cours d’exécution, la boîte de dialogue peut lancer le débogueur.  

 L’exemple suivant montre comment utiliser `ASSERT` pour vérifier la valeur de retour d’une fonction :  

```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  

 Vous pouvez utiliser Assert avec la fonction [IsKindOf](https://msdn.microsoft.com/library/7c87c748-b7e0-4c6d-9694-6035e62fdfd6) pour fournir une vérification de type des arguments de fonction :  

```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  

 La `ASSERT` macro ne produit aucun code dans la version Release. Si vous devez évaluer l’expression dans la version Release, utilisez la macro [verify](https://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) au lieu de la méthode Assert.  

### <a name="mfc-assert_valid-and-cobjectassertvalid"></a><a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID et CObject :: AssertValid  
 La méthode [CObject :: AssertValid](https://msdn.microsoft.com/library/534a0744-4ab6-423d-b492-b4058b3d5157) fournit des contrôles au moment de l’exécution de l’état interne d’un objet. Même si vous n’êtes pas obligé de substituer `AssertValid` lorsque vous dérivez votre classe de `CObject` , vous pouvez rendre votre classe plus fiable en procédant ainsi. `AssertValid` doit effectuer des assertions sur toutes les variables membres de l’objet pour vérifier qu’elles contiennent des valeurs valides. Par exemple, il doit vérifier que les variables de membre de pointeur ne sont pas NULL.  

 L’exemple suivant montre comment déclarer une `AssertValid` fonction :  

```  
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

 Lorsque vous substituez `AssertValid` , appelez la version de la classe de base de `AssertValid` avant d’effectuer vos propres vérifications. Utilisez ensuite la macro Assert pour vérifier les membres propres à votre classe dérivée, comme illustré ici :  

```  
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

 Si l’une de vos variables de membre stocke des objets, vous pouvez utiliser la `ASSERT_VALID` macro pour tester leur validité interne (si leurs classes remplacent `AssertValid` ).  

 Par exemple, considérez une classe `CMyData` , qui stocke une [CObList](https://msdn.microsoft.com/library/80699c93-33d8-4f8b-b8cf-7b58aeab64ca) dans l’une de ses variables membres. La `CObList` variable, `m_DataList` , stocke une collection d' `CPerson` objets. Une déclaration abrégée de `CMyData` ressemble à ceci :  

```  
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

 La `AssertValid` substitution dans `CMyData` ressemble à ceci :  

```  
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

 `CMyData` utilise le `AssertValid` mécanisme pour tester la validité des objets stockés dans ses membres de données. La substitution `AssertValid` de `CMyData` appelle la `ASSERT_VALID` macro pour sa propre m_pDataList variable membre.  

 Le test de validité ne s’arrête pas à ce niveau, car la classe `CObList` remplace également `AssertValid` . Ce remplacement effectue des tests de validité supplémentaires sur l’état interne de la liste. Ainsi, un test de validité sur un `CMyData` objet entraîne des tests de validité supplémentaires pour les États internes de l’objet de liste stocké `CObList` .  

 Avec un peu plus de travail, vous pouvez également ajouter des tests de validité pour les `CPerson` objets stockés dans la liste. Vous pouvez dériver une classe `CPersonList` de `CObList` et substituer `AssertValid` . Dans la substitution, vous appelez, puis `CObject::AssertValid` itérez au sein de la liste, en appelant `AssertValid` sur chaque `CPerson` objet stocké dans la liste. La `CPerson` classe présentée au début de cette rubrique se substitue déjà à `AssertValid` .  

 Il s’agit d’un mécanisme puissant quand vous générez pour le débogage. Lorsque vous générez ensuite pour la mise en version, le mécanisme est désactivé automatiquement.  

### <a name="limitations-of-assertvalid"></a><a name="BKMK_Limitations_of_AssertValid"></a> Limitations de AssertValid  
 Une assertion déclenchée indique que l’objet est incorrect et que l’exécution s’arrête. Toutefois, un manque d’assertion indique uniquement qu’aucun problème n’a été trouvé, mais il n’est pas garanti que l’objet soit correct.  

 [Dans cette rubrique](#BKMK_In_this_topic)  

## <a name="using-assertions"></a><a name="BKMK_Using_assertions"></a> Utilisation d’assertions  

### <a name="catching-logic-errors"></a><a name="BKMK_Catching_logic_errors"></a> Interception des erreurs de logique  
 Vous pouvez définir une assertion sur une condition qui doit être vraie selon la logique de votre programme. L’assertion n’a aucun effet, à moins qu’une erreur logique ne se produise.  

 Supposons, par exemple, que vous simuliez des molécules de gaz dans un conteneur et que la variable `numMols` représente le nombre total de molécules. Ce nombre ne peut pas être inférieur à zéro. vous pouvez donc inclure une instruction d’assertion MFC telle que la suivante :  

```  
ASSERT(numMols >= 0);  

```  

 Vous pouvez également inclure une assertion CRT comme suit :  

```  
_ASSERT(numMols >= 0);  
```  

 Ces instructions ne font rien si votre programme fonctionne correctement. Toutefois, si une erreur de logique `numMols` est inférieure à zéro, l’assertion interrompt l’exécution de votre programme et affiche la [boîte de dialogue échec](../debugger/assertion-failed-dialog-box.md)de l’assertion.  

 [Dans cette rubrique](#BKMK_In_this_topic)  

### <a name="checking-results"></a><a name="BKMK_Checking_results_"></a> Vérification des résultats  
 Les assertions sont précieuses pour les opérations de test dont les résultats ne sont pas évidents à partir d’une inspection visuelle rapide.  

 Par exemple, considérez le code suivant, qui met à jour la variable `iMols` en fonction du contenu de la liste liée vers laquelle pointe `mols` :  

```  
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

 Le nombre de molécules comptées par `iMols` doit toujours être inférieur ou égal au nombre total de molécules, `numMols` . L’inspection visuelle de la boucle n’indique pas que cela sera nécessairement le cas, de sorte qu’une instruction d’assertion est utilisée après la boucle pour tester cette condition.  

 [Dans cette rubrique](#BKMK_In_this_topic)  

### <a name="finding-unhandled-errors"></a><a name="BKMK_Testing_error_conditions_"></a> Recherche d’erreurs non gérées  
 Vous pouvez utiliser des assertions pour tester les conditions d’erreur à un point de votre code où des erreurs doivent être traitées. Dans l’exemple suivant, une routine graphique retourne un code d’erreur ou zéro pour la réussite.  

```  
myErr = myGraphRoutine(a, b);  

/* Code to handle errors and  
   reset myErr if successful */  

ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  

 Si le code de gestion des erreurs fonctionne correctement, l’erreur doit être gérée et `myErr` réinitialisée à zéro avant que l’assertion soit atteinte. Si `myErr` a une autre valeur, l’assertion échoue, le programme s’arrête et la [boîte de dialogue échec](../debugger/assertion-failed-dialog-box.md) de l’assertion s’affiche.  

 Toutefois, les instructions d’assertion ne remplacent pas le code de gestion des erreurs. L’exemple suivant illustre une instruction d’assertion qui peut entraîner des problèmes dans le code de la version finale :  

```  
myErr = myGraphRoutine(a, b);  

/* No Code to handle errors */  

ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  

 Ce code repose sur l’instruction d’assertion pour gérer la condition d’erreur. Par conséquent, tout code d’erreur retourné par `myGraphRoutine` sera non géré dans le code de la version finale.  

 [Dans cette rubrique](#BKMK_In_this_topic)  

## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage de code natif](../debugger/debugging-native-code.md)   
 [Assertions dans du code managé](../debugger/assertions-in-managed-code.md)
