---
title: "VSInstr | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils d’analyse des performances, instrumentation"
  - "instrumentation, outil VSInstr"
  - "outils de profilage, VSInstr"
  - "outils en ligne de commande, instrumentation"
  - "ligne de commande, outils"
  - "VSInstr"
  - "VSInstr, outil"
  - "outils d’analyse des performances, outil VSInstr"
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
caps.latest.revision: 44
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 44
---
# VSInstr
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'outil VSInstr permet d'instrumenter les binaires.  Il est appelé à l'aide de la syntaxe suivante :  
  
```  
VSInstr [/U] filename [/options]  
```  
  
 Le tableau suivant décrit les options de l'outil VSInstr :  
  
|Options|Description|  
|-------------|-----------------|  
|**Help** ou **?**|Affiche l'aide.|  
|**U**|Écrit la sortie de console redirigée en Unicode.  Il doit s'agir de la première option spécifiée.|  
|`@filename`|Indique le nom d'un fichier de réponse contenant une option de commande par ligne.  N'utilisez pas de guillemets.|  
|**OutputPath** `:path`|Indique un répertoire de destination pour l'image instrumentée.  Si un chemin de sortie n'est pas spécifié, le binaire d'origine est renommé en ajoutant "Orig" au nom de fichier dans le même répertoire et une copie du binaire est instrumentée.|  
|**Exclude** `:funcspec`|Indique une spécification de fonction à exclure de l'instrumentation par les sondes.  Cela est utile lorsque l'insertion de la sonde de profilage dans une fonction provoque des résultats inattendus ou non souhaités.<br /><br /> N'utilisez pas les options **Exclude** et **Include** qui font référence aux fonctions du même binaire.<br /><br /> Vous pouvez déterminer la spécification de plusieurs fonctions avec des options **Exclude** distinctes.<br /><br /> `funcspec` est défini comme :<br /><br /> \[namespace\<separator1\>\] \[class\<separator2\>\]function<br /><br /> \<separator1\> est `::` pour le code natif, et `.` pour le code managé.<br /><br /> \<Séparateur2\> est toujours `::`<br /><br /> **Exclude** est pris en charge avec la couverture du code.<br /><br /> Le caractère générique \* est pris en charge.  Par exemple, pour exclure toutes les fonctions d'un espace de noms, utilisez :<br /><br /> MyNamespace::\*<br /><br /> Vous pouvez utiliser **VSInstr \/DumpFuncs** pour répertorier les noms complets des fonctions dans le binaire spécifié.|  
|**Include** `:funcspec`|Indique une spécification de fonction dans un binaire à instrumenter avec les sondes.  Toutes les autres fonctions dans les binaires ne sont pas instrumentées.<br /><br /> Vous pouvez déterminer plusieurs spécifications de fonctions avec des options **Include** distinctes.<br /><br /> N'utilisez pas les options **Include** et **Exclude** qui font référence aux fonctions du même binaire.<br /><br /> **Include** n'est pas pris en charge avec la couverture du code.<br /><br /> `funcspec` est défini comme :<br /><br /> \[namespace\<separator1\>\] \[class\<separator2\>\]function<br /><br /> \<separator1\> est `::` pour le code natif, et `.` pour le code managé.<br /><br /> \<Séparateur2\> est toujours `::`<br /><br /> Le caractère générique \* est pris en charge.  Par exemple, pour inclure toutes les fonctions d'un espace de noms, utilisez :<br /><br /> MyNamespace::\*<br /><br /> Vous pouvez utiliser **VSInstr \/DumpFuncs** pour répertorier les noms complets des fonctions dans le binaire spécifié.|  
|**DumpFuncs**|Répertorie les fonctions dans l'image spécifiée.  Aucune instrumentation n'est effectuée.|  
|**ExcludeSmallFuncs**|Exclut de l'instrumentation les petites fonctions qui sont des fonctions courtes qui ne passent pas d'appels de fonction.  L'option **ExcludeSmallFuncs** entraîne une moindre surcharge d'instrumentation et donc une vitesse d'instrumentation améliorée.<br /><br /> L'exclusion des petites fonctions réduit également la taille du fichier .vsp et le temps requis pour l'analyse.|  
|**Mark:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname,markid`|Insère une marque de profil \(identificateur utilisé pour délimiter les données des rapports\) que vous pouvez utiliser pour identifier le début ou la fin d'une plage de données dans le fichier de rapport .vsp.<br /><br /> **Before**  `` \- Juste avant l'entrée de la fonction cible.<br /><br /> **After**  `` \- Juste après la sortie de la fonction cible.<br /><br /> **Top**  `` \- Juste après l'entrée de la fonction cible.<br /><br /> **Bottom**  `` \- Juste avant chaque retour dans la fonction cible.<br /><br /> `funcname` \- Nom de la fonction cible<br /><br /> `Markid`\- Entier positif \(long\) à utiliser comme identificateur de la marque de profil.|  
|**Coverage**|Assure l'instrumentation de couverture.  Il peut être utilisé uniquement avec les options suivantes : **Verbose**, **OutputPath**, **Exclude** et **Logfile**.|  
|**Verbose**|L'option **Verbose** permet d'afficher des informations détaillées sur le processus d'instrumentation.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|Supprime les avertissements spécifiques ou tous les avertissements.<br /><br /> `Message Number`\- numéro d'avertissement.  Si `Message Number` est omis, tous les avertissements sont supprimés.<br /><br /> Pour plus d'informations, consultez [Avertissements VSInstr](../profiling/vsinstr-warnings.md).|  
|**Control** `:{` **Thread** `&#124;`  **Process** `&#124;` **Global** `}`|Spécifie le niveau de profilage des Options de contrôle de collecte de données VSInstr suivantes :<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread**  `` \- spécifie les fonctions de contrôle de collecte de données au niveau du thread.  Le profilage est démarré ou arrêté uniquement pour le thread actuel.  L'état de profilage des autres threads n'est pas affecté.  La valeur par défaut est thread.<br /><br /> **Process**  `` \- spécifie les fonctions de contrôle de collecte des données de profilage au niveau du processus.  Le profilage démarre ou s'arrête pour tous les threads du processus actuel.  L'état de profilage des autres processus n'est pas affecté.<br /><br /> **Global**  `` \- spécifie les fonctions de contrôle de collecte de données \(interprocessus\) au niveau global.<br /><br /> Une erreur se produit si vous ne spécifiez pas le niveau de profilage.|  
|**Start** `:{` **Inside** `&#124;` **Outside** `},funcname`|Limite la collecte de données à la fonction cible et aux fonctions enfants appelées par cette fonction.<br /><br /> **Inside**  `` \- Insère immédiatement la fonction StartProfile après l'entrée à la fonction cible.  Insère immédiatement la fonction StopProfile avant chaque retour dans la fonction cible.<br /><br /> **Outside**  `` \- Insère immédiatement la fonction StartProfile avant chaque appel à la fonction cible.  Insère immédiatement la fonction StopProfile après chaque appel à la fonction cible.<br /><br /> `funcname` \- nom de la fonction cible.|  
|**Suspend** `:{` **Inside** `&#124;` **Outside** `},funcname`|Exclut la collecte de données pour la fonction cible et les fonctions enfants appelées par la fonction.<br /><br /> **Inside**  `` \- Insère immédiatement la fonction SuspendProfile après l'entrée à la fonction cible.  Insère immédiatement la fonction ResumeProfile avant chaque retour dans la fonction cible.<br /><br /> **Outside**  `` \- Insère immédiatement la fonction SuspendProfile avant l'entrée à la fonction cible.  Insère immédiatement la fonction ResumeProfile après la sortie de la fonction cible.<br /><br /> `funcname` \- nom de la fonction cible.<br /><br /> Si la fonction cible contient une fonction StartProfile, la fonction SuspendProfile est insérée avant elle.  Si la fonction cible contient une fonction StopProfile, la fonction ResumeProfile est insérée après elle.|  
|**StartOnly:** `{` **Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom** `},funcname`|Commence la collecte de données pendant une exécution du profilage.  Elle insère la fonction API StartProfile à l'emplacement spécifié.<br /><br /> **Before**  ``  \- juste avant l'entrée de la fonction cible.<br /><br /> **After**  ``  \- juste après la sortie de la fonction cible.<br /><br /> **Top**  ``  \- juste après l'entrée de la fonction cible.<br /><br /> **Bottom**  ``  \- juste avant chaque retour dans la fonction cible.<br /><br /> `funcname` \- nom de la fonction cible.|  
|**StopOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Suspend la collecte de données pendant une exécution du profilage.  Elle insère la fonction StopProfile à l'emplacement spécifié.<br /><br /> **Before**  ``  \- juste avant l'entrée de la fonction cible.<br /><br /> **After**  ``  \- juste après la sortie de la fonction cible.<br /><br /> **Top**  ``  \- juste après l'entrée de la fonction cible.<br /><br /> **Bottom**  ``  \- juste avant chaque retour dans la fonction cible.<br /><br /> `funcname` \- nom de la fonction cible.|  
|**SuspendOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Suspend la collecte de données pendant une exécution du profilage.  Elle insère l'API SuspendProfile à l'emplacement spécifié.<br /><br /> **Before**  ``  \- juste avant l'entrée de la fonction cible.<br /><br /> **After**  ``  \- juste après la sortie de la fonction cible.<br /><br /> **Top**  ``  \- juste après l'entrée de la fonction cible.<br /><br /> **Bottom**  ``  \- juste avant chaque retour dans la fonction cible.<br /><br /> `funcname` \- nom de la fonction cible.<br /><br /> Si la fonction cible contient une fonction StartProfile, la fonction SuspendProfile est insérée avant elle.|  
|**ResumeOnly:**{**Before** `&#124;`  **After** `&#124;`  **Top** `&#124;` **Bottom**}`,funcname`|Commence ou reprend la collecte de données pendant une exécution du profilage.<br /><br /> Elle est généralement utilisée pour commencer le profilage après qu'une option **SuspendOnly** l'a arrêté.  Elle insère une API ResumeProfile à l'emplacement spécifié.<br /><br /> **Before**  ``  \- juste avant l'entrée de la fonction cible.<br /><br /> **After**  ``  \- juste après la sortie de la fonction cible.<br /><br /> **Top**  ``  \- juste après l'entrée de la fonction cible.<br /><br /> **Bottom**  ``  \- juste avant chaque retour dans la fonction cible.<br /><br /> `funcname` \- nom de la fonction cible.<br /><br /> Si la fonction cible contient une fonction StopProfile, la fonction ResumeProfile est insérée après elle.|  
  
## Voir aussi  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Avertissements VSInstr](../profiling/vsinstr-warnings.md)   
 [Vues des rapports d’outils de profilage](../profiling/performance-report-views.md)