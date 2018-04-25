---
title: Exemple de Dia2dump | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5559d1ac2a03eaeb1dca57531cd2f19831851d3b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="dia2dump-sample"></a>Dia2dump, exemple
L’exemple Dia2dump est installé avec Visual Studio et contient le fichier source Dia2dump.cpp. Le fichier exécutable compilé s’exécute à partir de la ligne de commande et affiche le contenu d’un fichier de base de données (.pdb) de programme entier.  
  
### <a name="to-install-the-sample"></a>Pour installer l’exemple  
  
1.  Vérifiez que votre système répond à toutes les exigences d’installation décrites dans la page de démarrage du programme d’installation de Visual Studio.  
  
2.  Installation de Visual Studio et suivez toutes les instructions d’installation et de configuration pour les exemples inclus.  
  
#### <a name="to-build-the-sample"></a>Pour générer l'exemple  
  
1.  Ouvrez le fichier Dia2dump.sln dans Visual Studio. (Si nécessaire, Visual Studio sera tout d’abord vous aider à mettre à niveau le projet Dia2dump.)  
  
2.  Dans les pages de propriétés de projet, dans le **C/C++** &#124; **général** &#124; **autres répertoires Include** propriété, spécifiez le `..\DIA SDK\include` active. Cela garantit que le compilateur peut trouver le fichier dia2.h.  
  
3.  Sur le **générer** menu, cliquez sur **régénérer la Solution**.  
  
4.  Fermez Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez une invite de commandes et tapez la commande suivante :  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier Source Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Porter, migrer et mettre à niveau des projets Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)