---
title: "VSPerfCLREnv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils en ligne de commande, VSPerfCLREnv"
  - "ligne de commande, outils"
  - "outils d’analyse des performances, VSPerfCLREnv"
  - "outils de profilage, VSPerfCLREnv"
  - "VSPerfCLREnv, outil"
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# VSPerfCLREnv
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'outil VSPerfCLREnv sert à définir les variables d'environnement nécessaires au profilage d'une application Framework .NET.  Il utilise la syntaxe suivante :  
  
```  
VsPerfCLREnv [/option]  
```  
  
 L'option que vous choisissez dépend du type de profilage utilisé : échantillonnage, instrumentation ou global.  Une option séparée est requise pour inclure les données sur l'interaction entre couches dans les données de profilage.  La syntaxe pour chaque option est décrite dans les tableaux suivants.  
  
> [!NOTE]
>  Une fois le profilage terminé, exécutez **VSPerfCLREnv** avec l'option **\/off** ou **\/globaloff** pour supprimer les variables d'environnement nécessaires au profilage.  Pour plus d'informations, consultez le tableau Options VSPerfCLREnv pour suppression des paramètres d'environnement ci\-après.  
  
 **Options VSPerfCLREnv pour la prise en compte des données d'interaction entre les couches**  
  
> [!WARNING]
>  Les données de profilage d'interaction de couche peuvent être collectées à l'aide de [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], ou [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)].  Toutefois, les données de profilage d'interaction de couche peuvent être affichées uniquement dans [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] et [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
 Le profilage de l'interaction entre les couches fournit des informations supplémentaires sur les requêtes ADO.NET dans des applications multicouches.  Les données sont collectées uniquement pour les appels de fonction synchrones.  Les données d'interaction peuvent être ajoutées à toute exécution du profilage à l'aide de toute méthode de profilage.  
  
 Les options **InteractionOn** et **GlobalInteractionOn** activent la collection de données d'interaction de couches.  L'option d'interaction doit être spécifiée après la définition de la variable d'environnement VSPerfCLREnv qui est obligatoire pour profiler une application.  
  
 L'exemple suivant inclut les données sur l'interaction entre couches dans une exécution du profilage qui utilise la méthode d'échantillonnage :  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 L'exemple suivant inclut les données d'interaction de couche dans une exécution de profilage pour un service Windows :  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **Options VSPerfCLREnv pour profilage par instrumentation de processus**  
  
 Le tableau suivant décrit les options VSPerfCLREnv pour le profilage par instrumentation :  
  
|Option|Description|  
|------------|-----------------|  
|**TraceOn**|Active le profilage à l'aide de la méthode d'instrumentation.  N'active pas le profilage par allocation de mémoire ni la collecte des données liées à la durée de vie des objets.|  
|**TraceGC**|Active le profilage par allocation de mémoire à l'aide de la méthode d'instrumentation.  N'active pas la collecte des données liées à la durée de vie des objets.|  
|**TraceGCLife**|Active le profilage par allocation de mémoire et la collecte des données liées à la durée de vie des objets à l'aide de la méthode d'instrumentation.|  
  
 **Options VSPerfCLREnv pour profilage par échantillonnage de processus**  
  
 Le tableau suivant décrit les options VSPerfCLREnv pour le profilage par échantillonnage :  
  
|Option|Description|  
|------------|-----------------|  
|**SampleOn**|Active le profilage à l'aide de la méthode d'échantillonnage.  N'active pas le profilage par allocation de mémoire ni la collecte des données liées à la durée de vie des objets.|  
|**SampleGC**|Active le profilage par allocation de mémoire à l'aide de la méthode d'échantillonnage.  N'active pas la collecte des données liées à la durée de vie des objets.|  
|**SampleGCLife**|Active le profilage par allocation de mémoire à l'aide de la méthode d'échantillonnage.  Active également la collecte des données liées à la durée de vie des objets.|  
|**SampleLineOff**|Désactive la collecte des données de profilage au niveau ligne .NET.|  
  
 **Options VSPerfCLREnv pour profilage global**  
  
 Pour profiler un service managé \(tel qu'une application web ASP.NET\) démarré par le système d'exploitation plutôt que par l'utilisateur, utilisez les options de profilage global de VSPerfCLREnv.  Le tableau suivant décrit les versions globales des options VSPerfCLREnv.  Ces options définissent les variables d'environnement appropriées dans le Registre.  
  
|Option|Description|  
|------------|-----------------|  
|**GlobalTraceOn**|Active le profilage global à l'aide de la méthode d'instrumentation.  Ne collecte pas les événements d'allocation de mémoire ni les données liées à la durée de vie des objets.|  
|**GlobalTraceGC**|Active le profilage global par allocation de mémoire à l'aide de la méthode d'instrumentation.  N'active pas la collecte des données liées à la durée de vie des objets.|  
|**GlobalTraceGCLife**|Active le profilage global par allocation de mémoire à l'aide de la méthode d'instrumentation.  Active également la collecte des données liées à la durée de vie des objets.|  
|**GlobalSampleOn**|Active le profilage global à l'aide de la méthode d'échantillonnage.  N'active pas la collecte des événements d'allocation de mémoire ni des données liées à la durée de vie des objets.|  
|**GlobalSampleGC**|Active le profilage global par allocation de mémoire à l'aide de la méthode d'échantillonnage.  N'active pas la collecte des données liées à la durée de vie des objets.|  
|**GlobalSampleGCLife**|Active le profilage global par allocation de mémoire à l'aide de la méthode d'échantillonnage.  Active également la collecte des données liées à la durée de vie des objets.|  
  
 **Options VSPerfCLREnv pour suppression des paramètres d'environnement**  
  
 Lorsque vous avez terminé le profilage de l'application managée, utilisez l'une des options suivantes pour supprimer les variables d'environnement ajoutées par VSPerfCLREnv.  Le tableau suivant décrit comment supprimer les variables d'environnement aussi bien standard que globales :  
  
|Option|Description|  
|------------|-----------------|  
|**Off**|Supprime les variables d'environnement pour le profilage .NET standard.  Utilisez cette option lorsque les options VSPerfClrEnv non globales ont été utilisées pour définir les variables d'environnement de profileur.|  
|**GlobalOff**|Supprime les variables d'environnement pour le profilage .NET global.  Utilisez cette option lorsque l'application a été démarrée par le système d'exploitation et pas par le profileur.|  
  
## Notes  
 Ces options ne sont pas nécessaires pour le profilage d'une application managée si l'application est démarrée à l'aide de l'Explorateur de performances dans l'IDE.  L'Explorateur de performances définit tous les paramètres d'environnement qui vous sont nécessaires.  
  
 Si l'environnement correct n'a pas été défini pendant le profilage, un avertissement s'affiche lors de l'analyse et les noms de fonctions managées ne sont pas correctement résolus.  
  
## Voir aussi  
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)