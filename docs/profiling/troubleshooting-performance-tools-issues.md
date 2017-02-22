---
title: "R&#233;solution des probl&#232;mes li&#233;s aux outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# R&#233;solution des probl&#232;mes li&#233;s aux outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il se peut que vous rencontriez l'un des problèmes suivants lors de l'utilisation des outils de profilage :  
  
-   [Aucune donnée n'est collectée par les outils de profilage](#NoDataCollected)  
  
-   [Affichages de performances et numéros d'affichage de rapports pour les noms de fonctions](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> Aucune donnée n'est collectée par les outils de profilage  
 Une fois qu'une application est profilée, aucun fichier de données de profilage \(.vsp\) n'est créé et l'avertissement suivant s'affiche dans la fenêtre Sortie ou dans la fenêtre de commande :  
  
 PRF0025 : Aucune donnée n'a été collectée.  
  
 Ce dysfonctionnement peut être provoqué par plusieurs problèmes :  
  
-   Un processus qui a été profilé à l'aide de l'échantillonnage ou de la méthode de mémoire .NET démarre un processus enfant qui devient le processus qui exécute le travail de l'application.  Par exemple, certaines applications lisent la ligne de commande pour déterminer si elles ont été démarrées en tant qu'applications Windows ou qu'applications de ligne de commande.  Si une application Windows a été demandée, le processus d'origine démarre un nouveau processus configuré en tant qu'application Windows ; le processus d'origine est alors interrompu.  Étant donné que les outils de profilage ne collectent pas automatiquement de données pour les processus enfant, aucune donnée n'est collectée.  
  
     Pour collecter des données de profilage dans ce type de situation, attachez le profileur au processus enfant au lieu de démarrer l'application à l'aide du profileur.  Pour plus d'informations, consultez [Procédure : attacher le profileur à des processus en cours d’exécution ou l’en détacher](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) et [Attacher \(VSPerfCmd\)](../profiling/attach.md)  
  
##  <a name="NoSymbols"></a> Affichages de performances et numéros d'affichage de rapports pour les noms de fonctions  
 Après avoir profilé une application, vous voyez des nombres à la place des noms de fonctions dans les rapports et les affichages.  
  
 Ce problème est provoqué par le moteur d'analyse des outils de profilage qui est incapable de rechercher les fichiers .pdb qui contiennent des informations de symboles qui mappent des informations de code source, comme des noms de fonctions ou des numéros de lignes sur le fichier compilé.  Par défaut, le compilateur crée le fichier .pdb lorsque le fichier d'application est généré.  Une référence au répertoire local du fichier .pdb est stockée dans l'application compilée.  Le moteur d'analyse recherche le fichier .pdb dans le répertoire référencé, puis dans le fichier qui contient actuellement le fichier d'application.  Si le fichier .pdb est introuvable, le moteur d'analyse utilise alors les offsets de fonctions au lieu des noms de fonctions.  
  
 Vous pouvez résoudre le problème de deux manières différentes :  
  
-   Rechercher les fichiers .pdb et les placer dans le même répertoire que les fichiers d'application  
  
-   Embarquer les informations de symbole dans le fichier de données de profilage \(.vsp\)  Pour plus d’informations, consultez [Enregistrement d’informations de symbole avec des fichiers de données de profilage](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Le moteur d'analyse exige que le fichier .pdb possède la même version que le fichier d'application compilé.  Un fichier .pdb d'une build antérieure ou ultérieure du fichier d'application ne fonctionnera pas.