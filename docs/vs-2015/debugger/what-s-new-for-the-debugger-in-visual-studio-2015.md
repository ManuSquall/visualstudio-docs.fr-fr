---
title: Quelles sont les nouveautés du débogueur dans Visual Studio 2015 | Microsoft Docs
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
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: 86
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 743875ef4ab7582bd4c1a254c82f168b96ba8208
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188615"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2015"></a>Nouveautés du débogueur dans Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour plus d’informations sur toutes les nouveautés en matière de débogage et de diagnostics dans Visual Studio 2015, consultez les [Notes de publication de Visual Studio 2015 Update 1](https://www.visualstudio.com/news/vs2015-update1-vs#debug).  
  
 Pour plus d’informations sur toutes les nouveautés en matière de débogage et de diagnostics dans Visual Studio 2015 RTM, consultez les [Notes de publication de Visual Studio 2015](https://www.visualstudio.com/news/vs2015-vs#debug).  
  
## <a name="visual-studio-2015-update-1-changes"></a>Modifications apportées à Visual Studio 2015 Update 1  
 La fonctionnalité C++ Modifier & Continuer offre davantage de fonctionnalités. Pour plus d’informations, consultez [Modifier & Continuer (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).  
  
 Pour déboguer les violations d’accès Visual C++, une nouvelle boîte de dialogue d’exception spécifie le pointeur à l’origine de l’exception. Pour plus d’informations, consultez [How Can I Debug an Access Violation?](../debugger/how-can-i-debug-an-access-violation-q.md) et [Improvement to Debugging C++ Access Violations in Visual Studio 2015 Update 1](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/improvement-to-debugging-c-access-violations-in-visual-studio-2015-update-1.aspx)  
  
## <a name="visual-studio-2015-rtm-debugger-ui-and-hotkey-changes"></a>Interface utilisateur du débogueur et changements de touches d’accès rapide dans Visual Studio 2015 RTM  
 Des modifications significatives ont été apportées à l’interface utilisateur relative aux exceptions et aux points d’arrêt.  
  
### <a name="breakpoints"></a>Points d’arrêt  
 Dans Visual Studio 2015, la fenêtre **Paramètres de point d’arrêt** constitue une nouvelle façon de configurer des points d’arrêt.  
  
 Voici un résumé des principales fenêtres de points d’arrêt et touches d’accès rapide :  
  
|Fonctionnalité|Emplacement du menu|Touche d’accès rapide|  
|-------------|-------------------|------------|  
|Nouveau point d’arrêt, basculer le point d’arrêt|**Déboguer / basculer le point d’arrêt**<br /><br /> Menu contextuel dans l’éditeur/ **Insérer un point d’arrêt**<br /><br /> Cliquez dans la marge de gauche|F9|  
|Nouveau point d’arrêt sur fonction|**Déboguer / nouveau point d’arrêt / point d’arrêt de fonction**|Dans Visual Studio 2015 RTM (avec aucune mise à jour), utilisez ALT + F9, B<br /><br /> Dans Visual Studio 2015 Update 1 et versions ultérieures, utilisez CTRL + B|  
|Fenêtre**Points d’arrêt** |**Déboguer / Windows / points d’arrêt**|CTRL+ALT+B|  
|**Paramètres de point d’arrêt**, **Conditions**|Menu contextuel sur le point d’arrêt/ **Conditions**|ALT+F9, C|  
|**Paramètres de point d’arrêt**, **Actions**|Menu contextuel sur le point d’arrêt/ **Actions**|Aucune touche d’accès rapide|  
  
 Pour plus d’informations, consultez les articles suivants :  
  
1.  [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)  
  
2.  [Nouvelle expérience de Configuration de point d’arrêt](http://blogs.msdn.com/b/visualstudioalm/archive/2014/10/06/new-breakpoint-configuration-experience.aspx)  
  
3.  [Expérience de Configuration de points d’arrêt](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)  
  
### <a name="exception-settings"></a>Paramètres d’exception  
 La nouvelle fenêtre **Paramètres d’exception** vous permet de spécifier le type de gestion des exceptions souhaité pour des exceptions uniques ou des catégories d’exceptions.  
  
|Fonctionnalité|Emplacement du menu|Touche d’accès rapide|  
|-------------|-------------------|------------|  
|Fenêtre**Paramètres d’exception** |**Déboguer / Windows / Paramètres d’Exception**|CTRL+ALT+E|  
  
 Pour plus d’informations, consultez les articles suivants :  
  
1.  [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)  
  
2.  [La nouvelle fenêtre d’Exceptions](http://blogs.msdn.com/b/visualstudioalm/archive/2015/02/23/the-new-exception-settings-window-in-visual-studio-2015.aspx)  
  
### <a name="edit-and-continue"></a>Modifier & Continuer  
 Dans Visual Studio 2015, vous pouvez définir l’option Modifier &amp; Continuer dans la page **Outils/Options/Débogage/Général** . Dans les versions précédentes, ces paramètres se trouvaient dans une catégorie d’options distincte.  
  
### <a name="attach-to-process"></a>Attacher au processus  
 Dans Visual Studio 2015, la commande Attacher au processus est disponible uniquement dans le menu Déboguer. Dans la version précédente, elle était également disponible dans le menu Outils. La touche d’accès rapide CTRL+ALT+P fonctionne dans toutes les versions.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)



