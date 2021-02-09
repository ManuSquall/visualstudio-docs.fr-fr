---
title: Lignes, vue | Microsoft Docs
description: Découvrez comment la vue lignes est uniquement disponible pour les données du profileur qui ont été collectées à l’aide de la méthode d’échantillonnage.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.lines
helpviewer_keywords:
- profiling tools reports, Line view
- profiling tools, Line view
- Lines view
ms.assetid: 71ec0781-6031-4e17-af09-f50226018437
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f99431faaa7bfc77bd7cd9a14be03f7cc2238127
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917835"
---
# <a name="lines-view"></a>Lignes, vue
La vue Lignes est disponible uniquement pour les données du profileur collectées à l’aide de la méthode d’échantillonnage. Elle n’est pas disponible pour les données collectées à l’aide de l’instrumentation.

 Pour les données de profil d’échantillonnage, la vue Lignes identifie les instructions d’une fonction qui s’exécutait directement lors de la collecte de l’échantillon. Pour les données de mémoire .NET, elle identifie les instructions qui allouent la mémoire.

 Dans un fichier source, une instruction peut couvrir plusieurs lignes d’un fichier source, et une ligne unique peut inclure plusieurs instructions.

 Une instruction est identifiée par les éléments suivants :

- Le fichier source contenant l’instruction de fonction.

- La fonction contenant l’instruction.

- La ligne source au niveau de laquelle l’instruction commence.

- Le caractère de la ligne source au niveau duquel l’instruction commence.

- La ligne source au niveau de laquelle l’instruction se termine.

- Le caractère de la ligne source au niveau duquel l’instruction se termine.

## <a name="see-also"></a>Voir aussi
- [Lignes, vue](../profiling/lines-view-sampling-data.md)
- [Vue lignes-échantillonnage](../profiling/lines-view-dotnet-memory-sampling-data.md)
- [Lignes, vue](../profiling/lines-view-contention-data.md)
