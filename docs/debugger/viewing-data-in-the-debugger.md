---
title: Créer des vues personnalisées des données dans le débogueur | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2018
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 59e6c1879d5463682ee41d60e3928fce85c74a8d
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305141"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Créer des vues personnalisées des données dans le débogueur Visual Studio
Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] débogueur fournit de nombreux outils pour examiner et de modifier l’état de votre programme. La plupart de ces outils ne fonctionnent qu’en mode arrêt.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Créer des vues personnalisées des données dans les fenêtres de variables et les DataTips
 Un grand nombre de la [fenêtres du débogueur](../debugger/debugger-windows.md), telles que la **automatique** et **espion** windows, permettent d’inspecter des variables. Vous pouvez personnaliser les types de mode natifs, des objets gérés, et vos propres types sont affichés dans les fenêtres de variables du débogueur et dans [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Pour plus d’informations, consultez [créer des vues personnalisées d’objets natifs](../debugger/create-custom-views-of-native-objects.md) et [créer des vues personnalisées d’objets gérés](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Créer des visualiseurs personnalisés  
 Visualiseurs permettent d’afficher le contenu d’un objet ou une variable de manière explicite. Dans le débogueur Visual Studio, un visualiseur fait référence à des fenêtres différentes que vous pouvez ouvrir à l’aide de la loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur") icône. Par exemple, le visualiseur HTML montre comment une chaîne au format HTML sera interprétée et affichée dans un navigateur. Vous pouvez accéder aux visualiseurs depuis les DataTips, la **espion** fenêtre, le **automatique** fenêtre et le **variables locales** fenêtre. Le **Espion express** boîte de dialogue fournit également un visualiseur. Pour plus d’informations, consultez [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base du débogueur](../debugger/getting-started-with-the-debugger.md)   
 [Commande, fenêtre](../ide/reference/command-window.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)