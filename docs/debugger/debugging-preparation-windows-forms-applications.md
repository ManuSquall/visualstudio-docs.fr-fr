---
title: "Préparation du débogage : Applications Windows Forms | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [J#], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2d8f123359e4dfff02f05709d8028c2b9fcd3e9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-preparation-windows-forms-applications"></a>Préparation du débogage : applications Windows Forms
Le modèle de projet Windows Forms crée une application Windows Forms. Le débogage de ce type d'application dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est assez simple. Pour plus d’informations, consultez [création d’un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Lorsque vous créez un projet Windows Forms à l'aide du modèle de projet, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée automatiquement les paramètres requis pour les configurations Debug et Release. Si nécessaire, vous pouvez modifier ces paramètres. Ces paramètres peuvent être modifiés dans le  **\<nom du projet > Pages de propriétés** boîte de dialogue (**mon projet** en Visual Basic).  
  
 Pour plus d’informations, consultez [paramètres de propriété recommandés](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Le tableau suivant affiche un paramètre de propriété recommandé supplémentaire.  
  
### <a name="configuration-properties-in-debug-tab"></a>Propriétés de configuration sous l'onglet Déboguer  
  
|**Nom de propriété**|**Paramètre**|  
|-----------------------|-----------------|  
|**Action de démarrage**|-La valeur **démarrer le projet,** la plupart du temps. La valeur **démarrer le programme externe** si vous souhaitez démarrer un autre fichier exécutable lorsque vous démarrez le débogage (habituellement pour déboguer des DLL).|  
  
 Vous pouvez déboguer des applications Windows Forms dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou en établissant un attachement avec une application en cours d'exécution. Pour plus d’informations sur l’attachement, consultez [attacher au processus en cours](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Pour déboguer une application Windows Forms Visual Basic, C# ou F#  
  
1.  Ouvrez le projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Créez des points d'arrêt selon vos besoins.  
  
     Comme les applications Windows Forms sont pilotées par événements, vos points d'arrêt sont placés dans le code du gestionnaire d'événements ou dans des méthodes appelées par le code du gestionnaire d'événements. Les points d'arrêt sont généralement placés dans les événements suivants :  
  
    1.  Événements associés à un contrôle, tels que Click, Enter, etc.  
  
    2.  Événements associés au démarrage et à l'arrêt d'une application, tels que Load, Activated, etc.  
  
    3.  Événements de focus et de validation.  
  
     Pour plus d’informations, consultez [Création de gestionnaires d’événements dans les Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).  
  
3.  Sur le **déboguer** menu, cliquez sur **Démarrer**.  
  
4.  Débogage en utilisant les techniques présentées dans [principes fondamentaux du débogueur](../debugger/debugger-basics.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Comment : jeu de Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Paramètres de projet pour c# les Configurations de débogage](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configuration de débogage de paramètres de projet pour un Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](/dotnet/framework/winforms/index)