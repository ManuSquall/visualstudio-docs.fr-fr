---
title: "Macros pour la création de rapports | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5af21a708a05bfdc0338ca1c5b2bc038e192eb4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="macros-for-reporting"></a>Macros pour la création de rapports
Vous pouvez utiliser la **_RPTn**, et **_RPTFn** macros, définies dans CRTDBG. H, au lieu de l’utilisation de `printf` instructions pour le débogage. Ces macros disparaissent automatiquement dans votre version Release lorsque **_DEBUG** n’est pas défini, il est donc inutile de les placer entre **#ifdef**s.  
  
|Macro|Description|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|Sort une chaîne de message et zéro à quatre arguments. Pour _RPT1 à **_RPT4**, la chaîne du message sert d’une chaîne mise en forme du style printf pour les arguments.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2**, **_RPTF4**|Identique à **_RPTn**, mais ces macros génère également le fichier nom et numéro de ligne où se trouve la macro.|  
  
 Prenons l'exemple suivant :  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Ce code sort les valeurs de `someVar` et `otherVar` à **stdout**. Vous pouvez utiliser l'appel suivant à `_RPTF2` pour reporter ces mêmes valeurs et, en outre, le nom de fichier et le numéro de ligne:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Si vous constatez qu’une application particulière nécessite des rapports de débogage que les macros distribuées avec la bibliothèque Runtime C ne fournissent pas, vous pouvez écrire une macro conçue spécialement pour répondre à vos besoins. Dans un des fichiers d’en-tête, par exemple, vous pouvez inclure du code semblable au suivant pour définir une macro intitulée **ALERT_IF2**:  
  
```  
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
  
 Un appel à **ALERT_IF2** pourrait exécuter toutes les fonctions de la **printf** code au début de cette rubrique :  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Étant donné que vous pouvez facilement modifier une macro personnalisée pour reporter une quantité d’informations plus ou moins grande vers différentes destinations (suivant ce qui est le plus pratique), cette approche peut se révéler particulièrement utile au fur et à mesure que vos besoins de débogage évoluent.  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)