---
title: 'Comment : déplacer des binaires instrumentés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bd9c728b2b682582d63fde551b73e6604e283991
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757122"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Comment : déplacer des binaires instrumentés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lors de l’instrumentation, des sondes sont insérées dans le fichier binaire pour mesurer les performances de l’application. Quand vous choisissez de déplacer le fichier binaire instrumenté, une copie du fichier binaire d’origine est instrumentée et placée à l’emplacement spécifié. Cette option est utile si vous ne voulez pas que le profileur renomme votre fichier binaire d’origine. Si le fichier binaire n’est pas déplacé, la version d’origine du fichier binaire est remplacée.  
  
 **Spécifications**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Pour déplacer un fichier binaire instrumenté  
  
1.  Dans l’ **Explorateur de performances**, cliquez avec le bouton droit sur la session de performance, puis cliquez sur **Propriétés**.  
  
2.  Dans les **Pages de propriétés**, cliquez sur les propriétés **Binaire** .  
  
3.  Cochez la case **Déplacer les fichiers binaires instrumentés** .  
  
4.  Spécifiez l’emplacement du fichier binaire instrumenté.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)
