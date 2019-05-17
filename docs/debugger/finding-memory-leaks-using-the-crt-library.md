---
title: Rechercher les fuites de mémoire avec la bibliothèque CRT | Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7fdfedbb2f632bdb0fcaa05c7f0fb282a8fcd2b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849969"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Rechercher les fuites de mémoire avec la bibliothèque CRT

Les fuites de mémoire sont parmi les plus subtils et difficiles à détecter des bogues dans les applications C/C++. Résultat de l’échec de désallocation de mémoire précédemment alloué les fuites de mémoire. Une petite fuite de mémoire ne peut pas être remarquée dans un premier temps, mais au fil du temps peut provoquer des problèmes allant de faibles performances au blocage de l’application s’exécute en dehors de la mémoire. Une application de fuite utilise toute la mémoire disponible peut provoquer le blocage des autres applications, créer une confusion concernant l’application qui est responsable. Les fuites de mémoire même sans danger peuvent indiquer d’autres problèmes devant être corrigés.

 Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] débogueur et la bibliothèque d’exécution C (CRT) peuvent vous aider à détecter et identifier les fuites de mémoire.

## <a name="enable-memory-leak-detection"></a>Activer la détection des fuites de mémoire

Les principaux outils pour la détection des fuites de mémoire sont le débogueur C/C++ et la bibliothèque Runtime C (CRT) les fonctions de tas de débogage.

Pour activer toutes les fonctions du tas de débogage, incluez les instructions suivantes dans votre programme C++, dans l’ordre suivant :

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

L'instruction `#define` mappe une version de base des fonctions de tas CRT vers la version Debug correspondante. Si vous omettez le `#define` instruction, le dump de fuite de mémoire sera [moins détaillé](#interpret-the-memory-leak-report).

Y compris *crtdbg.h* mappe le `malloc` et `free` fonctions vers leurs versions debug, [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) et [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), qui effectuent le suivi de mémoire allocation et désallocation. Ce mappage se produit uniquement dans les versions Debug avec `_DEBUG`. Les versions Release utilisent les fonctions `malloc` et `free` ordinaires.

Une fois que vous avez activé les fonctions de tas de débogage à l’aide des instructions précédentes, ajoutez un appel à [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) avant un point de sortie d’application pour afficher un rapport des fuites de mémoire quand l’application s’arrête.

```cpp
_CrtDumpMemoryLeaks();
```

Si votre application dispose de plusieurs sorties, vous n’avez pas besoin de placer manuellement `_CrtDumpMemoryLeaks` à chaque point de sortie. Pour provoquer un appel automatique à `_CrtDumpMemoryLeaks` à chaque point de sortie, ajoutez un appel à `_CrtSetDbgFlag` au début de votre application avec les champs de bits indiqué ici :

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

Par défaut, `_CrtDumpMemoryLeaks` affiche un rapport des fuites de mémoire dans le volet **Débogage** de la fenêtre **Sortie** . Si vous utilisez une bibliothèque, celle-ci peut redéfinir la sortie vers un autre emplacement.

Vous pouvez utiliser `_CrtSetReportMode` pour rediriger le rapport vers un autre emplacement, ou revenir à la **sortie** fenêtre, comme illustré ici :

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interprétation du rapport des fuites de mémoire

Si votre application ne définit pas `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) affiche un rapport des fuites de mémoire qui ressemble à :

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Si votre application définit `_CRTDBG_MAP_ALLOC`, le rapport des fuites de mémoire se présente comme :

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Le deuxième rapport indique le nom de fichier et numéro de ligne où la mémoire perdue est d’abord allouée.

Si vous définissez `_CRTDBG_MAP_ALLOC`, affiche le rapport des fuites de mémoire :

- Le numéro d’allocation de mémoire, qui est `18` dans l’exemple
- Le type de bloc, `normal` dans l’exemple.
- L’emplacement de stockage hexadécimal, `0x00780E80` dans l’exemple.
- La taille du bloc, `64 bytes` dans l’exemple.
- les 16 premiers octets de données du bloc, au format hexadécimal.

Types de blocs de mémoire sont *normal*, *client*, ou *CRT*. Un *bloc normal* est un bloc de mémoire ordinaire alloué par votre programme. Un *bloc client* est un type de bloc de mémoire spécial utilisé par les programmes MFC pour les objets qui nécessitent un destructeur. Suivant l'objet créé, l'opérateur MFC `new` crée soit un bloc normal, soit un bloc client.

Un *bloc CRT* est alloué par la bibliothèque CRT pour ses propres besoins. La bibliothèque CRT gère la désallocation de ces blocs, de sorte que les blocs CRT n’apparaissent dans le rapport des fuites de mémoire, sauf s’il existe des problèmes graves avec la bibliothèque CRT.

Il existe deux autres types de blocs de mémoire qui n'apparaissent jamais dans les rapports de fuite de mémoire. Un *bloc libre* n’a été libérés, par définition n’est pas une fuite de mémoire. Un *bloc ignore* mémoire que vous avez explicitement marqués pour exclure du rapport des fuites de mémoire.

Les techniques précédentes identifient les fuites de mémoire pour la mémoire allouée à l’aide de la bibliothèque CRT standard `malloc` (fonction). Si votre programme alloue de la mémoire à l’aide de C++ `new` opérateur, cependant, vous pouvez uniquement voir le nom de fichier et numéro de ligne où `operator new` appels `_malloc_dbg` dans le rapport des fuites de mémoire. Pour créer un rapport des fuites de mémoire plus utile, vous pouvez écrire une macro comme suit pour signaler la ligne qui a effectué l’allocation :

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Maintenant que vous pouvez remplacer le `new` opérateur à l’aide de la `DBG_NEW` macro dans votre code. Dans les versions debug, `DBG_NEW` utilise une surcharge de global `operator new` qui accepte des paramètres supplémentaires pour le type de bloc, le fichier et le numéro de ligne. La surcharge de `new` appelle `_malloc_dbg` pour enregistrer les informations supplémentaires. Les rapports de fuite de mémoire affichent le nom de fichier et numéro de ligne où les objets ayant fuit ont été alloués. Les versions Release utilisent toujours la valeur par défaut `new`. Voici un exemple de la technique :

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

Lorsque vous exécutez ce code dans Visual Studio du débogueur, l’appel à `_CrtDumpMemoryLeaks` génère un rapport dans le **sortie** fenêtre ressemble à :

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Cette sortie des rapports que l’allocation d’une fuite a été à la ligne 20 de *debug_new.cpp*.

>[!NOTE]
>Nous ne vous recommandons de créer une macro de préprocesseur nommée `new`, ou n’importe quel autre mot clé du langage.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Définissez des points d’arrêt sur un numéro d’allocation de mémoire

Le numéro d'allocation de mémoire vous indique lorsqu'un bloc de mémoire perdue a été alloué. Un bloc avec un numéro d’allocation de mémoire de 18, est, par exemple, le 18e bloc de mémoire alloué pendant l’exécution de l’application. Le rapport CRT compte toutes les allocations de blocs de mémoire pendant l’exécution, y compris les allocations par la bibliothèque CRT et d’autres bibliothèques telles que MFC. Par conséquent, la mémoire d’allocation bloc numéro 18 n’est probablement pas le 18e bloc de mémoire alloué par votre code.

Vous pouvez utiliser le numéro d'allocation pour définir un point d'arrêt sur l'allocation de mémoire.

**Pour définir un point d’arrêt d’allocation de mémoire à l’aide de la fenêtre Espion :**

1. Définir un point d’arrêt au début de votre application et démarrez le débogage.

1. Lorsque l’application s’arrête au point d’arrêt, ouvrez un **espion** en sélectionnant **déboguer** > **Windows** > **Espion 1** (ou **espion 2**, **espion 3**, ou **espion 4**).

1. Dans le **espion** fenêtre, tapez `_crtBreakAlloc` dans le **nom** colonne.

   Si vous utilisez la version DLL multithread de la bibliothèque CRT (l’option /MD), ajoutez l’opérateur de contexte : `{,,ucrtbased.dll}_crtBreakAlloc`

1. Appuyez sur **Entrée**.

   Le débogueur évalue l'expression et place le résultat dans la colonne **Valeur** . Cette valeur est égale à **-1** si vous n’avez défini aucun point d’arrêt sur les allocations de mémoire.

1. Dans le **valeur** colonne, remplacez la valeur par le numéro d’allocation de l’allocation de mémoire où vous souhaitez que le débogueur s’arrête.

Une fois que vous définissez un point d’arrêt sur un numéro d’allocation de mémoire, continuer le débogage. Veillez à exécuter dans les mêmes conditions, donc ne change pas le numéro d’allocation de mémoire. Lorsque votre programme s’arrête à l’allocation de mémoire spécifiée, utilisez la **pile des appels** fenêtre et autres fenêtres du débogueur pour déterminer les conditions sous lesquelles la mémoire a été allouée. Ensuite, vous pouvez poursuivre l’exécution pour observer ce qui se passe à l’objet et déterminer la raison pour laquelle elle n’est pas correctement libérée.

La définition d’un point d’arrêt sur variable peut aussi s’avérer utile. Pour plus d’informations, consultez [Utilisation des points d’arrêt](../debugger/using-breakpoints.md).

Vous pouvez aussi définir des points d’arrêt d’allocation de mémoire dans le code. Vous pouvez définir :

```cpp
_crtBreakAlloc = 18;
```

 ou :

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Comparer les États de la mémoire
 Une autre technique pour détecter les fuites de mémoire consiste à prendre des instantanés de l'état de la mémoire de l'application en certains points clés. Pour prendre un instantané de l’état de la mémoire à un moment donné dans votre application, créez un `_CrtMemState` structurer et transmettez-le à la `_CrtMemCheckpoint` (fonction).

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

Le `_CrtMemCheckpoint` fonction remplit la structure avec un instantané de l’état actuel de la mémoire.

Pour afficher le contenu d’un `_CrtMemState` , passez-la à la structure de la `_ CrtMemDumpStatistics` (fonction) :

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` Crée un dump de l’état de la mémoire qui ressemble à :

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

Pour déterminer si une fuite de mémoire a eu lieu dans une section de code, vous pouvez prendre des instantanés de l'état de la mémoire avant et après la section, puis utiliser `_ CrtMemDifference` pour comparer les deux états :

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference` Compare les États de mémoire `s1` et `s2` et retourne un résultat (`s3`) qui est la différence entre `s1` et `s2`.

Une technique permettant de rechercher les fuites de mémoire commence en plaçant `_CrtMemCheckpoint` au début et à la fin de votre application, puis en utilisant les appels `_CrtMemDifference` de comparer les résultats. Si `_CrtMemDifference` présente une fuite de mémoire, vous pouvez ajouter d’autres `_CrtMemCheckpoint` appels pour diviser votre programme à l’aide d’une recherche binaire, jusqu'à ce que vous avez isolé la source des fuites.

## <a name="false-positives"></a>Faux positifs
 `_CrtDumpMemoryLeaks` peut donner de fausses indications de fuites de mémoire si une bibliothèque marque des allocations internes comme des blocs normal au lieu des blocs CRT ou le client se bloque. Dans ce cas, `_CrtDumpMemoryLeaks` est incapable d'indiquer la différence entre les allocations d'utilisateur et les allocations de bibliothèque internes. Si les destructeurs globaux des allocations de la bibliothèque s'exécutent après le point d'appel à `_CrtDumpMemoryLeaks`, chaque allocation de bibliothèque interne est signalée comme une fuite de mémoire. Les versions de la bibliothèque de modèles Standard antérieures à Visual Studio .NET peut provoquer `_CrtDumpMemoryLeaks` pour signaler le nombre de faux positifs.

## <a name="see-also"></a>Voir aussi
- [Détails du tas de débogage CRT](../debugger/crt-debug-heap-details.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)
