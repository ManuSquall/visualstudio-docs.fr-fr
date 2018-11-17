---
title: Exemple de Dia2dump | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 727d7a4a97bc0aa55d370a45549941ab286930f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805396"
---
# <a name="dia2dump-sample"></a>Dia2dump, exemple
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L’exemple Dia2dump est installé avec Visual Studio et contient le dia2dump.cpp, fichier source. Le fichier exécutable compilé s’exécute à partir de la ligne de commande et affiche le contenu d’un fichier de base de données (.pdb) programme entier.  
  
### <a name="to-install-the-sample"></a>Pour installer l’exemple  
  
1.  Vérifiez que votre système répond à toutes les exigences d’installation décrites dans la page de démarrage du programme d’installation de Visual Studio.  
  
2.  Installation de Visual Studio et suivez toutes les instructions d’installation et de configuration pour les exemples inclus.  
  
#### <a name="to-build-the-sample"></a>Pour générer l'exemple  
  
1.  Ouvrez le fichier Dia2dump.sln dans Visual Studio. (Si nécessaire, Visual Studio sera tout d’abord vous aider à mettre à niveau le projet Dia2dump.)  
  
2.  Dans les pages de propriétés de projet, dans le **C/C++** &#124; **général** &#124; **autres répertoires Include** propriété, spécifiez le `..\DIA SDK\include` directory. Cela garantit que le compilateur peut trouver le fichier dia2.h.  
  
3.  Sur le **Build** menu, cliquez sur **régénérer la Solution**.  
  
4.  Fermez Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez une invite de commandes et tapez la commande suivante :  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Dia2dump.cpp, fichier Source](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Guide pratique pour dépanner les échecs de mise à niveau de projets Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)



