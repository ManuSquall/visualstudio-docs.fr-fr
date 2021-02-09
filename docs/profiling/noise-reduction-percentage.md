---
title: Pourcentage de réduction du bruit | Microsoft Docs
description: En savoir plus sur le pourcentage de réduction du bruit et sur la façon dont vous pouvez contrôler le nombre d’entrées affichées dans l’arborescence des appels.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 531ff082197ca1f7e63008aeda1c27e083b569de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922425"
---
# <a name="noise-reduction-percentage"></a>Pourcentage de réduction du bruit
Par défaut, la valeur du paramètre Pourcentage de réduction du bruit est 2. Seules les entrées qui ont un pourcentage de temps inclusif supérieur ou égal à cette valeur sont affichées dans l’arborescence des appels. En changeant la valeur, vous pouvez contrôler le nombre d’entrées qui sont affichées dans l’arborescence des appels. Par exemple, changer la valeur en 10 affichera seulement les entrées de l’arborescence des appels qui ont un temps inclusif supérieur ou égal à 10 %. En augmentant la valeur du paramètre, vous pouvez vous concentrer sur les entrées qui influent le plus sur les performances de votre processus.