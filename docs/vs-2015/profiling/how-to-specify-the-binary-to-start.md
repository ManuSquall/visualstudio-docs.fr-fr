---
title: Guide pratique pour spécifier le fichier binaire à démarrer | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec65dd3a5bcc812ff2f7c42ae4cbbba6080664db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503524"
---
# <a name="how-to-specify-the-binary-to-start"></a>Comment : spécifier le binaire à démarrer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : spécifier le binaire à démarrer](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-the-binary-to-start).  
  
Pour profiler des fichiers binaires, tels que les DLL, vous devez entrer des informations dans la boîte de dialogue **Pages de propriétés de \<Cible>**. Ces informations indiquent où le projet DLL peut trouver l’application appelante.  
  
 **Spécifications**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Pour spécifier l’exécutable à démarrer  
  
1.  Dans l’**Explorateur de performances**, cliquez avec le bouton droit sur le fichier binaire cible, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Pages de propriétés**, cliquez sur les propriétés **Lancer**.  
  
3.  Cochez la case **Remplacer les paramètres du projet**.  
  
4.  Dans la zone de texte **Exécutable à lancer**, spécifiez l’emplacement du fichier.  
  
5.  Dans la zone de texte **Arguments**, spécifiez les arguments nécessaires pour démarrer l’application.  
  
6.  Dans la zone de texte **Répertoire de travail**, spécifiez l’emplacement du répertoire.  
  
7.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de sessions de performances](../profiling/configuring-performance-sessions.md)



