---
title: 'Comment : utiliser la fenêtre Registres | Microsoft Docs'
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
- vs.debug.registers
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 668ed9b48d5013a0a134911c4bed56b99ba7e3c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502170"
---
# <a name="how-to-use-the-registers-window"></a>Comment : utiliser la fenêtre Registres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [afficher les valeurs de Registre dans le débogueur dans Visual Studio](https://docs.microsoft.com/visualstudio/debugger/how-to-use-the-registers-window).  
  
La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans le **Options** boîte de dialogue, **débogage** nœud, **général** catégorie.  
  
 Le **inscrit** fenêtre affiche le contenu du Registre. Si vous conservez le **inscrit** fenêtre à mesure que vous parcourez votre programme, vous pouvez voir valeurs des registres modifier votre code s’exécute. Les valeurs récemment modifiées s'affichent en rouge. Il est possible de modifier les valeurs des registres. Pour plus d’informations, consultez [Comment : modifier une valeur de Registre](../debugger/how-to-edit-a-register-value.md).  
  
 Pour réduire l’encombrement, la **inscrit** fenêtre classe les registres en groupes, lesquels varient en fonction de la plateforme et le processeur de type. Vous pouvez afficher ou masquer des groupes selon vos besoins. Pour plus d’informations, consultez [Comment : afficher et masquer les groupes de registres](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Pour une introduction avancée aux concepts qui sous-tendent les registres et la fenêtre Registres, consultez [principes fondamentaux de débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Pour afficher la fenêtre Registres  
  
-   Sur le **déboguer** menu, choisissez **Windows**, puis choisissez **inscrit**.  
  
     Le débogueur doit être en cours d'exécution ou en mode arrêt.  
  
    > [!NOTE]
    >  Les informations de Registre ne sont pas disponibles aux applications de script ou SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de base du débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Concepts de base du débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md)





