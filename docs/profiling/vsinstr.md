---
title: VSInstr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e1c5d548ae8e197523fb92ed130ebeebb04af3f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945767"
---
# <a name="vsinstr"></a>VSInstr
L’outil VSInstr est utilisé pour instrumenter des ressources binaires. Il est appelé à l’aide de la syntaxe suivante :  
  
```cmd  
VSInstr [/U] filename [/options]  
```  
  
 Le tableau suivant décrit les options de l’outil VSInstr :  
  
|Options|Description|  
|-------------|-----------------|  
|**Help** ou **?**|Affiche de l’aide.|  
|**U**|Écrit la sortie redirigée de la console au format Unicode. Cela doit être la première option spécifiée.|  
|`@filename`|Spécifie le nom d’un fichier réponse qui contient une option de commande par ligne.  N’utilisez pas de guillemets.|  
|**OutputPath** `:path`|Spécifie un répertoire de destination pour l’image instrumentée. Si aucun chemin de sortie n’est spécifié, le binaire d’origine est renommé en ajoutant « Orig » au nom de fichier dans le même répertoire, et une copie du binaire est instrumentée.|  
|**Exclude** `:funcspec`|Spécifie une spécification de fonction à exclure de l’instrumentation par les sondes. Cette option est utile quand le profilage d’une insertion de sondes dans une fonction provoque des résultats inattendus ou non souhaités.<br /><br /> N’utilisez pas d’options **Exclude** et **Include** qui font référence à des fonctions dans le même binaire.<br /><br /> Vous pouvez spécifier plusieurs spécifications de fonction avec différentes options **Exclude**.<br /><br /> `funcspec` est défini comme suit :<br /><br /> [espace de noms\<séparateur1>] [classe\<séparateur2>]fonction<br /><br /> \<séparateur1> est `::` pour le code natif, et `.` pour le code managé.<br /><br /> \<séparateur2> est toujours `::`.<br /><br /> **Exclude** est pris en charge avec la couverture du code.<br /><br /> Le caractère générique \* est pris en charge. Par exemple, pour exclure toutes les fonctions dans un espace de noms, utilisez :<br /><br /> nom_espace_de_noms::\*<br /><br /> Vous pouvez utiliser **VSInstr /DumpFuncs** pour répertorier les noms complets des fonctions dans le binaire spécifié.|  
|**Include** `:funcspec`|Spécifie une spécification de fonction dans un binaire à instrumenter avec les sondes. Toutes les autres fonctions dans les binaires ne sont pas instrumentées.<br /><br /> Vous pouvez spécifier plusieurs spécifications de fonction avec différentes options **Include**.<br /><br /> N’utilisez pas d’options **Include** et **Exclude** qui font référence à des fonctions dans le même binaire.<br /><br /> **Include** n’est pas pris en charge avec la couverture du code.<br /><br /> `funcspec` est défini comme suit :<br /><br /> [espace de noms\<séparateur1>] [classe\<séparateur2>]fonction<br /><br /> \<séparateur1> est `::` pour le code natif, et `.` pour le code managé.<br /><br /> \<séparateur2> est toujours `::`.<br /><br /> Le caractère générique \* est pris en charge. Par exemple, pour inclure toutes les fonctions dans un espace de noms, utilisez :<br /><br /> nom_espace_de_noms::\*<br /><br /> Vous pouvez utiliser **VSInstr /DumpFuncs** pour répertorier les noms complets des fonctions dans le binaire spécifié.|  
|**DumpFuncs**|Répertorie les fonctions dans l’image spécifiée. Aucune instrumentation n’est effectuée.|  
|**ExcludeSmallFuncs**|Exclut de l’instrumentation les petites fonctions (fonctions courtes qui n’effectuent pas d’appels de fonction). L’option **ExcludeSmallFuncs** permet de réduire la charge liée à l’instrumentation et donc d’accélérer celle-ci.<br /><br /> L’exclusion des petites fonctions réduit également la taille du fichier .*vsp* et le temps nécessaire à l’analyse.|  
|**Mark:**{**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname,markid`|Insère une marque de profil (identificateur utilisé pour délimiter les données dans les rapports) que vous pouvez utiliser pour identifier le début ou la fin d’une plage de données dans le fichier de rapport .vsp.<br /><br /> **Before** : juste avant l’entrée dans la fonction cible.<br /><br /> **After** : juste après la sortie de la fonction cible.<br /><br /> **Top** : juste après l’entrée dans la fonction cible.<br /><br /> **Bottom** : juste avant chaque retour dans la fonction cible.<br /><br /> `funcname` : nom de la fonction cible<br /><br /> `Markid` : entier positif (long) à utiliser comme identificateur de la marque de profil.|  
|**Coverage**|Exécute l’instrumentation de la couverture. Peut être utilisée uniquement avec les options suivantes : **Verbose**, **OutputPath**, **Exclude**, and **Logfile**.|  
|**Verbose**|L’option **Verbose** permet d’afficher des informations détaillées sur le processus d’instrumentation.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|Supprimer la totalité ou une partie spécifique des avertissements.<br /><br /> `Message Number` : numéro d’avertissement. Si `Message Number` est omis, tous les avertissements sont supprimés.<br /><br /> Pour plus d’informations, consultez [Avertissements VSInstr](../profiling/vsinstr-warnings.md).|  
|**Control** `:{` **Thread** `&#124;` **Process** `&#124;` **Global** `}`|Spécifie le niveau de profilage des options suivantes du contrôle de la collecte de données VSInstr :<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread** : spécifie les fonctions de contrôle de collecte de données au niveau du thread. Le profilage est démarré ou arrêté uniquement pour le thread actuel. L’état de profilage des autres threads n’est pas affecté. La valeur par défaut correspond au thread.<br /><br /> **Process** : spécifie les fonctions de contrôle de collecte de données de profilage au niveau du processus. Le profilage démarre ou s’arrête pour tous les threads dans le processus actuel. L’état de profilage des autres processus n’est pas affecté.<br /><br /> **Global** : spécifie les fonctions de contrôle de collecte de données (interprocessus) au niveau global.<br /><br /> Une erreur se produit si vous ne spécifiez pas le niveau de profilage.|  
|**Start** `:{` **Inside** `&#124;` **Outside** `},funcname`|Limite la collecte de données à la fonction cible et aux fonctions enfants appelées par cette fonction.<br /><br /> **Inside** : insère la fonction StartProfile immédiatement après l’entrée dans la fonction cible. Insère la fonction StopProfile juste avant chaque retour dans la fonction cible.<br /><br /> **Outside** : insère la fonction StartProfile juste avant chaque appel à la fonction cible. Insère la fonction StopProfile immédiatement après chaque appel à la fonction cible.<br /><br /> `funcname` : nom de la fonction cible.|  
|**Suspend** `:{` **Inside** `&#124;` **Outside** `},funcname`|Exclut la collecte de données pour la fonction cible et les fonctions enfants appelées par la fonction.<br /><br /> **Inside** : insère la fonction SuspendProfile immédiatement après l’entrée dans la fonction cible. Insère la fonction ResumeProfile juste avant chaque retour dans la fonction cible.<br /><br /> **Outside** : insère la fonction SuspendProfile juste avant l’entrée dans la fonction cible. Insère la fonction ResumeProfile immédiatement après la sortie de la fonction cible.<br /><br /> `funcname` : nom de la fonction cible<br /><br /> Si la fonction cible contient une fonction StartProfile, la fonction SuspendProfile est insérée avant celle-ci. Si la fonction cible contient une fonction StopProfile, la fonction ResumeProfile est insérée après celle-ci.|  
|**StartOnly :** `{` **Before** `&#124;` **After** `&#124;` **Top** `&#124;` **Bottom** `},funcname`|Commence la collecte de données pendant une exécution de profilage. Elle insère la fonction API StartProfile à l’emplacement spécifié.<br /><br /> **Before** : juste avant l’entrée dans la fonction cible.<br /><br /> **After** : juste après la sortie de la fonction cible.<br /><br /> **Top** : juste après l’entrée dans la fonction cible.<br /><br /> **Bottom** : juste avant chaque retour dans la fonction cible.<br /><br /> `funcname` : nom de la fonction cible|  
|**StopOnly:**{**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname`|Arrête la collecte de données pendant une exécution de profilage. Elle insère la fonction StopProfile à l’emplacement spécifié.<br /><br /> **Before** : juste avant l’entrée dans la fonction cible.<br /><br /> **After** : juste après la sortie de la fonction cible.<br /><br /> **Top** : juste après l’entrée dans la fonction cible.<br /><br /> **Bottom** : juste avant chaque retour dans la fonction cible.<br /><br /> `funcname` : nom de la fonction cible|  
|**SuspendOnly:**{**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname`|Arrête la collecte de données pendant une exécution de profilage. Elle insère l’API SuspendProfile à l’emplacement spécifié.<br /><br /> **Before** : juste avant l’entrée dans la fonction cible.<br /><br /> **After** : juste après la sortie de la fonction cible.<br /><br /> **Top** : juste après l’entrée dans la fonction cible.<br /><br /> **Bottom** : juste avant chaque retour dans la fonction cible.<br /><br /> `funcname` : nom de la fonction cible<br /><br /> Si la fonction cible contient une fonction StartProfile, la fonction SuspendProfile est insérée avant celle-ci.|  
|**ResumeOnly:**{**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname`|Commence ou reprend la collecte de données pendant une exécution de profilage.<br /><br /> Elle est généralement utilisée pour commencer un profilage après l’arrêt d’un profilage par une option **SuspendOnly**. Elle insère une API ResumeProfile à l’emplacement spécifié.<br /><br /> **Before** : juste avant l’entrée dans la fonction cible.<br /><br /> **After** : juste après la sortie de la fonction cible.<br /><br /> **Top** : juste après l’entrée dans la fonction cible.<br /><br /> **Bottom** : juste avant chaque retour dans la fonction cible.<br /><br /> `funcname` : nom de la fonction cible<br /><br /> Si la fonction cible contient une fonction StopProfile, la fonction ResumeProfile est insérée après celle-ci.|  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Avertissements VSInstr](../profiling/vsinstr-warnings.md)   
 [Vues du rapport des performances](../profiling/performance-report-views.md)