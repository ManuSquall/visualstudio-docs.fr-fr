---
title: 'Préparation du débogage : Applications Windows Forms | Microsoft Docs'
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
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [J#], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9448b6116f59f22aed6dd0796a3409806021ba0e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262156"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Préparation du débogage : applications Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le modèle de projet Windows Forms crée une application Windows Forms. Le débogage de ce type d'application dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] est assez simple. Pour plus d’informations, consultez [création d’un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Lorsque vous créez un projet Windows Forms à l’aide du modèle de projet, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] crée automatiquement les paramètres requis pour les configurations Debug et Release. Si nécessaire, vous pouvez modifier ces paramètres. Ces paramètres peuvent être modifiés dans le  **\<nom_projet > Pages de propriétés** boîte de dialogue (**mon projet** en Visual Basic).  
  
 Pour plus d’informations, consultez [paramètres de propriété recommandés](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Le tableau suivant affiche un paramètre de propriété recommandé supplémentaire.  
  
### <a name="configuration-properties-in-debug-tab"></a>Propriétés de configuration sous l'onglet Déboguer  
  
|**Nom de propriété**|**Paramètre**|  
|-----------------------|-----------------|  
|**Action de démarrage**|-La valeur **projet de démarrage,** la plupart du temps. La valeur **démarrer le programme externe** si vous souhaitez démarrer un autre fichier exécutable lorsque vous démarrez le débogage (habituellement pour déboguer des DLL).|  
  
 Vous pouvez déboguer des applications Windows Forms dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou en établissant un attachement avec une application en cours d’exécution. Pour plus d’informations sur l’attachement, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Pour déboguer une application Windows Forms Visual Basic, C# ou F#  
  
1.  Ouvrez le projet dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2.  Créez des points d'arrêt selon vos besoins.  
  
     Comme les applications Windows Forms sont pilotées par événements, vos points d’arrêt sont placés dans le code du gestionnaire d’événements ou dans des méthodes appelées par le code du gestionnaire d’événements. Les points d'arrêt sont généralement placés dans les événements suivants :  
  
    1.  Événements associés à un contrôle, tels que Click, Enter, etc.  
  
    2.  Événements associés au démarrage et à l'arrêt d'une application, tels que Load, Activated, etc.  
  
    3.  Événements de focus et de validation.  
  
     Pour plus d’informations, consultez [Création de gestionnaires d’événements dans les Windows Forms](http://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701).  
  
3.  Sur le **déboguer** menu, cliquez sur **Démarrer**.  
  
4.  Débogage en utilisant les techniques présentées dans [principes fondamentaux du débogueur](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Comment : jeu de Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](http://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)



