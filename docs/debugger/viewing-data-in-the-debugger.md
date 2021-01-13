---
title: Créer des vues personnalisées de données dans le débogueur | Microsoft Docs
description: Découvrez les différentes façons d’inspecter et de modifier l’état du programme dans le débogueur Visual Studio. Celles-ci incluent les fenêtres automatique et espion, DataTips et visualiseurs.
ms.custom: SEO-VS-2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5acac83a6d461f6b7301ff2bfe89d92dc78d00ee
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149909"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger-c-visual-basic-c"></a>Créer des vues personnalisées de données dans le débogueur Visual Studio (C#, Visual Basic, C++)

Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] débogueur fournit de nombreux outils permettant d’inspecter et de modifier l’état de votre programme. La plupart de ces outils ne fonctionnent qu’en mode arrêt.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Créer des vues personnalisées de données dans des fenêtres de variables et des DataTips

 La plupart des [fenêtres du débogueur](../debugger/debugger-windows.md), telles que les fenêtres **automatique** et **Espion** , vous permettent d’inspecter des variables. Vous pouvez personnaliser la façon dont les types C++, les objets managés et vos propres types sont affichés dans les fenêtres de variables du débogueur et dans les [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Pour plus d’informations, consultez [créer des vues personnalisées d’objets C++](../debugger/create-custom-views-of-native-objects.md) et [créer des vues personnalisées d’objets managés](../debugger/create-custom-views-of-managed-objects.md).

## <a name="create-custom-visualizers"></a>Créer des visualiseurs personnalisés

 Les visualiseurs vous permettent d’afficher le contenu d’un objet ou d’une variable de façon explicite. Dans le débogueur Visual Studio, un visualiseur fait référence aux différentes fenêtres que vous pouvez ouvrir à l’aide de l’icône de loupe ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Icône de visualiseur") . Par exemple, le Visualiseur HTML montre comment une chaîne HTML est interprétée et affichée dans un navigateur. Vous pouvez accéder aux visualiseurs depuis les DataTips, la fenêtre **Espion** , la fenêtre **automatique** et la fenêtre **variables locales** . La boîte de dialogue **Espion express** fournit également un visualiseur. Pour plus d’informations, consultez [créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md).

## <a name="see-also"></a>Voir aussi

- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Fenêtre Commande](../ide/reference/command-window.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
