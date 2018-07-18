---
title: 'Le débogage managé : Paramètres de propriété recommandés | Documents Microsoft'
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
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e1c4b725871012f1fbf2c80f3e978f133d4db5b0
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476440"
---
# <a name="managed-debugging-recommended-property-settings"></a>Débogage managé : paramètres de propriété recommandés
Certaines propriétés doivent être définies de la même manière pour tous les scénarios de débogage managé.  
  
 Les tableaux suivants présentent les paramètres de propriété recommandés.  
  
 Les paramètres qui n'y sont pas répertoriés peuvent varier parmi les différents types de projet managés. Par exemple, **Action de démarrage** sera défini différemment dans un projet Windows Forms que dans un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projet.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Propriétés de configuration sous l'onglet Générer (C#) ou Compiler (Visual Basic)  
  
|**Nom de propriété**|**Paramètre**|  
|-----------------------|-----------------|  
|**Définir la constante DEBUG**|C# et F# : activez la case à cocher. Cela permet à votre application d'utiliser la classe Debug.|  
|**Définir la constante TRACE**|C# et F# : activez la case à cocher. Cela permet à votre application d'utiliser la classe Trace.|  
|**Optimiser le code**|C#, F# et Visual Basic : valeur false. Le code optimisé est plus difficile à déboguer, car les instructions générées ne correspondent pas directement à votre code source. Si vous trouvez que votre programme comporte un bogue visible uniquement dans le code optimisé, vous pouvez activer ce paramètre, mais n’oubliez pas que le code affiché dans le **code machine** fenêtre est généré à partir d’une source optimisée qui ne correspond ne peut-être pas à ce que vous voyez dans le Code Éditeur. Pour déboguer du code optimisé, vous devez désactiver l'option Uniquement mon code. (Consultez [limiter le pas à pas à uniquement mon Code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code)).<br /><br /> Pour plus d’informations, consultez [des paramètres de projet pour les Configurations Debug c#](../debugger/project-settings-for-csharp-debug-configurations.md) ou [paramètres de projet pour une Configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Chemin de sortie**|La valeur bin\Debug\\.|  
|**Options avancées de compilation**|Visual Basic uniquement. Cliquez sur **avancé** pour définir les propriétés avancées qui sont décrites dans le tableau suivant.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Boîte de dialogue Paramètres avancés du compilateur  
  
|**Nom de propriété**|**Paramètre**|  
|-----------------------|-----------------|  
|**Activer les optimisations**|La valeur false pour les raisons spécifiées dans le **optimiser le code** option dans le tableau précédent.|  
|**Générer des informations de débogage**|Activez cette case à cocher pour que l'indicateur /DEBUG soit défini pendant la compilation, ce qui génèrera les informations nécessaires pour faciliter le débogage.|  
|**Définir la constante DEBUG**|Activez cette case à cocher pour définir la constante `DEBUG` qui permet à votre application d'utiliser la classe <xref:System.Diagnostics.Debug>.|  
|**Définir la constante TRACE**|Activez cette case à cocher pour définir la constante `TRACE` qui permet à votre application d'utiliser la classe <xref:System.Diagnostics.Trace>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)