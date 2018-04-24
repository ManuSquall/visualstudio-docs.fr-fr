---
title: Créer des vues personnalisées de données dans le débogueur | Documents Microsoft
ms.custom: ''
ms.date: 06/27/2017
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
ms.openlocfilehash: 5ccf8b24618aeb2cb4b8774786bf96b2184f5da9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Créer des vues personnalisées de données dans le débogueur Visual Studio
Le débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fournit tout un ensemble d’outils permettant d’examiner et de modifier l’état de votre programme. La plupart de ces outils ne fonctionnent qu’en mode arrêt.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Créer des vues personnalisées de données dans les fenêtres de variables et les DataTips
 Un grand nombre de la [fenêtres du débogueur](../debugger/debugger-windows.md), telles que la **automatique** et **espion** windows, permettent d’inspecter des variables pendant que vous déboguez. Vous pouvez personnaliser l’affichage des types natifs et des objets gérés dans les fenêtres de variables du débogueur et dans [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Cela peut être utile d’afficher les types que vous créez dans vos propres applications. Pour plus d’informations, consultez [créer des vues personnalisées d’objets natifs](../debugger/create-custom-views-of-native-objects.md) et [créer des vues personnalisées d’objets gérés](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Créer des visualiseurs personnalisés  
 Les visualiseurs vous permettent de vous permet d’afficher le contenu d’un objet ou une variable de manière explicite. Dans le débogueur Visual Studio, un visualiseur fait référence aux différentes fenêtres que vous pouvez ouvrir à l’aide de l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "icône de visualiseur"). Vous pouvez, par exemple, utiliser le visualiseur HTML pour voir une chaîne HTML telle qu’elle sera interprétée et affichée dans un navigateur. Vous pouvez accéder aux visualiseurs depuis les DataTips, la fenêtre **Espion** , la fenêtre **Automatique** , la fenêtre **Variables locales** ou la boîte de dialogue **Espion express** . Pour plus d’informations, consultez [créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [Fenêtre Commande](../ide/reference/command-window.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)