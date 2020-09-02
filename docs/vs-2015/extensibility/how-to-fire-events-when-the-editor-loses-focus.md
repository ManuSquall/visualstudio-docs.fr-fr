---
title: 'Comment : déclencher des événements lorsque l’éditeur perd le focus | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204192"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Guide pratique pour déclencher des événements quand l’éditeur perd le focus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il est parfois nécessaire de savoir quand un éditeur perd le focus sur le cadre de la fenêtre. Par exemple, vous devrez peut-être extraire le code à partir d’une fenêtre de code une fois que l’éditeur ne se concentre plus dessus. La procédure suivante fournit les étapes à suivre pour recevoir la notification de l’éditeur qui perd le focus.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Pour déclencher un événement en réponse à un éditeur qui perd le focus  
  
1. Surveiller les événements de sélection en obtenant un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> objet à partir de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
2. Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> et fournissez votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objet.  
  
3. Dans votre appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> , recherchez `elementid==SEID_WindowFrame` .  
  
4. Testez le `varValueNew` paramètre pour deux choses :  
  
    1. Frame de fenêtre que vous recherchez.  
  
    2. Point auquel votre programme perd la sélection dans ce frame de fenêtre.
