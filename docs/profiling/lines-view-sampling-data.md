---
title: Lignes, vue - Données d’échantillonnage | Microsoft Docs
description: Découvrez comment la vue lignes des données d’échantillonnage répertorie les données de performance pour les instructions qui étaient en cours d’exécution lorsque les exemples ont été collectés dans l’exécution du profilage.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Lines view
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 38ae3e9c40204082ea8791ddea4e92d77a0d311e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721318"
---
# <a name="lines-view---sampling-data"></a>Lignes, vue - données d’échantillonnage
La vue Lignes des données d'échantillonnage répertorie les données de performance sur les instructions qui étaient en cours d'exécution lorsque les exemples ont été collectés dans l'exécution du profilage.

> [!NOTE]
> Les fonctionnalités de sécurité renforcée de Windows 8 et Windows Server 2012 ont imposé des changements importants dans la façon dont le profileur Visual Studio collecte les données sur ces plateformes. Les applications UWP nécessitent aussi de nouvelles techniques de collecte. Consultez [Outils d’analyse des performances sur les applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 Dans un fichier source, une instruction peut couvrir plusieurs lignes d'un fichier source, et une ligne unique peut inclure plusieurs instructions. Une instruction est identifiée par les éléments suivants :

- Le fichier source contenant l’instruction de fonction.

- La fonction contenant l’instruction.

- La ligne source au niveau de laquelle l’instruction commence.

- Le caractère de la ligne source au niveau duquel l’instruction commence.

- La ligne source au niveau de laquelle l’instruction se termine.

- Le caractère de la ligne source au niveau duquel l’instruction se termine.

  La colonne Nom de ligne fournit une concaténation des données d’identificateur pouvant être triée.

  Par définition, une instruction n’appelle pas d’autres fonctions. Par conséquent, seules les valeurs exclusives apparaissent.

|Colonne|Description|
|------------|-----------------|
|**ID de processus**|ID du processus (PID) de l'exécution du profilage.|
|**Nom du processus**|Nom du processus.|
|**Nom du module**|Nom du module qui contient la ligne de fonction.|
|**Chemin du module**|Chemin du module qui contient la ligne de fonction.|
|**Source File**|Fichier source qui contient la ligne de fonction.|
|**Nom de la fonction**|Nom de la fonction.|
|**Numéro de ligne de fonction**|Numéro de ligne du début de cette fonction dans le fichier source.|
|**Adresse de la fonction**|Adresse de départ de la fonction.|
|**Début ligne source**|Numéro de la ligne de début dans le fichier source au niveau duquel cet échantillon a été collecté.|
|**Fin ligne source**|Numéro de ligne de fin dans le fichier source au niveau duquel cet échantillon a été collecté.|
|**Début caractère source**|Décalage du caractère de début dans la ligne de fichier source au niveau de laquelle cet échantillon a été collecté.|
|**Fin du caractère source**|Décalage du caractère de fin dans la ligne de fichier source au niveau de laquelle cet échantillon a été collecté.|
|**Nom de ligne**|Identificateur généré par le profileur de la ligne avec la syntaxe suivante : `Source File` **; [** `Line Number Start` **,**`Character Start` **]-> ; [**`Line Number End`**,**`Character End`**]**|
|**Échantillons exclusifs**|Nombre total d’échantillons collectés pendant l’exécution de la ligne de fonction.|
|**% d’échantillons exclusifs**|Pourcentage de tous les échantillons collectés pendant l’exécution de la fonction dans le cadre de l’exécution du profilage.|

## <a name="see-also"></a>Voir aussi
- [Vue lignes-échantillonnage](../profiling/lines-view-dotnet-memory-sampling-data.md)
