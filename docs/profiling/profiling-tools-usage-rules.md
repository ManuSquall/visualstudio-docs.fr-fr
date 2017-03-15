---
title: "R&#232;gles d&#39;utilisation des outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# R&#232;gles d&#39;utilisation des outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les règles de performance de la catégorie d'utilisation des outils de profilage fournissent de l'aide pour l'utilisation du profileur pour la collecte plus efficace des données.  
  
|||  
|-|-|  
|[DA0002 : VSPerfCorProf.dll manquant](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|Le profilage de ligne de commande peut contenir des données incomplètes pour les binaires [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Cela peut être dû à l'absence de définition des variables d'environnement correctes.|  
|[DA0003 : Nombreux échantillons de noyau](../profiling/da0003-many-kernel-samples.md)|De nombreux exemples de profilage qui se sont produits en dehors de l'exécution du fichier binaire cible ont été enregistrés.  Pour collecter des données plus précises, utilisez la méthode d'instrumentation.|  
|[DA0004 : Utilisation intensive du processeur](../profiling/da0004-high-processor-usage.md)|Les données de profilage suggèrent que vos processeurs étaient régulièrement occupés pendant l'exécution du profilage.  Pour collecter des données plus précises, utilisez la méthode d'échantillonnage.|  
|[DA0008 : Peu d'échantillons collectés](../profiling/da0008-few-samples-collected.md)|Le nombre d'exemples collectés dans l'exécution du profilage n'était pas assez élevé pour être statistiquement significatif.  Envisagez un autre profilage et l'exécution de l'application pour une plus longue durée.  Vous pouvez  également envisager d'utiliser la méthode d'instrumentation pour collecter des données.|  
|[DA0026 : traitement du temps processeur noyau excessif](../Topic/DA0026:%20Excessive%20kernel%20CPU%20time%20processing.md)|Une durée significative lors de l'exécution du profilage est survenue en mode noyau de processeur.  Envisagez un échantillonnage à l'aide d'appels systèmes comme la métrique au lieu d'utiliser le temps comme métrique.|  
|[DA0029 : version CLR non prise en charge](../profiling/da0029-unsupported-clr-version.md)|Le fichier binaire profilé utilise une version de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] qui n'est pas pris en charge par le profileur.  Les rapports de profileur ne peuvent pas résoudre de noms de symbole.|  
|[DA0030 : collecter les mesures d'interaction de couche pour les projets de base de données](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Un nombre significatif d'appels aux méthodes dans l'espace de noms <xref:System.Data?displayProperty=fullName> a été collecté.  Pour inclure des données sur les appels de base de données, envisagez de collecter des données sur l'interaction entre les couches dans vos exécutions de profil.|