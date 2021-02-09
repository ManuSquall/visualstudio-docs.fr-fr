---
title: Rechercher les fuites de mémoire avec la bibliothèque CRT | Microsoft Docs
description: Découvrez comment le débogueur C/C++ et la bibliothèque Runtime C (CRT) peuvent vous aider à trouver des fuites de mémoire. Les techniques incluent des rapports de fuite de mémoire et la comparaison des instantanés de mémoire.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f98bfb3aca5be844018c4c7d9736ab2fa74ebb71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870673"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Rechercher les fuites de mémoire avec la bibliothèque CRT

Les fuites de mémoire sont parmi les bogues les plus subtiles et les plus difficiles à détecter dans les applications C/C++. Les fuites de mémoire résultent de l’échec de la désallocation correcte de la mémoire qui a été précédemment allouée. Une petite fuite de mémoire peut ne pas être remarquée au début, mais au fil du temps peut entraîner des symptômes allant de mauvaises performances au blocage lorsque l’application manque de mémoire. Une application présentant une fuite qui utilise toute la mémoire disponible peut provoquer le blocage d’autres applications, créant ainsi une confusion en ce qui concerne l’application responsable. Même les fuites de mémoire sans incidence peuvent indiquer d’autres problèmes qui doivent être corrigés.

Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] débogueur et la bibliothèque Runtime C (CRT) peuvent vous aider à détecter et identifier les fuites de mémoire.

## <a name="enable-memory-leak-detection"></a>Activer la détection des fuites de mémoire

Les principaux outils de détection des fuites de mémoire sont le débogueur C/C++ et les fonctions du tas de débogage de la bibliothèque Runtime C (CRT).

Pour activer toutes les fonctions du tas de débogage, incluez les instructions suivantes dans votre programme C++, dans l’ordre suivant :

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

L'instruction `#define` mappe une version de base des fonctions de tas CRT vers la version Debug correspondante. Si vous omettez l' `#define` instruction, le vidage des fuites de mémoire sera [moins détaillé](#interpret-the-memory-leak-report).

L’inclusion de *CRTDBG. h* mappe les `malloc` `free` fonctions et à leurs versions debug, [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) et [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), qui assurent le suivi de l’allocation et de la désallocation de mémoire. Ce mappage se produit uniquement dans les versions Debug avec `_DEBUG`. Les versions Release utilisent les fonctions `malloc` et `free` ordinaires.

Une fois que vous avez activé les fonctions de tas de débogage à l’aide des instructions précédentes, passez un appel à [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) avant un point de sortie de l’application pour afficher un rapport des fuites de mémoire lorsque l’application s’arrête.

```cpp
_CrtDumpMemoryLeaks();
```

Si votre application comporte plusieurs sorties, vous n’avez pas besoin de placer manuellement `_CrtDumpMemoryLeaks` à chaque point de sortie. Pour déclencher un appel automatique à à `_CrtDumpMemoryLeaks` chaque point de sortie, passez un appel à `_CrtSetDbgFlag` au début de votre application avec les champs de bits indiqués ici :

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

Par défaut, `_CrtDumpMemoryLeaks` affiche un rapport des fuites de mémoire dans le volet **Débogage** de la fenêtre **Sortie** . Si vous utilisez une bibliothèque, celle-ci peut redéfinir la sortie vers un autre emplacement.

Vous pouvez utiliser `_CrtSetReportMode` pour rediriger le rapport vers un autre emplacement ou revenir à la fenêtre **sortie** comme indiqué ici :

```cpp
_CrtSetReportMode( _CRT_WARN, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interprétation du rapport des fuites de mémoire

Si votre application ne définit pas `_CRTDBG_MAP_ALLOC` , [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) affiche un rapport des fuites de mémoire qui ressemble à ceci :

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Si votre application définit `_CRTDBG_MAP_ALLOC` , le rapport des fuites de mémoire ressemble à ceci :

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Le deuxième rapport indique le nom de fichier et le numéro de ligne où la mémoire perdue est d’abord allouée.

Que vous définissiez ou non `_CRTDBG_MAP_ALLOC` , le rapport des fuites de mémoire affiche :

- Le numéro d’allocation de mémoire, qui est `18` dans l’exemple
- Type de bloc, `normal` dans l’exemple.
- Emplacement de la mémoire hexadécimale, `0x00780E80` dans l’exemple.
- Taille du bloc, `64 bytes` dans l’exemple.
- les 16 premiers octets de données du bloc, au format hexadécimal.

Les types de blocs de mémoire sont *normal*, *client* ou *CRT*. Un *bloc normal* est un bloc de mémoire ordinaire alloué par votre programme. Un *bloc client* est un type de bloc de mémoire spécial utilisé par les programmes MFC pour les objets qui nécessitent un destructeur. Suivant l'objet créé, l'opérateur MFC `new` crée soit un bloc normal, soit un bloc client.

Un *bloc CRT* est alloué par la bibliothèque CRT pour ses propres besoins. La bibliothèque CRT gère la désallocation de ces blocs. par conséquent, les blocs CRT n’apparaissent pas dans le rapport des fuites de mémoire à moins qu’il y ait des problèmes sérieux avec la bibliothèque CRT.

Il existe deux autres types de blocs de mémoire qui n'apparaissent jamais dans les rapports de fuite de mémoire. Un *bloc libre* est une mémoire qui a été libérée. par conséquent, la définition n’est pas divulguée. Un *bloc ignore* est une mémoire que vous avez marquée explicitement pour exclure du rapport des fuites de mémoire.

Les techniques précédentes identifient les fuites de mémoire pour la mémoire allouée à l’aide de la fonction CRT standard `malloc` . Toutefois, si votre programme alloue de la mémoire à l’aide de l' `new` opérateur C++, vous ne verrez peut-être que le nom du fichier et le numéro de ligne où les appels se trouvent `operator new` `_malloc_dbg` dans le rapport des fuites de mémoire. Pour créer un rapport de fuite de mémoire plus utile, vous pouvez écrire une macro semblable à la suivante pour indiquer la ligne qui a effectué l’allocation :

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Vous pouvez maintenant remplacer l' `new` opérateur à l’aide `DBG_NEW` de la macro dans votre code. Dans les versions Debug, `DBG_NEW` utilise une surcharge de global `operator new` qui accepte des paramètres supplémentaires pour le type de bloc, le fichier et le numéro de ligne. Surcharge des `new` appels `_malloc_dbg` pour enregistrer les informations supplémentaires. Les rapports de fuite de mémoire affichent le nom de fichier et le numéro de ligne où les objets ayant fait l’objet d’une fuite ont été alloués. Les versions release utilisent toujours la valeur par défaut `new` . Voici un exemple de la technique :

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

Quand vous exécutez ce code dans le débogueur Visual Studio, l’appel à `_CrtDumpMemoryLeaks` génère un rapport dans la fenêtre **sortie** qui ressemble à ce qui suit :

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Cette sortie indique que l’allocation avec fuite était à la ligne 20 de *DEBUG_NEW. cpp*.

>[!NOTE]
>Nous vous déconseillons de créer une macro de préprocesseur nommée `new` ou tout autre mot clé de langage.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Définir des points d’arrêt sur un numéro d’allocation de mémoire

Le numéro d'allocation de mémoire vous indique lorsqu'un bloc de mémoire perdue a été alloué. Un bloc avec un numéro d’allocation de mémoire de 18, par exemple, est le 18e bloc de mémoire alloué pendant l’exécution de l’application. Le rapport CRT compte toutes les allocations de blocs de mémoire pendant l’exécution, y compris les allocations par la bibliothèque CRT et d’autres bibliothèques telles que MFC. Par conséquent, le bloc d’allocation de mémoire Numéro 18 n’est probablement pas le 18e bloc de mémoire alloué par votre code.

Vous pouvez utiliser le numéro d'allocation pour définir un point d'arrêt sur l'allocation de mémoire.

**Pour définir un point d’arrêt d’allocation de mémoire à l’aide de l’Fenêtre Espion :**

1. Définissez un point d’arrêt vers le début de votre application, puis démarrez le débogage.

1. Lorsque l’application s’interrompt au point d’arrêt, ouvrez une fenêtre **Espion** en sélectionnant **Déboguer**  >  **Windows**  >  **Watch 1** (ou **Espion 2**, **Espion 3** ou **Espion 4**).

1. Dans la fenêtre **Espion** , tapez `_crtBreakAlloc` dans la colonne **nom** .

   Si vous utilisez la version DLL multithread de la bibliothèque CRT (l’option/MD), ajoutez l’opérateur de contexte : `{,,ucrtbased.dll}_crtBreakAlloc`
   
   Assurez-vous que les symboles de débogage sont chargés. Dans le cas contraire, `_crtBreakAlloc` il est signalé comme non *identifié*.

1. Appuyez sur **Entrée**.

   Le débogueur évalue l'expression et place le résultat dans la colonne **Valeur** . Cette valeur sera égale **à-1** si vous n’avez défini aucun point d’arrêt sur les allocations de mémoire.

1. Dans la colonne **valeur** , remplacez la valeur par le numéro d’allocation de l’allocation de mémoire où vous souhaitez que le débogueur s’arrête.

Une fois que vous avez défini un point d’arrêt sur un numéro d’allocation de mémoire, continuez à déboguer. Veillez à exécuter dans les mêmes conditions, afin que le numéro d’allocation de mémoire ne change pas. Lorsque votre programme s’arrête à l’allocation de mémoire spécifiée, utilisez la fenêtre **pile des appels** et les autres fenêtres du débogueur pour déterminer les conditions dans lesquelles la mémoire a été allouée. Ensuite, vous pouvez poursuivre l’exécution pour observer ce qui arrive à l’objet et déterminer la raison pour laquelle il n’est pas correctement libéré.

La définition d’un point d’arrêt sur variable peut aussi s’avérer utile. Pour plus d’informations, consultez [utilisation de points d’arrêt](../debugger/using-breakpoints.md).

Vous pouvez aussi définir des points d’arrêt d’allocation de mémoire dans le code. Vous pouvez définir :

```cpp
_crtBreakAlloc = 18;
```

 ou :

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Comparer les États de la mémoire

Une autre technique pour détecter les fuites de mémoire consiste à prendre des instantanés de l'état de la mémoire de l'application en certains points clés. Pour prendre un instantané de l’état de la mémoire à un point donné de votre application, créez une `_CrtMemState` structure et transmettez-la à la `_CrtMemCheckpoint` fonction.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

La `_CrtMemCheckpoint` fonction remplit la structure avec un instantané de l’état actuel de la mémoire.

Pour sortir le contenu d’une `_CrtMemState` structure, transmettez la structure à la `_ CrtMemDumpStatistics` fonction :

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` génère un vidage de l’état de la mémoire qui ressemble à ceci :

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

`_CrtMemDifference` compare les États de la mémoire `s1` et `s2` et retourne un résultat ( `s3` ) qui correspond à la différence entre `s1` et `s2` .

Pour rechercher les fuites de mémoire, une technique consiste à placer `_CrtMemCheckpoint` des appels au début et à la fin de votre application, puis à utiliser `_CrtMemDifference` pour comparer les résultats. Si `_CrtMemDifference` indique une fuite de mémoire, vous pouvez ajouter `_CrtMemCheckpoint` d’autres appels pour diviser votre programme à l’aide d’une recherche binaire, jusqu’à ce que vous ayez isolé la source de la fuite.

## <a name="false-positives"></a>Faux positifs

 `_CrtDumpMemoryLeaks` peut fournir des fausses indications de fuites de mémoire si une bibliothèque marque des allocations internes comme blocs normaux plutôt que des blocs CRT ou des blocs client. Dans ce cas, `_CrtDumpMemoryLeaks` est incapable d'indiquer la différence entre les allocations d'utilisateur et les allocations de bibliothèque internes. Si les destructeurs globaux des allocations de la bibliothèque s'exécutent après le point d'appel à `_CrtDumpMemoryLeaks`, chaque allocation de bibliothèque interne est signalée comme une fuite de mémoire. Les versions de la bibliothèque STL (Standard Template Library) antérieures à Visual Studio .NET peuvent générer des `_CrtDumpMemoryLeaks` rapports de faux positifs.

## <a name="see-also"></a>Voir aussi

- [Détails du tas de débogage CRT](../debugger/crt-debug-heap-details.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage de code natif](../debugger/debugging-native-code.md)
