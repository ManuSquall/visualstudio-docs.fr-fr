---
title: 'Comment : déclencher des événements lorsque l’éditeur perd le Focus | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2462e41470b72c63f5c96a69d2776af2a640c372
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501791"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Comment : déclencher des événements lorsque l’éditeur perd le Focus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : incendie événements lors de l’éditeur perd le Focus](https://docs.microsoft.com/visualstudio/extensibility/how-to-fire-events-when-the-editor-loses-focus).  
  
Il est parfois nécessaire de savoir quand un éditeur perd le focus sur le frame de fenêtre. Par exemple, vous devrez peut-être extraire du code à partir d’une fenêtre de code une fois que l’éditeur de focus n’est plus sur celui-ci. La procédure suivante fournit les étapes à suivre pour recevoir une notification de l’éditeur perd le focus.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Pour déclencher un événement en réponse à un éditeur perd le focus  
  
1.  Surveiller les événements de sélection en obtenant un <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> à partir de l’objet <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>.  
  
2.  Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> et fournir votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objet.  
  
3.  Dans votre appel à <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>, recherchez `elementid==SEID_WindowFrame`.  
  
4.  Test du `varValueNew` paramètre pour deux choses :  
  
    1.  Le frame de fenêtre que vous recherchez.  
  
    2.  Le point auquel votre programme perd la sélection pour ce frame de fenêtre.

