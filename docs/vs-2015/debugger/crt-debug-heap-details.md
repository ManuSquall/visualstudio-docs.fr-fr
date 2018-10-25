---
title: Détails du tas de débogage CRT | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 900127801a232ed41f119def930f8bbfe8e93550
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923002"
---
# <a name="crt-debug-heap-details"></a>Détails du tas de débogage CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette rubrique présente en détail le tas de débogage CRT.  
  
##  <a name="BKMK_Contents"></a> Sommaire  
 [Rechercher les dépassements de mémoire tampon avec le tas de débogage](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Types de bloc sur le tas de débogage](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Recherchez les fuites de l’intégrité et de la mémoire de tas](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Configurer le tas de débogage](#BKMK_Configure_the_debug_heap)  
  
 [nouveau, supprimer et _CLIENT_BLOCKs dans le C++ tas de débogage](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Fonctions de création de rapports d’état du tas](#BKMK_Heap_State_Reporting_Functions)  
  
 [Suivre les demandes d’Allocation du tas](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Rechercher les dépassements de mémoire tampon avec le tas de débogage  
 Le remplacement de la fin d'une mémoire tampon allouée et les fuites de mémoire (impossibilité de libérer les allocations lorsqu'elles sont devenues inutiles) comptent parmi les problèmes les plus courants et les plus complexes auxquels les programmeurs sont confrontés. Le tas de débogage fournit des outils puissants pour résoudre les problèmes d'allocation de mémoire de ce type.  
  
 Les versions Debug des fonctions du tas appellent les versions standard ou de base utilisées dans les versions Release. Lorsque vous demandez un bloc de mémoire, le gestionnaire du tas de débogage alloue, à partir du tas de base, un bloc de mémoire légèrement plus grand que ce qui est demandé et retourne un pointeur vers votre partie de ce bloc. Par exemple, supposons que votre application contient l'appel : `malloc( 10 )`. Dans une version Release, [malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) appellerait la routine d’allocation du tas de base qui demanderait une allocation de 10 octets. Dans une version Debug, `malloc` appellerait [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb), laquelle appellerait la routine d’allocation du tas de base demande une allocation de 10 octets plus environ 36 octets de mémoire supplémentaire. Tous les blocs de mémoire résultants dans le tas de débogage sont connectés dans une seule liste liée, ordonnée en fonction du moment où ils ont été alloués.  
  
 La mémoire supplémentaire allouée par les routines du tas de débogage est utilisée pour les informations de comptabilité, pour les pointeurs qui lient les blocs de mémoire entre eux et pour les petites mémoires tampons de chaque côté de vos données dans le but d'intercepter les remplacements de la zone allouée.  
  
 Actuellement, la structure des en-têtes de bloc utilisée pour stocker les informations de comptabilité du tas de débogage est déclarée comme suit dans le fichier d'en-tête DBGINT.H :  
  
```  
typedef struct _CrtMemBlockHeader  
{  
// Pointer to the block allocated just before this one:  
    struct _CrtMemBlockHeader *pBlockHeaderNext;  
// Pointer to the block allocated just after this one:  
    struct _CrtMemBlockHeader *pBlockHeaderPrev;  
    char *szFileName;    // File name  
    int nLine;           // Line number  
    size_t nDataSize;    // Size of user block  
    int nBlockUse;       // Type of block  
    long lRequest;       // Allocation number  
// Buffer just before (lower than) the user's memory:  
    unsigned char gap[nNoMansLandSize];  
} _CrtMemBlockHeader;  
  
/* In an actual memory block in the debug heap,  
 * this structure is followed by:  
 *   unsigned char data[nDataSize];  
 *   unsigned char anotherGap[nNoMansLandSize];  
 */  
```  
  
 Le `NoMansLand` mémoires tampons de chaque côté de la zone de données utilisateur du bloc sont actuellement taille de 4 octets et sont remplis avec une valeur d’octet connue permet de vérifier que les limites du bloc de mémoire de l’utilisateur n’ont pas été remplacés par les routines de tas de débogage. Le tas de débogage remplit également les nouveaux blocs de mémoire avec une valeur connue. Si vous choisissez de conserver les blocs libérés dans la liste liée du tas, comme indiqué ci-après, ces blocs libérés contiennent également une valeur connue. Actuellement, les valeurs d'octets réelles utilisées sont les suivantes :  
  
 NoMansLand (0xFD)  
 Les mémoires tampons « NoMansLand » de chaque côté de la mémoire utilisée par une application contiennent actuellement 0xFD.  
  
 Blocs libérés (0xDD)  
 Les blocs libérés restés inutilisés dans la liste liée du tas de débogage lorsque l'indicateur `_CRTDBG_DELAY_FREE_MEM_DF` est défini contiennent actuellement 0xDD.  
  
 Nouveaux objets (0xCD)  
 Les nouveaux objets contiennent 0xCD lorsqu'ils sont alloués.  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop")  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Types de bloc sur le tas de débogage  
 Chaque bloc de mémoire dans le tas de débogage est assigné à l'un des cinq types d'allocations. Ces types sont suivis et reportés différemment pour la détection des fuites et la création de rapports d'état. Vous pouvez spécifier un type de bloc en l’allouant à l’aide d’un appel direct à une des fonctions d’allocation de tas de débogage comme [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Les cinq types de blocs de mémoire dans le tas de débogage (défini le **nBlockUse** membre de la **_CrtMemBlockHeader** structure) sont les suivantes :  
  
 **_NORMAL_BLOCK**  
 Un appel à [malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) ou [calloc](http://msdn.microsoft.com/library/17bb79a1-98cf-4096-90cb-1f9365cd6829) crée un bloc Normal. Si vous avez l’intention d’utiliser uniquement des blocs Normal et n’ont pas besoin de blocs Client, il pouvez que vous souhaitez définir [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), ce qui entraîne l’allocation de tas tous les appels à être mappées à leurs équivalents de débogage dans les versions Debug. Cela permettra de stocker le nom de fichier et le numéro de ligne relatifs à chaque appel d'allocation dans l'en-tête du bloc correspondant.  
  
 `_CRT_BLOCK`  
 Les blocs de mémoire alloués en interne par de nombreuses fonctions de la bibliothèque Runtime sont marqués comme des blocs CRT pour pouvoir être traités séparément. En conséquence, ils n'influent pas forcément sur la détection des fuites et les autres opérations. Une allocation ne doit jamais allouer, réallouer ou libérer un bloc de type CRT.  
  
 `_CLIENT_BLOCK`  
 Pour les besoins du débogage, une application peut effectuer un suivi spécial d'un groupe donné d'allocations en leur associant ce type de bloc de mémoire, avec des appels explicites aux fonctions du tas de débogage. MFC, par exemple, alloue tous **CObjects** en tant que blocs Client ; les autres applications peuvent conserver différents objets mémoire dans les blocs Client. Il est également possible de spécifier des sous-types de bloc Client afin d'augmenter la granularité du suivi. Pour spécifier des sous-types de bloc Client, décalez le nombre de gauche de 16 bits et faites une réunion logique (`OR`) avec `_CLIENT_BLOCK`. Exemple :  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 Une fonction de raccordement fourni par le client pour faire un dump des objets stockés dans les blocs Client peut être installée à l’aide de [_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033)et sera ensuite appelée chaque fois qu’un bloc Client est exporté par une fonction de débogage. En outre, [_CrtDoForAllClientObjects](http://msdn.microsoft.com/library/d0fdb835-3cdc-45f1-9a21-54208e8df248) peut être utilisé pour appeler une fonction donnée fournie par l’application pour chaque bloc Client dans le tas de débogage.  
  
 **_FREE_BLOCK**  
 Normalement, les blocs qui sont libérés sont supprimés de la liste. Pour vérifier qu'aucune écriture n'est plus effectuée dans la mémoire libérée ou pour simuler des conditions de mémoire insuffisante, vous pouvez choisir de conserver les blocs libérés sur la liste liée, marqués en tant que Free et remplis avec une valeur d'octet connue (actuellement 0xDD).  
  
 **_IGNORE_BLOCK**  
 Il est possible de désactiver les opérations du tas de débogage pendant une certaine durée. Pendant cette période, les blocs de mémoire sont conservés dans la liste, mais marqués en tant que blocs Ignore.  
  
 Pour déterminer le type et le sous-type d’un bloc donné, utilisez la fonction [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) et les macros **_BLOCK_TYPE** et **_BLOCK_SUBTYPE**. Les macros sont définies (dans crtdbg.h) comme suit :  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Recherchez les fuites de l’intégrité et de la mémoire de tas  
 L’accès à de nombreuses fonctionnalités du tas de débogage doit s’effectuer à partir de votre code. La section suivante décrit certaines fonctionnalités et la façon de les utiliser.  
  
 `_CrtCheckMemory`  
 Vous pouvez utiliser un appel à [_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765), par exemple, pour vérifier l’intégrité du tas à tout moment. Cette fonction inspecte chaque bloc de mémoire dans le tas, vérifie que les informations d'en-tête du bloc de mémoire sont valides et confirme que les mémoires tampons n'ont pas été modifiées.  
  
 `_CrtSetDbgFlag`  
 Vous pouvez contrôler la façon dont le tas de débogage effectue le suivi des allocations à l’aide d’un indicateur interne, [_crtDbgFlag](http://msdn.microsoft.com/library/9e7adb47-8ab9-4e19-81d5-e2f237979973), ce qui peut être lu et défini à l’aide du [_CrtSetDbgFlag](http://msdn.microsoft.com/library/b5657ffb-6178-4cbf-9886-1af904ede94c) (fonction). Vous pouvez, en modifiant cet indicateur, ordonner au tas de débogage de rechercher les fuites de mémoire lorsque le programme s'arrête et de signaler les fuites détectées. De même, vous pouvez spécifier que les blocs de mémoire libérés ne doivent pas être supprimés de la liste liée, afin de simuler des situations de mémoire insuffisante. Lorsque le tas est vérifié, une inspection complète de ces blocs libérés est effectuée pour vérifier qu'ils n'ont pas été dérangés.  
  
 Le **_crtDbgFlag** indicateur contient les champs de bits suivants :  
  
|Champ de bits|Par défaut<br /><br /> par défaut|Description|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|Activé|Active l'allocation de débogage. Lorsque ce bit est désactivé, les allocations restent enchaînées, mais leur type de bloc est **_IGNORE_BLOCK**.|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|Off|Interdit la libération réelle de la mémoire, comme pour la simulation de conditions de mémoire insuffisante. Lorsque ce bit est activé, les blocs libérés sont conservés dans la liste liée du tas de débogage mais sont marquées comme **_FREE_BLOCK** et remplis avec une valeur d’octet spéciale.|  
|**_CRTDBG_CHECK_ALWAYS_DF**|Off|Entraîne **_CrtCheckMemory** est appelé à chaque allocation et désallocation. Cela ralentit l'exécution, mais permet d'intercepter rapidement les erreurs.|  
|**_CRTDBG_CHECK_CRT_DF**|Off|Provoque des blocs marqués en tant que type **_CRT_BLOCK** à inclure dans les opérations de détection des fuites et de différence des États. Lorsque ce bit est à 0, la mémoire utilisée en interne par la bibliothèque Runtime est ignorée pendant ces opérations.|  
|**_CRTDBG_LEAK_CHECK_DF**|Off|Provoque une vérification des fuites à exécuter à la sortie du programme via un appel à **_CrtDumpMemoryLeaks**. Un rapport d'erreurs est généré si l'application n'a pas pu libérer toute la mémoire qu'elle a allouée.|  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> Configurer le tas de débogage  
 Tous les appels aux fonctions du tas, telles que `malloc`, `free`, `calloc`, `realloc`, `new` et `delete`, sont traduits dans les versions Debug de ces fonctions qui opèrent dans le tas de débogage. Lorsque vous libérez un bloc de mémoire, le tas de débogage vérifie automatiquement l'intégrité des mémoires tampons de chaque côté de votre zone allouée et envoie un rapport d'erreur si un remplacement a eu lieu.  
  
 **Pour utiliser le tas de débogage**  
  
- Liez la version Debug de votre application à une version débogage de la bibliothèque Runtime C.  
  
  **Pour modifier un ou plusieurs champs de bits _crtDbgFlag et créer un nouvel état de l’indicateur**  
  
1. Appelez `_CrtSetDbgFlag` alors que le paramètre `newFlag` a la valeur `_CRTDBG_REPORT_FLAG` (pour obtenir l'état actuel de `_crtDbgFlag`) et stockez la valeur retournée dans une variable temporaire.  
  
2. Activez les bits par `OR`- ing (au niveau du bit &#124; symbole) la variable temporaire avec les masques de bits correspondants (représentés dans le code d’application par des constantes manifestes).  
  
3. Désactivez les autres bits en faisant une intersection logique `AND` (opérateur de bits de symbole &) entre la variable et un `NOT` (symbole ~ au niveau du bit) des masques de bits appropriés.  
  
4. Appelez `_CrtSetDbgFlag` alors que le paramètre `newFlag` a la valeur stockée dans la variable temporaire afin de créer l'état de `_crtDbgFlag`.  
  
   Par exemple, les lignes de code suivantes activent la détection automatique des fuites et désactivent la vérification pour les blocs de type `_CRT_BLOCK`:  
  
```  
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> nouveau, supprimer et _CLIENT_BLOCKs dans le C++ tas de débogage  
 Les versions de débogage de la bibliothèque Runtime C contiennent les versions de débogage des opérateurs C++ `new` et `delete`. Si vous utilisez le type d'allocation `_CLIENT_BLOCK`, vous devez appeler la version Debug de l'opérateur `new` directement ou créer des macros qui remplacent l'opérateur `new` en mode debug, comme le montre l'exemple suivant :  
  
```  
/* MyDbgNew.h  
 Defines global operator new to allocate from  
 client blocks  
*/  
  
#ifdef _DEBUG  
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)  
#else  
   #define DEBUG_CLIENTBLOCK  
#endif // _DEBUG  
  
/* MyApp.cpp  
        Use a default workspace for a Console Application to  
 *      build a Debug version of this code  
*/  
  
#include "crtdbg.h"  
#include "mydbgnew.h"  
  
#ifdef _DEBUG  
#define new DEBUG_CLIENTBLOCK  
#endif  
  
int main( )   {  
    char *p1;  
    p1 =  new char[40];  
    _CrtMemDumpAllObjectsSince( NULL );  
}  
```  
  
 La version Debug de l’opérateur `delete` fonctionne avec tous les types de bloc et ne nécessite aucune modification dans votre programme lorsque vous compilez une version Release.  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> Fonctions de création de rapports d’état du tas  
 **_CrtMemState**  
  
 Pour capturer un instantané récapitulatif de l'état du tas à un moment donné, utilisez la structure _CrtMemState définie dans CRTDBG.H :  
  
```  
typedef struct _CrtMemState  
{  
    // Pointer to the most recently allocated block:  
    struct _CrtMemBlockHeader * pBlockHeader;  
    // A counter for each of the 5 types of block:  
    size_t lCounts[_MAX_BLOCKS];  
    // Total bytes allocated in each block type:  
    size_t lSizes[_MAX_BLOCKS];  
    // The most bytes allocated at a time up to now:  
    size_t lHighWaterCount;  
    // The total bytes allocated at present:  
    size_t lTotalCount;  
} _CrtMemState;  
```  
  
 Cette structure enregistre un pointeur vers le premier bloc (celui qui a été alloué en dernier) dans la liste liée du tas de débogage. Elle enregistre ensuite dans deux tableaux le nombre de blocs de mémoire de chaque type (_NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK, etc.) présents dans la liste et le nombre d'octets alloués dans chaque type de bloc. Enfin, elle enregistre le plus grand nombre d'octets alloués globalement dans le tas jusqu'à ce point et le nombre d'octets actuellement alloués.  
  
 **Autres fonctions de création de rapports CRT**  
  
 Les fonctions suivantes reportent l'état et le contenu du tas, et utilisent les informations pour faciliter la détection des fuites de mémoire et des autres problèmes.  
  
|Fonction|Description|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](http://msdn.microsoft.com/library/f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc)|Enregistre un instantané du tas dans un **_CrtMemState** structure fournie par l’application.|  
|[_CrtMemDifference](http://msdn.microsoft.com/library/0f327278-b551-482f-958b-76941f796ba4)|Compare deux structures d'état de mémoire, enregistre la différence entre ces dernières dans une troisième structure d'état et retourne TRUE si les deux états sont différents.|  
|[_CrtMemDumpStatistics](http://msdn.microsoft.com/library/27b9d731-3184-4a2d-b9a7-6566ab28a9fe)|Exporte une donnée **_CrtMemState** structure. La structure peut contenir un instantané de l'état du tas de débogage à un moment donné ou la différence entre deux instantanés.|  
|[_CrtMemDumpAllObjectsSince](http://msdn.microsoft.com/library/c48a447a-e6bb-475c-9271-a3021182a0dc)|Fait un dump des informations sur tous les objets alloués depuis la capture d'un instantané donné du tas ou le début de l'exécution. Chaque fois qu’elle fait une **_CLIENT_BLOCK** bloc, il appelle une fonction de raccordement fournie par l’application, si une telle fonction a été installée à l’aide de **_CrtSetDumpClient**.|  
|[_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c)|Détermine si des fuites de mémoire se sont produites depuis le début de l'exécution du programme et, dans ce cas, fait un dump de tous les objets alloués. Chaque fois que **_CrtDumpMemoryLeaks** exporte un **_CLIENT_BLOCK** bloc, il appelle une fonction de raccordement fournie par l’application, si une telle fonction a été installée à l’aide de **_CrtSetDumpClient**.|  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> Suivre les demandes d’Allocation du tas  
 La localisation du nom du fichier source et du numéro de ligne où une macro d'assertion ou de création de rapports est exécutée facilite souvent l'identification de la cause d'un problème. Dans le cas des fonctions d'allocation du tas, cela est moins sûr. Alors que les macros peuvent être insérées en de nombreux points appropriés dans l’arborescence logique d’une application, une allocation est souvent enfouie dans une routine spéciale appelée à partir de nombreux emplacements distincts et à différentes heures. En général, la question n'est pas de savoir quelle ligne de code a effectué une mauvaise allocation, mais plutôt quelle est, parmi les milliers d'allocations effectuées par cette ligne de code, celle qui était incorrecte, et pour quelle raison elle l'était.  
  
 **Numéros de demande d’Allocation uniques et _crtBreakAlloc**  
  
 Le moyen le plus simple d'identifier précisément l'appel d'allocation du tas qui s'est avéré incorrect consiste à exploiter le numéro de demande d'allocation unique associé à chaque bloc dans le tas de débogage. Lorsque les informations sur un bloc sont signalées par une des fonctions de dump, ce numéro de demande d’allocation est placé entre accolades (par exemple, «{36}»).  
  
 Une fois que vous connaissez le numéro de demande d’allocation d’un bloc alloué de façon incorrecte, vous pouvez passer ce numéro à [_CrtSetBreakAlloc](http://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1) pour créer un point d’arrêt. L'exécution sera interrompue juste avant l'allocation du bloc et vous pourrez effectuer des recherches rétroactives pour déterminer quelle routine est à l'origine de l'appel incorrect. Pour éviter une recompilation, vous pouvez accomplir la même chose dans le débogueur en définissant **_crtBreakAlloc** pour le numéro de demande d’allocation vous intéresse.  
  
 **Création de Versions Debug de vos Routines d’Allocation**  
  
 Une approche un peu plus complexe consiste à créer des versions Debug de vos propres routines d’allocation, comparables à la **_dbg** versions de la [fonctions d’allocation de tas](../debugger/debug-versions-of-heap-allocation-functions.md). Vous pouvez ensuite passer les arguments fichier source et numéro de ligne aux routines d’allocation du tas sous-jacentes : vous verrez alors immédiatement à quel endroit une allocation incorrecte a eu lieu.  
  
 Supposons, par exemple, que votre application contient une routine couramment utilisée, similaire à la suivante :  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 Dans un fichier d'en-tête, vous pourriez ajouter un code semblable au suivant :  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 Vous pourriez ensuite changer l'allocation dans votre routine de création d'enregistrements de la façon suivante :  
  
```  
int addNewRecord(struct RecStruct *prevRecord,  
                int recType, int recAccess  
#ifdef _DEBUG  
               , const char *srcFile, int srcLine  
#endif  
    )  
{  
    /* ... code omitted through actual allocation ... */  
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,  
            srcFile, scrLine)) == NULL)  
    /* ... rest of routine omitted too ... */  
}  
```  
  
 Dorénavant, le nom du fichier source et le numéro de ligne où `addNewRecord` a été appelé seront stockés à l'intérieur de chaque bloc résultant alloué dans le tas de débogage et seront reportés lors de l'examen de ce bloc.  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)



