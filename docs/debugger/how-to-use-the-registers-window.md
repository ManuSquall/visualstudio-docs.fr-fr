---
title: "Afficher les valeurs de Registre dans le débogueur Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7aa89b6e8d36c3eb47168c8672fb7eea1e3507db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger"></a>Afficher les valeurs de Registre et utiliser la fenêtre registres dans le débogueur Visual Studio
La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans le **Options** boîte de dialogue, **débogage** nœud, **général** catégorie.  
  
 Le **inscrit** fenêtre affiche le contenu du Registre. Si vous conservez le **inscrit** fenêtre à mesure que vous parcourez votre programme, vous pouvez voir valeurs des registres modifier votre code s’exécute. Les valeurs récemment modifiées s'affichent en rouge. Il est possible de modifier les valeurs des registres. Pour plus d’informations, consultez [Comment : modifier une valeur de Registre](../debugger/how-to-edit-a-register-value.md).  
  
 Pour réduire l’encombrement, la **inscrit** fenêtre classe les registres en groupes, lesquels varient en fonction de la plateforme de processeur et de type. Vous pouvez afficher ou masquer des groupes selon vos besoins. Pour plus d’informations, consultez [Comment : afficher et masquer les groupes de registres](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Pour obtenir une présentation générale des concepts qui sous-tendent les registres et la fenêtre Registres, consultez [principes fondamentaux de débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-registers-window"></a>Pour afficher la fenêtre Registres  
  
-   Sur le **déboguer** menu, choisissez **Windows**, puis choisissez **inscrit**.  
  
     Le débogueur doit être en cours d'exécution ou en mode arrêt.  
  
    > [!NOTE]
    >  Les informations de Registre ne sont pas disponibles aux applications de script ou SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de base du débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Concepts de base du débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md)