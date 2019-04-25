---
title: 'Procédure : Déclencher des événements lorsque l’éditeur perd le Focus | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec28c704cb8fecb38395c0c7b3f3e3d22ead389b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052894"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Procédure : Déclencher des événements lorsque l’éditeur perd le focus
Il est parfois nécessaire de savoir quand un éditeur perd le focus sur le frame de fenêtre. Par exemple, vous devrez peut-être extraire du code à partir d’une fenêtre de code une fois que l’éditeur de focus n’est plus sur celui-ci. La procédure suivante fournit les étapes à suivre pour recevoir une notification de l’éditeur perd le focus.

## <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Pour déclencher un événement en réponse à un éditeur perd le focus

1. Surveiller les événements de sélection en obtenant un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> à partir de l’objet <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.

2. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> et fournir votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objet.

3. Dans votre appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, recherchez `elementid==SEID_WindowFrame`.

4. Test du `varValueNew` paramètre pour deux choses :

    1. Le frame de fenêtre que vous recherchez.

    2. Le point auquel votre programme perd la sélection pour ce frame de fenêtre.