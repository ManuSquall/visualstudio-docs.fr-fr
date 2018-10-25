---
title: 'Préparation du débogage : Applications Windows Forms | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c4dc7cb560e6ae652474d16e003eafb352643ea
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951065"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Préparation du débogage : applications Windows Forms
Le modèle de projet Windows Forms crée une application Windows Forms. Le débogage de ce type d'application dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est assez simple. Pour plus d’informations, consultez [création d’un projet d’Application Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).  
  
 Lorsque vous créez un projet Windows Forms à l’aide du modèle de projet, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée automatiquement les paramètres requis pour les configurations Debug et Release. Si nécessaire, vous pouvez modifier ces paramètres. Ces paramètres peuvent être modifiés dans le  **\<nom_projet > Pages de propriétés** boîte de dialogue (**mon projet** en Visual Basic).  
  
 Pour plus d’informations, consultez [paramètres de propriété recommandés](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Le tableau suivant affiche un paramètre de propriété recommandé supplémentaire.  
  
### <a name="configuration-properties-in-debug-tab"></a>Propriétés de configuration sous l'onglet Déboguer  
  
|**Nom de propriété**|**Paramètre**|  
|-----------------------|-----------------|  
|**Action de démarrage**|-La valeur **projet de démarrage,** la plupart du temps. La valeur **démarrer le programme externe** si vous souhaitez démarrer un autre fichier exécutable lorsque vous démarrez le débogage (habituellement pour déboguer des DLL).|  
  
 Vous pouvez déboguer des applications Windows Forms dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou en établissant un attachement avec une application en cours d’exécution. Pour plus d’informations sur l’attachement, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Pour déboguer une application Windows Forms Visual Basic, C# ou F#  
  
1. Ouvrez le projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2. Créez des points d'arrêt selon vos besoins.  
  
    Comme les applications Windows Forms sont pilotées par événements, vos points d’arrêt sont placés dans le code du gestionnaire d’événements ou dans des méthodes appelées par le code du gestionnaire d’événements. Les points d'arrêt sont généralement placés dans les événements suivants :  
  
   1. Événements associés à un contrôle, tels que Click, Enter, etc.  
  
   2. Événements associés au démarrage et à l'arrêt d'une application, tels que Load, Activated, etc.  
  
   3. Événements de focus et de validation.  
  
      Pour plus d’informations, consultez [Création de gestionnaires d’événements dans les Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).  
  
3. Sur le **déboguer** menu, cliquez sur **Démarrer**.  
  
4. Débogage en utilisant les techniques présentées dans [principes fondamentaux du débogueur](../debugger/getting-started-with-the-debugger.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Comment : jeu de Configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Paramètres de projet pour des configurations Debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](/dotnet/framework/winforms/index)