---
title: Dépannage des outils d’analyse des performances | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93e9f75ad953ff9c6cd08e8eb78bcfbf01542223
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787924"
---
# <a name="troubleshooting-performance-tools-issues"></a>Dépannage des outils d’analyse des performances
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez rencontrer les problèmes suivants quand vous utilisez les outils de profilage :  
  
-   [Aucune donnée n’est collectée par les outils de profilage](#NoDataCollected)  
  
-   [Les vues et les rapports de performances affichent des numéros pour les noms des fonctions](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> Aucune donnée n’est collectée par les outils de profilage  
 Une fois l’application profilée, le fichier (.vsp) de données de profilage n’est pas créé et l’avertissement suivant s’affiche dans la fenêtre Sortie ou dans la fenêtre de commande :  
  
 PRF0025 : Aucune donnée n’a été collectée.  
  
 Ce problème peut avoir plusieurs causes :  
  
-   Un processus qui a été profilé à l’aide de l’échantillonnage ou de la méthode de mémoire .NET démarre un processus enfant qui devient le processus effectuant le travail de l’application. Par exemple, certaines applications lisent la ligne de commande pour déterminer si elles ont été démarrées comme application Windows ou comme application de ligne de commande. Si une application Windows a été demandée, le processus d’origine démarre un nouveau processus configuré comme application Windows et le processus d’origine se ferme alors. Comme les outils de profilage ne collectent pas automatiquement les données pour les processus enfants, aucune donnée n’est collectée.  
  
     Pour collecter des données de profilage dans ce cas, attachez le profileur au processus enfant au lieu de démarrer l’application avec le profileur. Pour plus d’informations, consultez [Guide pratique pour attacher les outils d’analyse des performances à des processus en cours d’exécution ou les en détacher](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) et [Attacher (VSPerfCmd)](../profiling/attach.md)  
  
##  <a name="NoSymbols"></a> Les vues et les rapports de performances affichent des numéros pour les noms des fonctions  
 Après avoir profilé une application, vous voyez des numéros au lieu des noms des fonctions dans les rapports et les vues.  
  
 Ce problème est provoqué par l’impossibilité pour le moteur d’analyse des outils de profilage de trouver les fichiers .pdb qui contiennent les informations de symbole qui mappent les informations du code source, comme les noms des fonctions et les numéros de lignes, au fichier compilé. Par défaut, le compilateur crée le fichier .pdb quand le fichier de l’application est généré. Une référence au répertoire local du fichier .pdb est stockée dans l’application compilée. Le moteur d’analyse recherche le fichier .pdb dans le répertoire référencé puis dans le fichier qui contient le fichier de l’application. Si le fichier .pdb est introuvable, le moteur d’analyse utilise les offsets des fonctions au lieu des noms de fonctions.  
  
 Vous pouvez résoudre le problème de deux manières :  
  
-   Recherchez les fichiers .pdb et placez-les dans le même répertoire que les fichiers de l’application.  
  
-   Incorporez les informations de symbole dans le fichier (.vsp) des données de profilage. Pour plus d’informations, consultez [Enregistrement d’informations de symbole avec des fichiers de données de performances](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Le moteur d’analyse nécessite que le fichier .pdb soit de la même version que le fichier de l’application compilée. Un fichier .pdb d’une build antérieure ou ultérieure du fichier de l’application ne fonctionne pas.



