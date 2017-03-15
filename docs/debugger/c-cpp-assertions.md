---
title: "Assertions C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "_DEBUG (macro)"
  - "ASSERT (macro)"
  - "Échec de l'assertion (boîte de dialogue)"
  - "assertions"
  - "assertions, effets secondaires"
  - "Pile des appels (fenêtre), échecs d'assertion"
  - "déboguer (C++), assertions"
  - "déboguer (MFC), assertions"
  - "erreurs (C++), intercepter à l'aide d'assertions"
  - "échecs, rechercher des emplacements"
  - "vérifier les résultats"
  - "résultats, vérifier"
  - "tester, conditions d'erreur avec instructions d'assertion"
  - "VERIFY (macro)"
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Assertions C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une instruction d'assertion spécifie une condition que vous prévoyez d'avoir la valeur true à un point dans votre programme.  Si cette condition n'est pas vraie, l'assertion échoue, l'exécution de votre programme est interrompue et le  [boîte de dialogue Échec de l'Assertion](../debugger/assertion-failed-dialog-box.md) s'affiche.  
  
 Visual C\+\+ prend en charge les instructions d'assertion basées sur les structures suivantes :  
  
-   Assertions MFC pour les programmes MFC.  
  
-   [ATLASSERT ;](../Topic/ATLASSERT.md) pour les programmes qui utilisent ATL.  
  
-   Assertions CRT pour les programmes qui utilisent la bibliothèque Runtime C.  
  
-   L'ANSI  [la fonction d'assertion](/visual-cpp/c-runtime-library/reference/assert-macro-assert-wassert) pour les autres programmes C\/C\+\+.  
  
 Vous pouvez utiliser des assertions pour intercepter les erreurs de logique, vérification des résultats d'une opération et Test des conditions d'erreur qui devraient avoir été gérées.  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 [Comment fonctionnent les assertions](#BKMK_How_assertions_work)  
  
 [Assertions dans les versions Debug et Release](#BKMK_Assertions_in_Debug_and_Release_builds)  
  
 [Effets secondaires de l'utilisation d'assertions](#BKMK_Side_effects_of_using_assertions)  
  
 [Assertions CRT](#BKMK_CRT_assertions)  
  
 [Assertions MFC](#BKMK_MFC_assertions)  
  
-   [MFC ASSERT_VALID et CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  
  
-   [Limitations de AssertValid](#BKMK_Limitations_of_AssertValid)  
  
 [Utilisation d'assertions](#BKMK_Using_assertions)  
  
-   [Interception des erreurs de logique](#BKMK_Catching_logic_errors)  
  
-   [Vérification des résultats](#BKMK_Checking_results_)  
  
-   [Erreurs non gérée de recherche](#BKMK_Testing_error_conditions_)  
  
##  <a name="BKMK_How_assertions_work"></a> Comment fonctionnent les assertions  
 Lorsque le débogueur s'arrête en raison d'une assertion de bibliothèque runtime MFC et C, puis si la source est disponible, le débogueur accède au point du fichier source où l'assertion a eu lieu.  Le message d'assertion apparaît à la fois dans le  [fenêtre Sortie](../ide/reference/output-window.md) et le  **Échec de l'Assertion** boîte de dialogue.  Vous pouvez copier le message d'assertion de la  **sortie** fenêtre dans une fenêtre texte si vous souhaitez enregistrer pour vous y référer ultérieurement.  Le  **sortie** fenêtre peut également contenir d'autres messages d'erreur.  Examinez ces messages attentivement, car ils fournissent des indications sur la cause de l'échec de l'assertion.  
  
 Utiliser des assertions pour détecter les erreurs au cours du développement.  En règle générale, utilisez une assertion pour chaque hypothèse.  Par exemple, si vous supposez qu'un argument n'est pas NULL, vous pouvez utiliser une assertion pour tester cette hypothèse.  
  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Assertions dans les versions Debug et Release  
 Instructions d'assertion sont compilées uniquement si  `_DEBUG`est définie.  Dans le cas contraire, le compilateur traite les assertions comme des instructions null.  Par conséquent, les instructions d'assertion n'imposent aucune surcharge ou performances de coûts dans votre programme de version finale et vous permettent d'éviter d'utiliser  `#ifdef`directives.  
  
##  <a name="BKMK_Side_effects_of_using_assertions"></a> Effets secondaires de l'utilisation d'assertions  
 Lorsque vous ajoutez des assertions à votre code, assurez\-vous que les assertions n'ont pas d'effets secondaires.  Par exemple, considérez l'assertion suivante modifie la  `nM`valeur :  
  
```  
ASSERT(nM++ > 0); // Don't do this!  
  
```  
  
 Étant donné que la  `ASSERT`expression n'est pas évaluée dans la version Release de votre programme,  `nM`auront des valeurs différentes dans les versions Debug et Release.  Pour éviter ce problème dans les MFC, vous pouvez utiliser la  [Vérifier](../Topic/VERIFY.md) macro à la place de  `ASSERT`.   `VERIFY`évalue l'expression dans toutes les versions, mais ne vérifie pas le résultat dans la version Release.  
  
 Soyez très attentif sur l'utilisation des appels de fonction dans les instructions d'assertion, car l'évaluation d'une fonction peut avoir des effets secondaires inattendus.  
  
```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  
  
 `VERIFY`appels  `myFnctn`dans les versions Debug et Release, donc il est acceptable d'utiliser.  Toutefois, l'utilisation de  `VERIFY`impose la surcharge d'un appel de fonction superflue dans la version Release.  
  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
##  <a name="BKMK_CRT_assertions"></a> Assertions CRT  
 Le CRTDBG.H définit les  [macros Assert et ASSERTE](/visual-cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) pour vérifier les assertions.  
  
|Macro|Résultat|  
|-----------|--------------|  
|`_ASSERT`|Si l'expression spécifiée prend la valeur FALSE, le fichier nom et numéro de ligne de la  `_ASSERT`.|`_ASSERTE`|  
|`_ASSERTE`|Même en tant que  `_ASSERT`, plus une représentation sous forme de chaîne de l'expression qui a été affirmée.|  
  
 `_ASSERTE`est plus puissante, car elle indique l'expression affirmée dont la valeur est FALSE.  Cela peut être suffisant pour identifier le problème sans faire référence au code source.  Toutefois, la version Debug de votre application contiendra une constante de chaîne pour chaque expression affirmée avec  `_ASSERTE`.  Si vous utilisez plusieurs  `_ASSERTE`macros, ces expressions de chaîne occupent une quantité de mémoire significative.  Si cela pose un problème, utilisez  `_ASSERT`pour économiser de la mémoire.  
  
 Lors de la  `_DEBUG`est défini, le  `_ASSERTE`macro est définie comme suit :  
  
```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  
  
 Si l'expression affirmée prend la valeur FALSE,  [\_CrtDbgReport](/visual-cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) est appelé pour signaler l'échec de l'assertion \(à l'aide d'une boîte de dialogue de message par défaut\).  Si vous choisissez  **nouvelle tentative** dans la boîte de dialogue de message,  `_CrtDbgReport`renvoie la valeur 1 et  `_CrtDbgBreak`appelle le débogueur par l'intermédiaire de   `DebugBreak`.  
  
### Vérification de l'altération du tas  
 L'exemple suivant utilise  [\_CrtCheckMemory](/visual-cpp/c-runtime-library/reference/crtcheckmemory) pour vérifier l'altération du tas :  
  
```  
_ASSERTE(_CrtCheckMemory());  
```  
  
### Vérification de la validité du pointeur  
 L'exemple suivant utilise  [\_CrtIsValidPointer](/visual-cpp/c-runtime-library/reference/crtisvalidpointer) pour vérifier qu'une plage mémoire donnée est valide pour lire ou écrire.  
  
```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  
  
 L'exemple suivant utilise  [\_CrtIsValidHeapPointer](/visual-cpp/c-runtime-library/reference/crtisvalidheappointer) pour vérifier un pointeur désigne la mémoire dans le tas local \(le tas créé et managé par cette instance de la bibliothèque Runtime C — une DLL peut avoir sa propre instance de la bibliothèque et donc son propre tas, en dehors de celui de l'application\).  Cette assertion intercepte non seulement null ou adresses hors limites, mais également des pointeurs vers des variables statiques, variables de pile et toute autre mémoire non locale.  
  
```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  
  
### Vérification d'un bloc de mémoire  
 L'exemple suivant utilise  [\_CrtIsMemoryBlock](/visual-cpp/c-runtime-library/reference/crtismemoryblock) pour vérifier qu'un bloc de mémoire dans le tas local et a un type de bloc valide.  
  
```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  
  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
##  <a name="BKMK_MFC_assertions"></a> Assertions MFC  
 Les MFC définissent la  [ASSERT](../Topic/ASSERT%20\(MFC\).md) macro pour vérifier les assertions.  Il définit également la  `MFC ASSERT_VALID`et  `CObject::AssertValid`méthodes de vérification de l'état interne d'un   `CObject`\-objet dérivé.  
  
 Si l'argument de la MFC  `ASSERT`macro correspond à zéro ou la valeur false, la macro s'arrête l'exécution du programme et avertit l'utilisateur ; dans le cas contraire, l'exécution se poursuit.  
  
 Lorsqu'une assertion échoue, une boîte de message affiche le nom du fichier source et le numéro de ligne de l'assertion.  Si vous choisissez Réessayer dans la boîte de dialogue zone, un appel à  [AfxDebugBreak](../Topic/AfxDebugBreak%20\(MFC\).md) provoque l'exécution entre dans le débogueur.  À ce stade, vous pouvez examiner la pile des appels et utiliser d'autres fonctions de débogage pour déterminer pourquoi l'assertion a échoué.  Si vous avez activé le  [le débogage juste\-à\-temps](../debugger/just-in-time-debugging-in-visual-studio.md)et que le débogueur n'était pas en cours d'exécution, la boîte de dialogue peut lancer le débogueur.  
  
 L'exemple suivant montre comment utiliser  `ASSERT`pour vérifier la valeur de retour d'une fonction :  
  
```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  
  
 Vous pouvez utiliser ASSERT avec la  [IsKindOf](../Topic/CObject::IsKindOf.md) fonction afin de fournir des arguments de la fonction de vérification de type :  
  
```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  
  
 Le  `ASSERT`macro ne génère pas de code dans la version Release.  Si vous avez besoin d'évaluer l'expression dans la version Release, utilisez la  [Vérifier](../Topic/VERIFY.md) macro au lieu de l'assertion.  
  
###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT\_VALID et CObject::AssertValid  
 Le  [CObject::AssertValid](../Topic/CObject::AssertValid.md) méthode fournit des vérifications à l'exécution de l'état interne d'un objet.  Bien que vous n'êtes pas obligé de substituer  `AssertValid`lorsque vous dérivez votre classe de   `CObject`, vous pouvez rendre votre classe plus fiable en effectuant cette opération.  `AssertValid`doit exécuter des assertions sur toutes les variables de membre de l'objet pour vérifier qu'ils contiennent des valeurs valides.  Par exemple, elle devrait vérifier que les variables de membre de pointeur ne sont pas NULL.  
  
 L'exemple suivant montre comment déclarer un  `AssertValid`fonction :  
  
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
  
 Lorsque vous substituez  `AssertValid`, appelez la version de classe de base de  `AssertValid`avant d'effectuer vos propres vérifications.  Utilisez ensuite la macro ASSERT pour vérifier les membres propres à votre classe dérivée, comme indiqué ici :  
  
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
  
 Si une de vos variables de membre stocke des objets, vous pouvez utiliser la  `ASSERT_VALID`macro pour tester leur validité interne \(si leurs classes substituent   `AssertValid`\).  
  
 Par exemple, considérez une classe  `CMyData`, qui stocke un   [CObList](/visual-cpp/mfc/reference/coblist-class) dans une de ses variables membres.  Le  `CObList`variable,   `m_DataList`, stocke une collection de  `CPerson`objets.  Une déclaration abrégée de  `CMyData`ressemble à ceci :  
  
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
  
 Le  `AssertValid`substituer dans  `CMyData`ressemble à ceci :  
  
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
  
 `CMyData`utilise le  `AssertValid`mécanisme permettant de tester la validité des objets stockés dans ses données membres.  La substitution de  `AssertValid`de  `CMyData`appelle la  `ASSERT_VALID`macro pour son propre membre m\_pDataList.  
  
 Les tests de validité ne s'arrête pas à ce niveau, car la classe  `CObList`substitue également   `AssertValid`.  Cette substitution réalise des tests sur l'état interne de la liste de validité supplémentaires.  Par conséquent, une validité de test sur un  `CMyData`objet conduit à des tests de validité supplémentaires pour les états internes de le stockée  `CObList`objet de liste.  
  
 Avec un peu plus de travail, vous pouvez ajouter des tests de validité pour les  `CPerson`objets également stockées dans la liste.  Vous pourriez dériver une classe de  `CPersonList`de  `CObList`et substituez   `AssertValid`.  Dans la substitution, vous appelleriez  `CObject::AssertValid`, puis itérer la liste, l'appel de  `AssertValid`sur chaque  `CPerson`objet stocké dans la liste.  Le  `CPerson`classe affichée au début de cette rubrique déjà substitue   `AssertValid`.  
  
 Il s'agit d'un mécanisme puissant lorsque vous générez pour le débogage.  Lorsque par la suite, vous déboguez pour la diffusion, le mécanisme est automatiquement désactivé.  
  
###  <a name="BKMK_Limitations_of_AssertValid"></a> Limitations de AssertValid  
 Une assertion déclenchée indique que l'objet est manifestement défectueux et que l'exécution s'arrêtera.  Toutefois, une absence d'assertion indique seulement qu'aucun problème n'a été trouvé, mais n'est pas garanti que l'objet a été vérifié.  
  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Using_assertions"></a> Utilisation d'assertions  
  
###  <a name="BKMK_Catching_logic_errors"></a> Interception des erreurs de logique  
 Vous pouvez définir une assertion sur une condition qui doit être vraie en fonction de la logique de votre programme.  L'assertion n'a aucun effet, sauf si une erreur logique se produit.  
  
 Par exemple, supposons que vous simulez des molécules de gaz dans un récipient et que la variable  `numMols`représente le nombre total de molécules.  Ce nombre ne peut pas être inférieur à zéro, afin que vous pouvez inclure une instruction d'assertion MFC comme suit :  
  
```  
ASSERT(numMols >= 0);  
  
```  
  
 Ou une assertion CRT telle que :  
  
```  
_ASSERT(numMols >= 0);  
```  
  
 Ces instructions ne rien faire si votre programme ne fonctionne pas correctement.  Si une erreur logique provoque  `numMols` pour être inférieur à zéro, cependant, l'assertion interrompt l'exécution de votre programme et l'affiche la   [Échec de l'assertion, boîte de dialogue](../debugger/assertion-failed-dialog-box.md).  
  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Checking_results_"></a> Vérification des résultats  
 Les assertions sont utiles pour les opérations dont les résultats ne sont pas évidents à partir d'une rapide inspection visuelle de test.  
  
 Par exemple, considérez le code suivant, qui met à jour la variable  `iMols`en fonction du contenu de la liste liée désignée par   `mols`:  
  
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
  
 Le nombre de molécules calculé par  `iMols`doit toujours être inférieur ou égal au nombre total de molécules,   `numMols`.  Inspection visuelle de la boucle ne montre pas que ce sera nécessairement le cas, une instruction d'assertion est utilisé après la boucle pour tester cette condition.  
  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
###  <a name="BKMK_Testing_error_conditions_"></a> Erreurs non gérée de recherche  
 Vous pouvez utiliser des assertions pour tester les conditions d'erreur à un point dans votre code où toutes les erreurs devraient avoir été gérées.  Dans l'exemple suivant, une routine graphique retourne un code d'erreur ou zéro pour la réussite.  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* Code to handle errors and  
   reset myErr if successful */  
  
ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  
  
 Si le code de gestion des erreurs fonctionne correctement, l'erreur devrait être gérée et  `myErr`réinitialisé avant que l'assertion ne soit atteinte.  Si  `myErr`a une autre valeur, l'assertion échoue, le programme s'arrête et la  [Échec de l'assertion, boîte de dialogue](../debugger/assertion-failed-dialog-box.md)s'affiche.  
  
 Les instructions d'assertion ne sont pas un substitut pour un code de gestion des erreurs, toutefois.  L'exemple suivant illustre une instruction d'assertion qui peut provoquer des problèmes dans le code de version finale :  
  
```  
myErr = myGraphRoutine(a, b);  
  
/* No Code to handle errors */  
  
ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  
  
 Ce code s'appuie sur l'instruction d'assertion pour gérer la condition d'erreur.  Par conséquent, tout code d'erreur retourné par  `myGraphRoutine`sera non géré dans le code de version finale.  
  
 [Dans cette rubrique](#BKMK_In_this_topic)  
  
## Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Assertions dans du code managé](../debugger/assertions-in-managed-code.md)