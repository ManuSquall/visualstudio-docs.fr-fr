---
title: 'Procédure : Utiliser la fenêtre Registres | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 506425f4de218e258ca9a86bfad5154cbda5c223
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445043"
---
# <a name="how-to-use-the-registers-window"></a>Procédure : Utiliser la fenêtre Registres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans le **Options** boîte de dialogue, **débogage** nœud, **général** catégorie.  
  
 Le **inscrit** fenêtre affiche le contenu du Registre. Si vous conservez le **inscrit** fenêtre à mesure que vous parcourez votre programme, vous pouvez voir valeurs des registres modifier votre code s’exécute. Les valeurs récemment modifiées s'affichent en rouge. Il est possible de modifier les valeurs des registres. Pour plus d'informations, voir [Procédure : Modifier une valeur de Registre](../debugger/how-to-edit-a-register-value.md).  
  
 Pour réduire l’encombrement, la fenêtre **Registres** classe les registres en groupes, lesquels varient en fonction de la plateforme et du type de processeur. Vous pouvez afficher ou masquer des groupes selon vos besoins. Pour plus d'informations, voir [Procédure : Afficher et masquer les groupes de registres](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Pour une introduction avancée aux concepts qui sous-tendent les registres et la fenêtre Registres, consultez [principes fondamentaux de débogage : Registres (fenêtre)](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Pour afficher la fenêtre Registres  
  
- Sur le **déboguer** menu, choisissez **Windows**, puis choisissez **inscrit**.  
  
     Le débogueur doit être en cours d'exécution ou en mode arrêt.  
  
    > [!NOTE]
    > Les informations de Registre ne sont pas disponibles aux applications de script ou SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base pour le débogage : Registres (fenêtre)](../debugger/debugging-basics-registers-window.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Principes de base pour le débogage : la fenêtre Registres](../debugger/debugging-basics-registers-window.md)
