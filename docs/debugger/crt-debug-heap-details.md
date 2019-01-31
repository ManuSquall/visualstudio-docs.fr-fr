---
title: Détails du tas de débogage CRT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95d69b89dd9b0d3b3aa37187ce69cc57c303cd53
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934742"
---
# <a name="crt-debug-heap-details"></a>Détails du tas de débogage CRT
Cette rubrique présente en détail le tas de débogage CRT.  
  
##  <a name="BKMK_Contents"></a> Sommaire  
 [Rechercher les dépassements de mémoire tampon avec le tas de débogage](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Types de bloc sur le tas de débogage](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Contrôler l’intégrité et les fuites de mémoire de tas](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Configurer le tas de débogage](#BKMK_Configure_the_debug_heap)  
  
 [Nouveau, supprimer et _CLIENT_BLOCKs dans le tas de débogage C++](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Fonctions de création de rapports sur l’état du tas](#BKMK_Heap_State_Reporting_Functions)  
  
 [Suivre les demandes d’allocation du tas](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Rechercher les dépassements de mémoire tampon avec le tas de débogage  
 Le remplacement de la fin d'une mémoire tampon allouée et les fuites de mémoire (impossibilité de libérer les allocations lorsqu'elles sont devenues inutiles) comptent parmi les problèmes les plus courants et les plus complexes auxquels les programmeurs sont confrontés. Le tas de débogage fournit des outils puissants pour résoudre les problèmes d'allocation de mémoire de ce type.  
  
 Les versions Debug des fonctions du tas appellent les versions standard ou de base utilisées dans les versions Release. Lorsque vous demandez un bloc de mémoire, le gestionnaire du tas de débogage alloue, à partir du tas de base, un bloc de mémoire légèrement plus grand que ce qui est demandé et retourne un pointeur vers votre partie de ce bloc. Par exemple, supposons que votre application contient l'appel : `malloc( 10 )`. Dans une version Release, [malloc](/cpp/c-runtime-library/reference/malloc) appellerait la routine d’allocation du tas de base qui demanderait une allocation de 10 octets. Dans une version Debug, `malloc` appellerait [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg), laquelle appellerait la routine d’allocation du tas de base demande une allocation de 10 octets plus environ 36 octets de mémoire supplémentaire. Tous les blocs de mémoire résultants dans le tas de débogage sont connectés dans une seule liste liée, ordonnée en fonction du moment où ils ont été alloués.  
  
 La mémoire supplémentaire allouée par les routines du tas de débogage est utilisée pour les informations de comptabilité, pour les pointeurs qui lient les blocs de mémoire entre eux et pour les petites mémoires tampons de chaque côté de vos données dans le but d'intercepter les remplacements de la zone allouée.  
  
 Actuellement, la structure des en-têtes de bloc utilisée pour stocker les informations de comptabilité du tas de débogage est déclarée comme suit dans le fichier d'en-tête DBGINT.H :  
  
```cpp
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
  
 Les mémoires tampons `NoMansLand` de chaque côté de la zone des données utilisateur du bloc ont actuellement une taille de 4 octets et contiennent une valeur d’octet connue, utilisée par les routines du tas de débogage pour vérifier que les limites du bloc de mémoire de l’utilisateur n’ont pas été écrasées. Le tas de débogage remplit également les nouveaux blocs de mémoire avec une valeur connue. Si vous choisissez de conserver les blocs libérés dans la liste liée du tas, comme indiqué ci-après, ces blocs libérés contiennent également une valeur connue. Actuellement, les valeurs d'octets réelles utilisées sont les suivantes :  
  
 NoMansLand (0xFD)  
 Les mémoires tampons « NoMansLand » de chaque côté de la mémoire utilisée par une application contiennent actuellement 0xFD.  
  
 Blocs libérés (0xDD)  
 Les blocs libérés restés inutilisés dans la liste liée du tas de débogage lorsque l'indicateur `_CRTDBG_DELAY_FREE_MEM_DF` est défini contiennent actuellement 0xDD.  
  
 Nouveaux objets (0xCD)  
 Les nouveaux objets contiennent 0xCD lorsqu'ils sont alloués.  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop")  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Types de bloc sur le tas de débogage  
 Chaque bloc de mémoire dans le tas de débogage est assigné à l'un des cinq types d'allocations. Ces types sont suivis et reportés différemment pour la détection des fuites et la création de rapports d'état. Vous pouvez spécifier un type de bloc en l’allouant avec un appel direct à l’une des fonctions d’allocation du tas de débogage, comme [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Les cinq types de bloc de mémoire dans le tas de débogage (défini dans le membre **nBlockUse** de la structure **_CrtMemBlockHeader**) sont les suivants :  
  
 **_NORMAL_BLOCK**  
 Un appel à [malloc](/cpp/c-runtime-library/reference/malloc) ou à [calloc](/cpp/c-runtime-library/reference/calloc) crée un bloc Normal. Si vous avez l’intention d’utiliser uniquement des blocs Normal et n’avez pas besoin de blocs Client, vous pouvez définir [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), qui provoque le mappage de tous les appels d’allocation du tas sur leurs équivalents de débogage dans les versions Debug. Cela permettra de stocker le nom de fichier et le numéro de ligne relatifs à chaque appel d'allocation dans l'en-tête du bloc correspondant.  
  
 `_CRT_BLOCK`  
 Les blocs de mémoire alloués en interne par de nombreuses fonctions de la bibliothèque Runtime sont marqués comme des blocs CRT pour pouvoir être traités séparément. En conséquence, ils n'influent pas forcément sur la détection des fuites et les autres opérations. Une allocation ne doit jamais allouer, réallouer ou libérer un bloc de type CRT.  
  
 `_CLIENT_BLOCK`  
 Pour les besoins du débogage, une application peut effectuer un suivi spécial d'un groupe donné d'allocations en leur associant ce type de bloc de mémoire, avec des appels explicites aux fonctions du tas de débogage. Par exemple, MFC alloue tous les **CObjects** en tant que blocs Client ; les autres applications peuvent conserver différents objets mémoire dans des blocs Client. Il est également possible de spécifier des sous-types de bloc Client afin d'augmenter la granularité du suivi. Pour spécifier des sous-types de bloc Client, décalez le nombre de gauche de 16 bits et faites une réunion logique (`OR`) avec `_CLIENT_BLOCK`. Par exemple :  
  
```cpp
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 Vous pouvez installer une fonction de raccordement fournie par le client pour faire un dump des objets stockés dans les blocs Client avec [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient). Cette fonction sera ensuite appelée chaque fois qu’un bloc Client fera l’objet d’un dump à l’aide d’une fonction de débogage. Par ailleurs, [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects) peut servir à appeler une fonction donnée fournie par l’application pour chaque bloc Client dans le tas de débogage.  
  
 **_FREE_BLOCK**  
 Normalement, les blocs qui sont libérés sont supprimés de la liste. Pour vérifier qu'aucune écriture n'est plus effectuée dans la mémoire libérée ou pour simuler des conditions de mémoire insuffisante, vous pouvez choisir de conserver les blocs libérés sur la liste liée, marqués en tant que Free et remplis avec une valeur d'octet connue (actuellement 0xDD).  
  
 **_IGNORE_BLOCK**  
 Il est possible de désactiver les opérations du tas de débogage pendant une certaine durée. Pendant cette période, les blocs de mémoire sont conservés dans la liste, mais marqués en tant que blocs Ignore.  
  
 Pour déterminer le type et le sous-type d’un bloc donné, utilisez la fonction [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) et les macros **_BLOCK_TYPE** et **_BLOCK_SUBTYPE**. Les macros sont définies (dans crtdbg.h) comme suit :  
  
```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Contrôler l’intégrité et les fuites de mémoire de tas  
 L’accès à de nombreuses fonctionnalités du tas de débogage doit s’effectuer à partir de votre code. La section suivante décrit certaines fonctionnalités et la façon de les utiliser.  
  
 `_CrtCheckMemory`  
 Vous pouvez utiliser un appel à [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory), par exemple pour vérifier l’intégrité du tas à un point quelconque. Cette fonction inspecte chaque bloc de mémoire dans le tas, vérifie que les informations d'en-tête du bloc de mémoire sont valides et confirme que les mémoires tampons n'ont pas été modifiées.  
  
 `_CrtSetDbgFlag`  
 Vous pouvez contrôler la façon dont le tas de débogage effectue le suivi des allocations à l’aide d’un indicateur interne, [_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag), qui peut être lu et défini avec la fonction [_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag). Vous pouvez, en modifiant cet indicateur, ordonner au tas de débogage de rechercher les fuites de mémoire lorsque le programme s'arrête et de signaler les fuites détectées. De même, vous pouvez spécifier que les blocs de mémoire libérés ne doivent pas être supprimés de la liste liée, afin de simuler des situations de mémoire insuffisante. Lorsque le tas est vérifié, une inspection complète de ces blocs libérés est effectuée pour vérifier qu'ils n'ont pas été dérangés.  
  
 L’indicateur **_crtDbgFlag** contient les champs de bits suivants :  
  
|Champ de bits|Par défaut<br /><br /> par défaut|Description|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|Activé|Active l'allocation de débogage. Quand ce bit est désactivé, les allocations restent enchaînées, mais leur type de bloc est **_IGNORE_BLOCK**.|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|Off|Interdit la libération réelle de la mémoire, comme pour la simulation de conditions de mémoire insuffisante. Quand ce bit est activé, les blocs libérés sont conservés dans la liste liée du tas de débogage, mais sont marqués en tant que **_FREE_BLOCK** et remplis avec une valeur d’octet spéciale.|  
|**_CRTDBG_CHECK_ALWAYS_DF**|Off|Provoque un appel à **_CrtCheckMemory** à chaque allocation et désallocation. Cela ralentit l'exécution, mais permet d'intercepter rapidement les erreurs.|  
|**_CRTDBG_CHECK_CRT_DF**|Off|Entraîne l’inclusion des blocs marqués avec le type **_CRT_BLOCK** dans les opérations de détection des fuites et de différence des états. Lorsque ce bit est à 0, la mémoire utilisée en interne par la bibliothèque Runtime est ignorée pendant ces opérations.|  
|**_CRTDBG_LEAK_CHECK_DF**|Off|Provoque une vérification des fuites à l’arrêt du programme par l’intermédiaire d’un appel à **_CrtDumpMemoryLeaks**. Un rapport d'erreurs est généré si l'application n'a pas pu libérer toute la mémoire qu'elle a allouée.|  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> Configurer le tas de débogage  
 Tous les appels aux fonctions du tas, telles que `malloc`, `free`, `calloc`, `realloc`, `new` et `delete`, sont traduits dans les versions Debug de ces fonctions qui opèrent dans le tas de débogage. Lorsque vous libérez un bloc de mémoire, le tas de débogage vérifie automatiquement l'intégrité des mémoires tampons de chaque côté de votre zone allouée et envoie un rapport d'erreur si un remplacement a eu lieu.  
  
 **Pour utiliser le tas de débogage**  
  
- Liez la version Debug de votre application à une version débogage de la bibliothèque Runtime C.  
  
  **Pour changer un ou plusieurs champs de bits _crtDbgFlag et créer un nouvel état pour l’indicateur**  
  
1. Appelez `_CrtSetDbgFlag` alors que le paramètre `newFlag` a la valeur `_CRTDBG_REPORT_FLAG` (pour obtenir l'état actuel de `_crtDbgFlag`) et stockez la valeur retournée dans une variable temporaire.  
  
2. Activez les bits par `OR`- ing (au niveau du bit &#124; symbole) la variable temporaire avec les masques de bits correspondants (représentés dans le code d’application par des constantes manifestes).  
  
3. Désactivez les autres bits en faisant une intersection logique `AND` (opérateur de bits de symbole &) entre la variable et un `NOT` (symbole ~ au niveau du bit) des masques de bits appropriés.  
  
4. Appelez `_CrtSetDbgFlag` alors que le paramètre `newFlag` a la valeur stockée dans la variable temporaire afin de créer l'état de `_crtDbgFlag`.  
  
   Par exemple, les lignes de code suivantes activent la détection automatique des fuites et désactivent la vérification pour les blocs de type `_CRT_BLOCK`:  
  
```cpp
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> Nouveau, supprimer et _CLIENT_BLOCKs dans le tas de débogage C++  
 Les versions de débogage de la bibliothèque Runtime C contiennent les versions de débogage des opérateurs C++ `new` et `delete`. Si vous utilisez le type d'allocation `_CLIENT_BLOCK`, vous devez appeler la version Debug de l'opérateur `new` directement ou créer des macros qui remplacent l'opérateur `new` en mode debug, comme le montre l'exemple suivant :  
  
```cpp
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
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> Fonctions de création de rapports sur l’état du tas  
 **_CrtMemState**  
  
 Pour capturer un instantané récapitulatif de l'état du tas à un moment donné, utilisez la structure _CrtMemState définie dans CRTDBG.H :  
  
```cpp
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
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Enregistre un instantané du tas dans une structure **_CrtMemState** fournie par l’application.|  
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|Compare deux structures d'état de mémoire, enregistre la différence entre ces dernières dans une troisième structure d'état et retourne TRUE si les deux états sont différents.|  
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Fait un vidage d’une structure **_CrtMemState** donnée. La structure peut contenir un instantané de l'état du tas de débogage à un moment donné ou la différence entre deux instantanés.|  
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Fait un dump des informations sur tous les objets alloués depuis la capture d'un instantané donné du tas ou le début de l'exécution. Chaque fois qu’elle fait un vidage d’un bloc **_CLIENT_BLOCK**, elle appelle une fonction de raccordement fournie par l’application, si une telle fonction a été installée avec **_CrtSetDumpClient**.|  
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Détermine si des fuites de mémoire se sont produites depuis le début de l'exécution du programme et, dans ce cas, fait un dump de tous les objets alloués. Chaque fois que la fonction **_CrtDumpMemoryLeaks** fait un vidage d’un bloc **_CLIENT_BLOCK**, elle appelle une fonction de raccordement fournie par l’application, si une telle fonction a été installée avec **_CrtSetDumpClient**.|  
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> Suivre les demandes d’allocation du tas  
 La localisation du nom du fichier source et du numéro de ligne où une macro d'assertion ou de création de rapports est exécutée facilite souvent l'identification de la cause d'un problème. Dans le cas des fonctions d'allocation du tas, cela est moins sûr. Alors que les macros peuvent être insérées en de nombreux points appropriés dans l’arborescence logique d’une application, une allocation est souvent enfouie dans une routine spéciale appelée à partir de nombreux emplacements distincts et à différentes heures. En général, la question n'est pas de savoir quelle ligne de code a effectué une mauvaise allocation, mais plutôt quelle est, parmi les milliers d'allocations effectuées par cette ligne de code, celle qui était incorrecte, et pour quelle raison elle l'était.  
  
 **Numéros de demande d’allocation uniques et _crtBreakAlloc**  
  
 Le moyen le plus simple d'identifier précisément l'appel d'allocation du tas qui s'est avéré incorrect consiste à exploiter le numéro de demande d'allocation unique associé à chaque bloc dans le tas de débogage. Quand les informations sur un bloc sont reportées par l’une des fonctions de dump, ce numéro de demande d’allocation est placé entre accolades (par exemple « {36} »).  
  
 Une fois que vous connaissez le numéro de demande d’allocation d’un bloc alloué de façon incorrecte, vous pouvez passer ce numéro à [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) pour créer un point d’arrêt. L'exécution sera interrompue juste avant l'allocation du bloc et vous pourrez effectuer des recherches rétroactives pour déterminer quelle routine est à l'origine de l'appel incorrect. Pour éviter une recompilation, vous pouvez effectuer la même chose dans le débogueur en définissant **_crtBreakAlloc** sur le numéro de la demande d’allocation qui vous intéresse.  
  
 **Création de versions Debug de vos routines d’allocation**  
  
 Une approche un peu plus complexe consiste à créer des versions Debug de vos propres routines d’allocation, comparables aux versions **_dbg** des [fonctions d’allocation du tas](../debugger/debug-versions-of-heap-allocation-functions.md). Vous pouvez ensuite passer les arguments fichier source et numéro de ligne aux routines d’allocation du tas sous-jacentes : vous verrez alors immédiatement à quel endroit une allocation incorrecte a eu lieu.  
  
 Supposons, par exemple, que votre application contient une routine couramment utilisée, similaire à la suivante :  
  
```cpp
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 Dans un fichier d'en-tête, vous pourriez ajouter un code semblable au suivant :  
  
```cpp
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 Vous pourriez ensuite changer l'allocation dans votre routine de création d'enregistrements de la façon suivante :  
  
```cpp
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
  
 ![Retour au début](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)
