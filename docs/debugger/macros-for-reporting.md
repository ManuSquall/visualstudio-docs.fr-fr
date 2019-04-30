---
title: Macros pour la création de rapports | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c92424275a1dff69863b81fbf8567fbc4b84499
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905553"
---
# <a name="macros-for-reporting"></a>Macros pour la création de rapports
Pour le débogage, vous pouvez utiliser la **_RPTn** et **_RPTFn** macros, définies dans CRTDBG. H, au lieu de l’utilisation de `printf` instructions. Vous n’avez pas besoin d’inclose dans **#ifdef**s, car elles disparaissent automatiquement dans votre version Release lorsque **_DEBUG** n’est pas définie.

|Macro|Description|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Sort une chaîne de message et zéro à quatre arguments. Pour _RPT1 à **_RPT4**, la chaîne de message fait office de chaîne de mise en forme du style printf pour les arguments.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF4**|Ces macros sont identiques à **_RPTn**, mais elles montrent également le nom du fichier et le numéro de la ligne où est située la macro.|

 Prenons l'exemple suivant :

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Ce code écrit les valeurs de `someVar` et de `otherVar` dans **stdout**. Vous pouvez utiliser l'appel suivant à `_RPTF2` pour reporter ces mêmes valeurs et, en outre, le nom de fichier et le numéro de ligne:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Vous constaterez peut-être qu’une application particulière nécessite des rapports de débogage que les macros distribuées avec la bibliothèque Runtime C ne fournissent pas. Dans ce cas, vous pouvez écrire une macro conçue spécialement pour répondre à vos besoins. Dans un de vos fichiers d’en-tête, par exemple, vous pourriez inclure un code semblable au suivant pour définir une macro intitulée **ALERT_IF2** :

```cpp
#ifndef _DEBUG                  /* For RELEASE builds */
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)
#else                           /* For DEBUG builds   */
#define  ALERT_IF2(expr, msg, arg1, arg2) \
    do { \
        if ((expr) && \
            (1 == _CrtDbgReport(_CRT_ERROR, \
                __FILE__, __LINE__, msg, arg1, arg2))) \
            _CrtDbgBreak( ); \
    } while (0)
#endif
```

 Un seul appel à **ALERT_IF2** peut effectuer toutes les fonctions de la **printf** code :

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Vous pouvez facilement modifier une macro personnalisée pour signaler plus ou moins d’informations vers différentes destinations. Cette approche est particulièrement utile dans la mesure que vos besoins de débogage évoluent.

## <a name="see-also"></a>Voir aussi
- [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)
