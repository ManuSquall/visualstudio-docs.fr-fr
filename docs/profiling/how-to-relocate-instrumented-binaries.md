---
title: Déplacer des binaires instrumentés | Microsoft Docs
description: Découvrez comment les sondes sont insérées dans le fichier binaire pour mesurer les performances de l’application pendant l’instrumentation.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7c63a1ce67095696d590670327a1a33e2471c145
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907076"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Guide pratique pour déplacer des binaires instrumentés

Lors de l’instrumentation, des sondes sont insérées dans le fichier binaire pour mesurer les performances de l’application. Quand vous choisissez de déplacer le fichier binaire instrumenté, une copie du fichier binaire d’origine est instrumentée et placée à l’emplacement spécifié. Cette option est utile si vous ne voulez pas que le profileur renomme votre fichier binaire d’origine. Si le fichier binaire n’est pas déplacé, la version d’origine du fichier binaire est remplacée.

## <a name="to-relocate-instrumented-binary"></a>Pour déplacer un fichier binaire instrumenté

1. Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.

2. Dans les **Pages de propriétés**, cliquez sur les propriétés **Binaire** .

3. Cochez la case **Déplacer les fichiers binaires instrumentés** .

4. Spécifiez l’emplacement du fichier binaire instrumenté.

## <a name="see-also"></a>Voir aussi

[Configurer des sessions](../profiling/configuring-performance-sessions.md) 
 de performance [VSInstr](../profiling/vsinstr.md)
