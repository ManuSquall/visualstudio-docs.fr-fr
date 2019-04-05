---
title: Débogage de Script côté client | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5b8108f0751cbb8848a70b99f23dd3f204ccff2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949792"
---
# <a name="client-side-script-debugging"></a>Débogage de scripts côté client
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur Visual Studio fournit un environnement de débogage complet pour rechercher et corriger les erreurs dans les scripts clients des pages ASP.NET.  
  
## <a name="opening-script-documents"></a>Ouverture de documents de script  
 Vous pouvez afficher des listes de documents de script côté serveur et côté client dans l’ **Explorateur de solutions** . Vous pouvez ouvrir tout document de script à partir de l' **Explorateur de solutions**. Pour plus d'informations, voir [Procédure : afficher les documents de script](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Mappage de point d'arrêt  
 Dans Visual Studio, vous ne pouvez pas déboguer directement le code côté serveur, mais vous pouvez définir un point d'arrêt dans un fichier côté serveur. Visual Studio mappe automatiquement le point d'arrêt à un emplacement correspondant dans le fichier côté client et crée un point d'arrêt mappé dans le code côté client.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>Attachement manuel ou automatique au script  
 Pour commencer le débogage du script dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], le débogueur doit effectuer l'attachement au script que vous souhaitez déboguer. Cela peut se faire manuellement ou automatiquement.  
  
 Vous pouvez effectuer l'attachement manuellement à l'aide de l'interface de débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour choisir un processus de script en cours d'exécution auquel effectuer l'attachement. Pour plus d'informations, voir [Procédure : attacher à un script](../debugger/how-to-attach-to-script.md).  
  
 Le débogueur effectue l'attachement au script automatiquement lorsque l'un des cas suivants se produit :  
  
- Vous avez atteint un jeu de points d'arrêt dans le script.  
  
- Vous avez atteint une instruction `Stop` VBScript ou une instruction `debugger` JScript dans votre code de script.  
  
- Le navigateur ou le serveur rencontre une erreur de syntaxe ou d'exécution dans votre script. Lorsque cela se produit, une boîte de dialogue apparaît et propose de commencer le débogage.  
  
  Lorsque vous effectuez l'attachement au script manuellement, le processus de script continue de s'exécuter jusqu'à ce qu'il soit interrompu d'une manière ou d'une autre. Vous pouvez l'arrêter en sélectionnant **Arrêter** dans le menu **Débogage** .  
  
  Lorsque le débogueur effectue l'attachement automatiquement, l'exécution du script est interrompue à la ligne où le point d'arrêt, l'instruction `Stop` ou `debugger` ou l'erreur s'est produit(e), ou au point où vous avez choisi de lancer le débogage dans Internet Explorer.  
  
  À ce stade, vous pouvez utiliser les fonctions normales de débogage pour commencer le débogage. Par exemple, vous pouvez utiliser les commandes **Step** pour continuer à exécuter votre code ligne par ligne. Vous pouvez utiliser la fenêtre **Pile des appels** pour afficher et contrôler le flux de script. Vous pouvez utiliser les fenêtres de variables ou la fenêtre **Immédiat** pour afficher ou modifier des variables et des propriétés.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Amélioration des messages d'erreur liés au débogage des scripts  
 Visual Studio fournit des messages d’erreur améliorés pour les problèmes courants de débogage de scripts. Ces messages n'apparaissent pas, à moins que vous n'effectuiez l'attachement manuellement à Internet Explorer. Si vous rencontrez une condition d'erreur lorsqu'Internet Explorer est ouvert automatiquement, essayez d'effectuer l'attachement manuellement afin de voir les messages d'erreur.  
  
## <a name="debugging-ajax-script-applications"></a>Débogage d'applications de script AJAX  
 Les applications Web AJAX ont un usage intensif du code de script et représentent un sérieux défi pour le débogage. Pour plus d'informations sur les techniques de débogage AJAX, consultez  
  
 [Debugging and Tracing Ajax Applications Overview](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Limitations du débogage de script](../debugger/limitations-on-script-debugging.md)   
 [Fenêtres de variables](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)   
 [Fenêtre Exécution](../ide/reference/immediate-window.md)   
 [Debugging and Tracing Ajax Applications Overview](http://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)
