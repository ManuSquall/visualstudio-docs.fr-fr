---
title: "Vue Lignes - donn&#233;es d&#39;&#233;chantillonnage du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lignes (vue)"
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Vue Lignes - donn&#233;es d&#39;&#233;chantillonnage du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Lignes des données d'échantillonnage répertorie les données de performance pour les instructions qui s'exécutaient lorsque les échantillons ont été collectés lors de l'exécution du profilage.  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans Windows 8 et Windows Server 2012 nécessitaient d'importantes modifications de la manière dont le profileur Visual Studio collecte des données sur ces plateformes.  Les applications Windows Store requièrent également de nouvelles techniques de collecte.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Dans un fichier source, une instruction peut couvrir plusieurs lignes d'un fichier source, et une ligne unique peut inclure plusieurs instructions.  Une instruction est identifiée comme suit :  
  
-   Le fichier source contenant l'instruction de fonction.  
  
-   La fonction contenant l'instruction.  
  
-   La ligne source au niveau de laquelle l'instruction commence.  
  
-   Le caractère de la ligne source au niveau duquel l'instruction commence.  
  
-   La ligne source au niveau de laquelle l'instruction se termine.  
  
-   Le caractère de la ligne source au niveau duquel l'instruction se termine.  
  
 La colonne Nom de ligne fournit une concaténation pouvant être triée des données d'identificateur.  
  
 Par définition, une instruction n'appelle pas d'autres fonctions.  Par conséquent, seules les valeurs exclusives apparaissent.  
  
|Colonne|Description|  
|-------------|-----------------|  
|**ID de processus**|ID du processus \(PID\) de l'exécution du profilage.|  
|**Nom du processus**|Nom du processus.|  
|**Nom de module**|Nom du module qui contient la ligne de fonction.|  
|**Chemin du module**|Chemin d'accès du module qui contient la ligne de fonction.|  
|**Source File**|Fichier source qui contient la ligne de fonction.|  
|**Nom de la fonction**|Nom de la fonction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de départ de la fonction.|  
|**Début ligne source**|Numéro de ligne de début dans le fichier source à partir duquel cet échantillon a été collecté.|  
|**Fin ligne source**|Numéro de ligne de fin dans le fichier source à partir duquel cet échantillon a été collecté.|  
|**Début caractère source**|Décalage du caractère de début dans la ligne de fichier source au niveau de laquelle cet échantillon a été collecté.|  
|**Fin du caractère source**|Décalage du caractère de fin dans la ligne de fichier source au niveau de laquelle cet échantillon a été collecté.|  
|**Nom de ligne**|Identificateur généré par le profileur de la ligne avec la syntaxe suivante :`Source File`**;\[**`Line Number Start`**,**`Character Start`**\]\-\>;\[**`Line Number End`,`Character End`**\]**|  
|**Exemples exclusifs**|Nombre total d'échantillons collectés lorsque la ligne de fonction s'exécutait.|  
|**% d'échantillons exclusifs**|Pourcentage de tous les échantillons dans l'exécution du profilage qui ont été collectés lorsque la ligne de fonction s'exécutait.|  
  
## Voir aussi  
 [Vue Lignes \- échantillonnage](../profiling/lines-view-dotnet-memory-sampling-data.md)