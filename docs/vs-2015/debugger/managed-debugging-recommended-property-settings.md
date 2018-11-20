---
title: 'Débogage managé : Paramètres de propriété recommandés | Microsoft Docs'
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
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c82a624e5a2847da5c0f85a9e2ef4180a338a34
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724698"
---
# <a name="managed-debugging-recommended-property-settings"></a>Débogage managé : paramètres de propriété recommandés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Certaines propriétés doivent être définies de la même manière pour tous les scénarios de débogage managé.  
  
 Les tableaux suivants présentent les paramètres de propriété recommandés.  
  
 Les paramètres qui n'y sont pas répertoriés peuvent varier parmi les différents types de projet managés. Par exemple, **Action de démarrage** sera défini différemment dans un projet Windows Forms que dans un [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projet.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Propriétés de configuration sous l'onglet Générer (C#) ou Compiler (Visual Basic)  
  
|**Nom de propriété**|**Paramètre**|  
|-----------------------|-----------------|  
|**Définir la constante DEBUG**|C# et F# : activez la case à cocher. Cela permet à votre application d'utiliser la classe Debug.|  
|**Définir la constante TRACE**|C# et F# : activez la case à cocher. Cela permet à votre application d'utiliser la classe Trace.|  
|**Optimiser le code**|C#, F# et Visual Basic : valeur false. Le code optimisé est plus difficile à déboguer, car les instructions générées ne correspondent pas directement à votre code source. Si vous trouvez que votre programme comporte un bogue visible uniquement dans le code optimisé, vous pouvez activer ce paramètre, mais n’oubliez pas que le code affiché dans le **désassemblage** fenêtre est générée à partir d’une source optimisée qui ne correspond ne peut-être pas à ce que vous voyez dans le Code Éditeur. Pour déboguer le code optimisé, vous devez désactiver [uniquement mon Code](just-my-code.md).<br /><br /> Pour plus d’informations, consultez [des paramètres de projet pour les Configurations Debug c#](../debugger/project-settings-for-csharp-debug-configurations.md) ou [paramètres de projet pour une Configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
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



