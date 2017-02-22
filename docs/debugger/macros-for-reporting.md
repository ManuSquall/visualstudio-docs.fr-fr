---
title: "Macros pour la cr&#233;ation de rapports | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.macros"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "_RPTFn (macro)"
  - "_RPTn (macro)"
  - "CRT, macros pour la création de rapports"
  - "déboguer (CRT), macros pour la création de rapports"
  - "macros, macros de création de rapports CRT"
  - "macros, déboguer avec"
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Macros pour la cr&#233;ation de rapports
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez employer les macros **\_RPTn** et **\_RPTFn**, définies dans CRTDBG.H, au lieu d'utiliser des instructions `printf` pour le débogage.  Ces macros disparaissent automatiquement dans votre version Release lorsque **\_DEBUG** n'est pas défini ; il est donc inutile de les placer entre des **\#ifdef**.  
  
|Macro|Description|  
|-----------|-----------------|  
|**\_RPT0**, **\_RPT1**, **\_RPT2**, **\_RPT3**, **\_RPT4**|Sort une chaîne de message et zéro à quatre arguments.  Pour \_RPT1 à **\_RPT4**, la chaîne de message fait office de chaîne de mise en forme du style printf pour les arguments.|  
|**\_RPTF0**, **\_RPTF1**, **,\_RPTF2**, **\_RPTF4**|Ces macros sont identiques à **\_RPTn**, mais elles sortent également le nom du fichier et le numéro de la ligne où est située la macro.|  
  
 Prenons l'exemple suivant :  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Ce code sort les valeurs de `someVar` et de `otherVar` dans **stdout**.  Vous pouvez utiliser l'appel suivant à `_RPTF2` pour reporter ces mêmes valeurs et, en outre, le nom de fichier et le numéro de ligne:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Si vous constatez qu'une application particulière nécessite des rapports de débogage que les macros distribuées avec la bibliothèque Runtime C ne fournissent pas, vous pouvez écrire une macro conçue spécialement pour répondre à vos besoins.  Dans l'un de vos fichiers d'en\-tête, par exemple, vous pourriez inclure un code semblable au suivant pour définir une macro intitulée **ALERT\_IF2** :  
  
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
  
 Un appel à **ALERT\_IF2** pourrait exécuter toutes les fonctions du code **printf au début de cette rubrique** :  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Étant donné que vous pouvez facilement modifier une macro personnalisée pour reporter une quantité d'informations plus ou moins grande vers différentes destinations \(suivant ce qui est le plus pratique\), cette approche peut se révéler particulièrement utile au fur et à mesure que vos besoins de débogage évoluent.  
  
## Voir aussi  
 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)