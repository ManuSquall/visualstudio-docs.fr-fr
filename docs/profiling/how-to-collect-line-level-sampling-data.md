---
title: "Comment&#160;: collecter des donn&#233;es d’&#233;chantillonnage au niveau de la ligne | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils d’analyse des performances, échantillonnage au niveau de la ligne"
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Comment&#160;: collecter des donn&#233;es d’&#233;chantillonnage au niveau de la ligne
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'échantillonnage au niveau de la ligne est la capacité du profileur à déterminer l'endroit du code d'une fonction intensive de processeur, telle qu'une fonction avec exemples hautement exclusifs, où le processeur doit passer la plupart de son temps.  
  
## Vue d'ensemble  
 Pour l'échantillonnage au niveau de la ligne, le profileur parcourt la pile des appels du programme à intervalles définis et regroupe ces résultats.  Ces derniers indiquent quelles étaient les instructions exécutées par le processeur au moment de la prise des exemples.  Les données collectées sur les échantillons exclusifs sont ensuite analysées pour identifier les lignes de code et le pointeur d'instruction \(IP\).  
  
 L'échantillonnage au niveau de la ligne fonctionne pour le code aussi bien managé que natif.  Les rapports de performances qui affichent ces données incluent la vue Lignes et la vue Modules.  
  
 Les informations de début\/fin de caractère sont non disponibles pour le code natif.  Pour les instructions multilignes, les informations de début de ligne sont non disponibles pour le code natif ; seules les informations de fin de ligne sont disponibles.  
  
### Données disponibles  
 Les données d'échantillonnage disponibles incluent les informations suivantes :  
  
-   Nom de la fonction.  
  
-   Adresse de la fonction.  
  
-   Début de ligne \- numéro de ligne du code échantillonné.  
  
-   Fin de ligne \- numéro de ligne source de fin.  Il s'agit généralement des mêmes données que le « début de ligne », sauf lorsqu'une instruction de programme unique s'étend sur plusieurs lignes du code source.  
  
-   Début de caractère \- colonne de début de l'exemple d'agrégation.  Il s'agit en général de la valeur 0, sauf lorsqu'une ligne unique contient plusieurs instructions de programme.  
  
-   Fin de caractère \- colonne de fin de l'exemple d'agrégation.  
  
-   IP \- adresse où l'exemple d'agrégation a été pris \(vue IP seulement\).  
  
 En mode **Module**, si une fonction comporte des statistiques au niveau de la ligne, celles\-ci sont imbriquées sous chaque fonction.  En outre, les statistiques au niveau de l'IP imbriquées sous chaque ligne sont présentées.  
  
### Désactiver l'échantillonnage au niveau de la ligne pour le code managé  
 Par défaut, l'échantillonnage au niveau de la ligne est activé.  Vous pouvez désactiver la collecte de données au niveau de la ligne pour le code managé en procédant comme suit :  
  
-   Avant le profilage, tapez VSPerfCLREnv \/samplelineoff.  Cette action affecte à la fois les applications et les services.  
  
     \- ou \-  
  
-   Au moment du démarrage d'une application, tapez VSPerfCmd \/lineoff \<autres arguments\>.  
  
## Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Analyse des données des outils de profilage](../profiling/analyzing-performance-tools-data.md)