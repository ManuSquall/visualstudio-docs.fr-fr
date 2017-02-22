---
title: "Vue Lignes - donn&#233;es d&#39;&#233;chantillonnage de m&#233;moire .NET du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lignes (vue)"
ms.assetid: 6631ab87-0e62-4c76-a063-4ea7222b07da
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vue Lignes - donn&#233;es d&#39;&#233;chantillonnage de m&#233;moire .NET du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vue Lignes des données de profilage d'allocation de mémoire .NET qui utilisent la méthode d'échantillonnage répertorie les instructions qui ont alloué la mémoire pendant l'exécution du profilage.  Les colonnes comprennent également la taille et le nombre d'allocations.  
  
 Dans un fichier source, une instruction peut couvrir plusieurs lignes d'un fichier source, et une ligne unique peut inclure plusieurs instructions.  
  
 Une instruction est identifiée comme suit :  
  
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
|**Nom de module**|Nom du module qui contient l'instruction.|  
|**Chemin du module**|Chemin du module qui contient l'instruction.|  
|**Source File**|Fichier source contenant l'instruction de fonction.|  
|**Nom de la fonction**|Nom de la fonction contenant cette instruction.|  
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|  
|**Adresse de la fonction**|Adresse de départ de la fonction.|  
|**Début ligne source**|Numéro de la ligne initiale dans le fichier source à laquelle l'allocation s'est produite.|  
|**Fin ligne source**|Numéro de la ligne de fin dans le fichier source à laquelle l'allocation s'est produite.|  
|**Début caractère source**|Offset du caractère initial dans la ligne de fichier source à laquelle l'allocation s'est produite.|  
|**Fin du caractère source**|Offset du caractère de fin dans la ligne de fichier source à laquelle l'allocation s'est produite.|  
|**Nom de ligne**|Identificateur généré par le profileur de la ligne avec la syntaxe suivante :`Source File`**;\[**`Line Number Start`**,**`Character Start`**\]\-;\[\>;\[**`Line Number Start,Character Start`,\]|  
|**Allocations exclusives**|Nombre total d'objets créés dans cette ligne.|  
|**Allocations exclusives %**|Pourcentage de tous les objets créés dans l'exécution du profilage alloués dans cette ligne.|  
|**Octets exclusifs**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui ont été alloués dans cette ligne.|  
|**Octets exclusifs %**|Pourcentage de tous les octets de mémoire alloués dans l'exécution du profilage qui ont été alloués dans cette ligne.|  
  
## Voir aussi  
 [Vue Lignes](../profiling/lines-view-sampling-data.md)