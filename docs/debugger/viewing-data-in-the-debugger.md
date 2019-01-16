---
title: Créer des vues personnalisées des données dans le débogueur | Microsoft Docs
ms.date: 01/09/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e5c5466515e0e58fd94d7a949b04d060a90925d1
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227224"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Créer des vues personnalisées des données dans le débogueur Visual Studio (C#, Visual Basic, C++)

Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] débogueur fournit de nombreux outils pour examiner et de modifier l’état de votre programme. La plupart de ces outils ne fonctionnent qu’en mode arrêt.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Créer des vues personnalisées des données dans les fenêtres de variables et les DataTips

 Un grand nombre de la [fenêtres du débogueur](../debugger/debugger-windows.md), telles que la **automatique** et **espion** windows, permettent d’inspecter des variables. Vous pouvez personnaliser les types de mode natifs, des objets gérés, et vos propres types sont affichés dans les fenêtres de variables du débogueur et dans [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Pour plus d’informations, consultez [créer des vues personnalisées d’objets natifs](../debugger/create-custom-views-of-native-objects.md) et [créer des vues personnalisées d’objets](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Créer des visualiseurs personnalisés

 Visualiseurs permettent d’afficher le contenu d’un objet ou une variable de manière explicite. Dans le débogueur Visual Studio, un visualiseur fait référence à des fenêtres différentes que vous pouvez ouvrir à l’aide de la loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur") icône. Par exemple, le visualiseur HTML montre comment une chaîne au format HTML sera interprétée et affichée dans un navigateur. Vous pouvez accéder aux visualiseurs depuis les DataTips, la **espion** fenêtre, le **automatique** fenêtre et le **variables locales** fenêtre. Le **Espion express** boîte de dialogue fournit également un visualiseur. Pour plus d’informations, consultez [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Voir aussi

 [Tout d’abord examiner le débogueur](../debugger/debugger-feature-tour.md) [fenêtre de commande](../ide/reference/command-window.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)