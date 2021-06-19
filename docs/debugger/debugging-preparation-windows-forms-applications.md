---
title: Préparer le débogage des applications Windows Forms | Microsoft Docs
description: Suivez les étapes de préparation pour déboguer des applications Windows Forms, qui sont créées par le modèle de projet Windows Forms dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2181fe0b0189b0c0472f4d7cadd6a7c8e172a9b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387747"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Préparation du débogage : applications Windows Forms

Le modèle de projet d’application Windows Forms crée une application Windows Forms. Le débogage de ce type d'application dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] est assez simple. Pour plus d’informations sur la création d’un projet de ce type, consultez [créer une application Windows Form](../ide/create-csharp-winform-visual-studio.md).

 Lorsque vous créez un projet Windows Forms à l’aide du modèle de projet, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crée automatiquement les paramètres requis pour les configurations Debug et Release. Si nécessaire, vous pouvez modifier ces paramètres. Ces paramètres peuvent être modifiés dans la boîte de dialogue **\<project name> pages de propriétés** (**mon projet** dans Visual Basic).

 Pour plus d’informations, consultez [paramètres de propriété recommandés](../debugger/managed-debugging-recommended-property-settings.md).

 Le tableau suivant affiche un paramètre de propriété recommandé supplémentaire.

### <a name="configuration-properties-in-debug-tab"></a>Propriétés de configuration sous l'onglet Déboguer

|**Nom de la propriété**|**Paramètre**|
|-----------------------|-----------------|
|**Action de démarrage**|-   La valeur est la plupart du temps **Démarrer le projet**. Affectez la valeur **Démarrer le programme externe** si vous souhaitez démarrer un autre fichier exécutable quand vous commencez le débogage (habituellement pour déboguer des DLL).|

 Vous pouvez déboguer des applications Windows Forms dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou en établissant un attachement avec une application en cours d’exécution. Pour plus d’informations sur l’attachement, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Pour déboguer une application Windows Forms Visual Basic, C# ou F#

1. Ouvrez le projet dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

2. Créez des points d'arrêt selon vos besoins.

    Comme les applications Windows Forms sont pilotées par événements, vos points d’arrêt sont placés dans le code du gestionnaire d’événements ou dans des méthodes appelées par le code du gestionnaire d’événements. Les points d'arrêt sont généralement placés dans les événements suivants :

   1. Événements associés à un contrôle, tels que Click, Enter, etc.

   2. Événements associés au démarrage et à l'arrêt d'une application, tels que Load, Activated, etc.

   3. Événements de focus et de validation.

      Pour plus d’informations, consultez [Création de gestionnaires d’événements dans les Windows Forms](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).

3. Dans le menu **Déboguer** , cliquez sur **Démarrer**.

4. Déboguez à l’aide des techniques abordées dans [premier aperçu du débogueur](../debugger/debugger-feature-tour.md).

## <a name="see-also"></a>Voir aussi
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Comment : définir des configurations Debug et Release](../debugger/how-to-set-debug-and-release-configurations.md)
- [Paramètres de projet pour les configurations de débogage C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Joindre aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)