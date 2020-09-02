---
title: 'Comment : utiliser la fenêtre registres | Microsoft Docs'
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
ms.openlocfilehash: 233092af638824c462a6d9a47865a1c6f5fd9397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697464"
---
# <a name="how-to-use-the-registers-window"></a>Comment : utiliser la fenêtre Registres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans la boîte de dialogue **Options**, nœud **Débogage**, catégorie **Général**.  
  
 La fenêtre **registres** affiche le contenu du Registre. Si vous laissez la fenêtre **registres** ouverte au fur et à mesure que vous parcourez votre programme, vous pouvez voir les valeurs de Registre modifiées à mesure que votre code s’exécute. Les valeurs récemment modifiées s'affichent en rouge. Il est possible de modifier les valeurs des registres. Pour plus d’informations, consultez [Comment : modifier une valeur de Registre](../debugger/how-to-edit-a-register-value.md).  
  
 Pour réduire l’encombrement, la fenêtre **Registres** classe les registres en groupes, lesquels varient en fonction de la plateforme et du type de processeur. Vous pouvez afficher ou masquer des groupes selon vos besoins. Pour plus d’informations, consultez [Comment : afficher et masquer des groupes de registres](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Pour obtenir une présentation détaillée des concepts sous-jacents aux registres et à la fenêtre registres, consultez [concepts de base du débogage : registres (fenêtre](../debugger/debugging-basics-registers-window.md)).  
  
> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Pour afficher la fenêtre Registres  
  
- Dans le menu **Déboguer** , choisissez **fenêtres**, puis **registres**.  
  
     Le débogueur doit être en cours d'exécution ou en mode arrêt.  
  
    > [!NOTE]
    > Les informations de Registre ne sont pas disponibles aux applications de script ou SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de base du débogage : fenêtre registres](../debugger/debugging-basics-registers-window.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Concepts de base du débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md)
