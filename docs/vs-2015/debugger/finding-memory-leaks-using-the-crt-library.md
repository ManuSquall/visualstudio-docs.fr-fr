---
title: Recherche de fuites de mémoire à l’aide de la bibliothèque CRT | Microsoft Docs
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
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eca7af1cb572714214f264cac35b488fba993bdd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726559"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Recherche de fuites de mémoire à l'aide de la bibliothèque CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les fuites de mémoire, qui correspondent à l'échec de désallocation de mémoire précédemment allouée, figurent parmi les bogues les plus difficiles à détecter des applications C/C++. Au début, vous pourrez remarquer une petite fuite de mémoire, mais au fil du temps, cette fuite de mémoire peut progressivement provoquer des problèmes allant d'une perte de performances au blocage de l'application, lorsque la mémoire devient insuffisante. Pire encore, une application connaissant une fuite de mémoire qui utiliserait toute la mémoire disponible pourrait entraîner le blocage d'une autre application, provoquant le doute quant à l'application réellement responsable du blocage. Même les fuites de mémoire apparemment sans incidence peuvent être responsables d'autres problèmes devant être corrigés.  
  
 Le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et les bibliothèques runtime C (CRT) vous offrent la possibilité de détecter et d'identifier les fuites de mémoire.  
  
## <a name="enabling-memory-leak-detection"></a>Activation de la détection des fuites de mémoire  
 Les principaux outils de détection des fuites de mémoire sont le débogueur et les fonctions du tas de débogage des bibliothèques Runtime C (CRT).  
  
 Pour activer les fonctions du tas de débogage, incluez les instructions suivantes dans votre programme :  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Pour que les CRT fonctionnent correctement, les instructions `#include` doivent respecter l'ordre indiqué ici.  
  
 L'inclusion de crtdbg.h a pour résultat le mappage des fonctions `malloc` et [free](http://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) vers leurs versions Debug, [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) et `free`, qui effectuent le suivi de l'allocation et de la désallocation de mémoire. Ce mappage se produit uniquement dans les versions Debug avec `_DEBUG`. Les versions Release utilisent les fonctions `malloc` et `free` ordinaires.  
  
 L'instruction `#define` mappe une version de base des fonctions de tas CRT vers la version Debug correspondante. Si vous omettez l'instruction `#define` , le dump de fuite de mémoire sera moins détaillé.  
  
 Après avoir activé les fonctions de tas de débogage à l'aide de ces instructions, vous pouvez appeler `_CrtDumpMemoryLeaks` avant un point de sortie de l'application, de façon à afficher un rapport des fuites de mémoire lorsque vous quittez l'application :  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Si votre application dispose de plusieurs sorties, il n'est pas nécessaire d'appeler manuellement [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) à chaque point de sortie. Si vous appelez `_CrtSetDbgFlag` au début de votre application, `_CrtDumpMemoryLeaks` sera automatiquement appelé à chaque point de sortie. Vous devez définir les deux champs de bits indiqués ci-dessous :  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Par défaut, `_CrtDumpMemoryLeaks` affiche un rapport des fuites de mémoire dans le volet **Débogage** de la fenêtre **Sortie** . Vous pouvez utiliser `_CrtSetReportMode` pour rediriger le rapport vers un autre emplacement.  
  
 Si vous utilisez une bibliothèque, celle-ci peut redéfinir la sortie vers un autre emplacement. Dans ce cas, vous pouvez redéfinir l'emplacement de sortie vers la fenêtre **Sortie** comme indiqué ci-dessous :  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interprétation du rapport des fuites de mémoire  
 Si votre application ne définit pas `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) affiche un rapport des fuites de mémoire similaire à celui-ci :  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Si votre application définit `_CRTDBG_MAP_ALLOC`, le rapport des fuites de mémoire ressemblera à ceci :  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 À la différence du premier, le deuxième rapport indique le nom du fichier et le numéro de ligne où la mémoire perdue est d'abord allouée.  
  
 Que vous définissiez `_CRTDBG_MAP_ALLOC` ou non, le rapport des fuites de mémoire affiche les informations suivantes :  
  
- le numéro d'allocation de mémoire, en l'occurrence `18` ;  
  
- le [type de bloc](http://msdn.microsoft.com/en-us/e2f42faf-0687-49e7-aa1f-916038354f97), en l'occurrence `normal` ;  
  
- l'emplacement de stockage hexadécimal, en l'occurrence `0x00780E80` ;  
  
- la taille du bloc, en l'occurrence `64 bytes` ;  
  
- les 16 premiers octets de données du bloc, au format hexadécimal.  
  
  Le rapport des fuites de mémoire identifie un bloc de mémoire comme étant normal, client ou CRT. Un *bloc normal* est un bloc de mémoire ordinaire alloué par votre programme. Un *bloc client* est un type de bloc de mémoire spécial utilisé par les programmes MFC pour les objets qui nécessitent un destructeur. Suivant l'objet créé, l'opérateur MFC `new` crée soit un bloc normal, soit un bloc client. Un *bloc CRT* est alloué par la bibliothèque CRT pour ses propres besoins. La bibliothèque CRT gère la désallocation de ces blocs. Par conséquent, il est peu probable qu'ils apparaissent dans le rapport des fuites de mémoire, sauf en cas de problème important, comme par exemple, si la bibliothèque CRT est endommagée.  
  
  Il existe deux autres types de blocs de mémoire qui n'apparaissent jamais dans les rapports de fuite de mémoire. D'abord, le *bloc libre* , qui correspond à un bloc de mémoire libéré. Il n'a donc pas fait l'objet d'une fuite, par définition. Ensuite, le *bloc ignore* , qui correspond à de la mémoire explicitement marquée comme étant à exclure du rapport des fuites de mémoire.  
  
  Ces techniques fonctionnent pour la mémoire allouée à l'aide de la fonction CRT standard `malloc` . Si votre programme alloue de la mémoire à l’aide de C++ `new` opérateur, cependant, vous pouvez uniquement voir le fichier et numéro de ligne où l’implémentation de global `operator new` appels `_malloc_dbg` dans le rapport des fuites de mémoire. Étant donné que ce comportement n’est pas très utile, vous pouvez le modifier pour signaler la ligne qui a effectué l’allocation à l’aide d’une macro qui ressemble à ceci : 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Maintenant que vous pouvez remplacer le `new` opérateur à l’aide de la `DBG_NEW` macro dans votre code. Dans les versions debug, cet exemple utilise une surcharge de global `operator new` qui accepte des paramètres supplémentaires pour le type de bloc, le fichier et le numéro de ligne. Cette surcharge de `new` appelle `_malloc_dbg` pour enregistrer les informations supplémentaires. Lorsque vous utilisez `DBG_NEW`, la fuite de mémoire signale le nom de fichier et numéro de ligne où les objets ayant fuit ont été alloués. Dans les versions commerciales, il utilise la valeur par défaut `new`. (Nous ne recommandons pas créer de préprocesseur ou macro nommée `new`, ou n’importe quel autre mot clé du langage.) Voici un exemple de la technique :  
  
```cpp  
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```  
  
Lorsque vous exécutez ce code dans le débogueur dans Visual Studio, l’appel à `_CrtDumpMemoryLeaks` génère un rapport dans le **sortie** fenêtre ressemble à ceci :  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Cela vous indique que l’allocation d’une fuite a été à la ligne 20 du debug_new.cpp.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Définition de points d'arrêt sur un numéro d'allocation de mémoire  
 Le numéro d'allocation de mémoire vous indique lorsqu'un bloc de mémoire perdue a été alloué. Un bloc dont le numéro d'allocation de mémoire est égal à 18 correspond au 18e bloc de mémoire alloué pendant l'exécution de l'application. Le rapport CRT compte toutes les allocations de blocs de mémoire pendant l'exécution. Cela comprend les allocations effectuées par la bibliothèque CRT et d'autres bibliothèques telles que MFC. Par conséquent, un bloc dont le numéro d'allocation de mémoire est égal à 18 peut ne pas être le 18e bloc de mémoire alloué par votre code. En général, ce ne sera pas le cas.  
  
 Vous pouvez utiliser le numéro d'allocation pour définir un point d'arrêt sur l'allocation de mémoire.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>Pour définir un point d'arrêt d'allocation de mémoire à l'aide de la fenêtre Espion  
  
1. Définissez un point d'arrêt vers le début de votre application, puis démarrez-la.  
  
2. Lorsque l'application s'arrête au point d'arrêt, ouvrez la fenêtre **Espion** .  
  
3. Dans le **espion** fenêtre, tapez `_crtBreakAlloc` dans le **nom** colonne.  
  
    Si vous utilisez la version DLL multithread de la bibliothèque CRT (l'option /MD), incluez l'opérateur de contexte : `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4. Appuyez sur **RETOUR**.  
  
    Le débogueur évalue l'expression et place le résultat dans la colonne **Valeur** . Cette valeur sera égale à –1 si vous n'avez défini aucun point d'arrêt sur les allocations de mémoire.  
  
5. Remplacez la valeur dans la colonne **Valeur** par le numéro de l'allocation de mémoire où vous souhaitez effectuer l'arrêt.  
  
   Une fois le point d'arrêt défini sur un numéro d'allocation de mémoire, vous pouvez poursuivre le débogage. Veillez à exécuter le programme dans les mêmes conditions que lors de la précédente exécution, de manière à conserver le même ordre d'allocation de mémoire. Lorsque votre programme s'arrête à l'allocation de mémoire spécifiée, vous pouvez utiliser la fenêtre **Pile des appels** et les autres fenêtres de débogage pour déterminer dans quelles conditions la mémoire a été allouée. Ensuite, vous pouvez poursuivre l'exécution pour observer ce qui arrive à l'objet et connaître la raison pour laquelle il n'a pas été désalloué.  
  
   La définition d’un point d’arrêt sur variable peut aussi s’avérer utile. Pour plus d’informations, consultez [Using Breakpoints](../debugger/using-breakpoints.md).  
  
   Vous pouvez aussi définir des points d’arrêt d’allocation de mémoire dans le code. Il existe deux façons d'effectuer cette opération :  
  
```  
_crtBreakAlloc = 18;  
```  
  
 ou :  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Comparaison des états de la mémoire  
 Une autre technique pour détecter les fuites de mémoire consiste à prendre des instantanés de l'état de la mémoire de l'application en certains points clés. Pour prendre un instantané de l'état de la mémoire à un point donné de votre application, créez une structure **_CrtMemState** et passez-la à la fonction `_CrtMemCheckpoint` . Cette fonction remplit la structure avec un instantané de l'état actuel de la mémoire :  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` remplit la structure avec un instantané de l'état actuel de la mémoire :  
  
 Pour afficher le contenu d'une structure **_CrtMemState** , passez-la à la fonction `_ CrtMemDumpStatistics` :  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` crée un dump de l'état de la mémoire similaire à celui-ci :  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Pour déterminer si une fuite de mémoire a eu lieu dans une section de code, vous pouvez prendre des instantanés de l'état de la mémoire avant et après la section, puis utiliser `_ CrtMemDifference` pour comparer les deux états :  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` compare les états de mémoire `s1` et `s2` , puis retourne un résultat (`s3`) qui correspond à la différence entre `s1` et `s2`.  
  
 L'une des techniques permettant de rechercher les fuites de mémoire consiste à appeler `_CrtMemCheckpoint` au début et à la fin de votre application, puis à utiliser `_CrtMemDifference` pour comparer les résultats. Si `_CrtMemDifference` indique une fuite de mémoire, vous pouvez ajouter davantage d'appels à `_CrtMemCheckpoint` pour diviser votre programme à l'aide d'une recherche binaire jusqu'à ce que vous ayez isolé la source des fuites.  
  
## <a name="false-positives"></a>Faux positifs  
 Dans certains cas, `_CrtDumpMemoryLeaks` peut donner de fausses indications de fuites de mémoire. Cela peut se produire si vous utilisez une bibliothèque qui marque des allocations internes comme _NORMAL_BLOCK au lieu de `_CRT_BLOCK`ou `_CLIENT_BLOCK`. Dans ce cas, `_CrtDumpMemoryLeaks` est incapable d'indiquer la différence entre les allocations d'utilisateur et les allocations de bibliothèque internes. Si les destructeurs globaux des allocations de la bibliothèque s'exécutent après le point d'appel à `_CrtDumpMemoryLeaks`, chaque allocation de bibliothèque interne est signalée comme une fuite de mémoire. Dans les versions plus anciennes de la bibliothèque de modèles standard antérieures à Visual Studio .NET, `_CrtDumpMemoryLeaks` rapportait de tels faux positifs, mais ce problème a été résolu dans les versions récentes.  
  
## <a name="see-also"></a>Voir aussi  
 [Détails du tas de débogage CRT](../debugger/crt-debug-heap-details.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)



