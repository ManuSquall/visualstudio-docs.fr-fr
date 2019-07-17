---
title: Pourcentage de réduction du bruit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c6407b40f58c3acc02705379768085793a2b79b6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195551"
---
# <a name="noise-reduction-percentage"></a>Pourcentage de réduction du bruit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Par défaut, la valeur du paramètre Pourcentage de réduction du bruit est 2. Seules les entrées qui ont un pourcentage de temps inclusif supérieur ou égal à cette valeur sont affichées dans l’arborescence des appels. En changeant la valeur, vous pouvez contrôler le nombre d’entrées qui sont affichées dans l’arborescence des appels. Par exemple, changer la valeur en 10 affichera seulement les entrées de l’arborescence des appels qui ont un temps inclusif supérieur ou égal à 10 %. En augmentant la valeur du paramètre, vous pouvez vous concentrer sur les entrées qui influent le plus sur les performances de votre processus.
