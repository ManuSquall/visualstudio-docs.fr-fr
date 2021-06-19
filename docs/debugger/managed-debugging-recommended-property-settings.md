---
title: Paramètres de propriété du débogueur recommandés pour C#, VB | Microsoft Docs
description: Consultez les paramètres de propriété de génération et de compilation qui doivent être identiques pour tous les débogages managés. Les autres paramètres peuvent varier en fonction du type de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c2262194dbb6a8f4b0a47b4fcfc7f9f696c60167
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390396"
---
# <a name="managed-debugging-recommended-property-settings"></a>Débogage managé : paramètres de propriété recommandés
Certaines propriétés doivent être définies de la même manière pour tous les scénarios de débogage managé.

 Les tableaux suivants présentent les paramètres de propriété recommandés.

 Les paramètres qui n'y sont pas répertoriés peuvent varier parmi les différents types de projet managés. Par exemple, **Action de démarrage** sera défini différemment dans un projet Windows Forms et dans un projet [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].

### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Propriétés de configuration sous l'onglet Générer (C#) ou Compiler (Visual Basic)

|**Nom de la propriété**|**Paramètre**|
|-----------------------|-----------------|
|**Définir la constante DEBUG**|C# et F# : activez la case à cocher. Cela permet à votre application d'utiliser la classe Debug.|
|**Définir la constante TRACE**|C# et F# : activez la case à cocher. Cela permet à votre application d'utiliser la classe Trace.|
|**Optimiser le code**|C#, F# et Visual Basic : valeur false. Le code optimisé est plus difficile à déboguer, car les instructions générées ne correspondent pas directement à votre code source. Si vous constatez que votre programme comporte un bogue visible uniquement dans le code optimisé, vous pouvez activer ce paramètre, mais rappelez-vous que le code affiché dans la fenêtre **Code machine** est généré à partir d’une source optimisée qui ne correspond peut-être pas à ce que vous voyez dans l’éditeur de code. Pour déboguer du code optimisé, vous devez désactiver l'option Uniquement mon code. (Consultez [Limiter le pas à pas à Uniquement mon code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Pour plus d’informations, consultez [paramètres du projet pour les configurations de débogage C#](../debugger/project-settings-for-csharp-debug-configurations.md) ou [paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|
|**Chemin de sortie**|Affectez la valeur bin\Debug\\.|
|**Options avancées de compilation**|Visual Basic uniquement. Cliquez sur **Avancé** pour définir les propriétés avancées décrites dans le tableau suivant.|

### <a name="advanced-compiler-settings-dialog-box"></a>Boîte de dialogue Paramètres avancés du compilateur

|**Nom de la propriété**|**Paramètre**|
|-----------------------|-----------------|
|**Activer les optimisations**|Affectez la valeur false pour les raisons spécifiées dans l’option **optimiser le code** dans le tableau précédent.|
|**Générer des informations de débogage**|Activez cette case à cocher pour que l'indicateur /DEBUG soit défini pendant la compilation, ce qui génèrera les informations nécessaires pour faciliter le débogage.|
|**Définir la constante DEBUG**|Activez cette case à cocher pour définir la constante `DEBUG` qui permet à votre application d'utiliser la classe <xref:System.Diagnostics.Debug>.|
|**Définir la constante TRACE**|Activez cette case à cocher pour définir la constante `TRACE` qui permet à votre application d'utiliser la classe <xref:System.Diagnostics.Trace>.|

## <a name="see-also"></a>Voir aussi
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)