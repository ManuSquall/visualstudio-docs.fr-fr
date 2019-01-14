---
title: 'Procédure : Déplacer des binaires instrumentés | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f8b50c5b76ea5b22bc9d734d32e433db1c7594d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893076"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Procédure : Déplacer les fichiers binaires instrumentés

Lors de l’instrumentation, des sondes sont insérées dans le fichier binaire pour mesurer les performances de l’application. Quand vous choisissez de déplacer le fichier binaire instrumenté, une copie du fichier binaire d’origine est instrumentée et placée à l’emplacement spécifié. Cette option est utile si vous ne voulez pas que le profileur renomme votre fichier binaire d’origine. Si le fichier binaire n’est pas déplacé, la version d’origine du fichier binaire est remplacée.

## <a name="to-relocate-instrumented-binary"></a>Pour déplacer un fichier binaire instrumenté

1. Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.

2. Dans les **Pages de propriétés**, cliquez sur les propriétés **Binaire** .

3. Cochez la case **Déplacer les fichiers binaires instrumentés** .

4. Spécifiez l’emplacement du fichier binaire instrumenté.

## <a name="see-also"></a>Voir aussi

[Configurer des sessions de performances](../profiling/configuring-performance-sessions.md)  
[VSInstr](../profiling/vsinstr.md)
