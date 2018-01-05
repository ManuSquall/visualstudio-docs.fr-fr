---
title: "Débogage de Script côté client | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 401ee40e2d296cbef041cb56568b639d05835f04
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="client-side-script-debugging"></a>Débogage de scripts côté client
Le débogueur Visual Studio fournit un environnement de débogage complet pour rechercher et corriger les erreurs dans les scripts clients des pages ASP.NET.  
  
## <a name="opening-script-documents"></a>Ouverture de documents de script  
 Vous pouvez afficher des listes de documents de script côté serveur et côté client dans l’ **Explorateur de solutions** . Vous pouvez ouvrir tout document de script à partir de l' **Explorateur de solutions**. Pour plus d'informations, consultez [How to: View Script Documents](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Mappage de point d'arrêt  
 Dans Visual Studio, vous ne pouvez pas déboguer directement le code côté serveur, mais vous pouvez définir un point d'arrêt dans un fichier côté serveur. Visual Studio mappe automatiquement le point d'arrêt à un emplacement correspondant dans le fichier côté client et crée un point d'arrêt mappé dans le code côté client.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>Attachement manuel ou automatique au script  
 Pour commencer le débogage du script dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], le débogueur doit effectuer l'attachement au script que vous souhaitez déboguer. Cela peut se faire manuellement ou automatiquement.  
  
 Vous pouvez effectuer l'attachement manuellement à l'aide de l'interface de débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour choisir un processus de script en cours d'exécution auquel effectuer l'attachement. Pour plus d'informations, consultez [How to: Attach to Script](../debugger/how-to-attach-to-script.md).  
  
 Le débogueur effectue l'attachement au script automatiquement lorsque l'un des cas suivants se produit :  
  
-   Vous avez atteint un jeu de points d'arrêt dans le script.  
  
-   Vous avez atteint une instruction `Stop` VBScript ou une instruction `debugger` JScript dans votre code de script.  
  
-   Le navigateur ou le serveur rencontre une erreur de syntaxe ou d'exécution dans votre script. Lorsque cela se produit, une boîte de dialogue apparaît et propose de commencer le débogage.  
  
 Lorsque vous effectuez l'attachement au script manuellement, le processus de script continue de s'exécuter jusqu'à ce qu'il soit interrompu d'une manière ou d'une autre. Vous pouvez l'arrêter en sélectionnant **Arrêter** dans le menu **Débogage** .  
  
 Lorsque le débogueur effectue l'attachement automatiquement, l'exécution du script est interrompue à la ligne où le point d'arrêt, l'instruction `Stop` ou `debugger` ou l'erreur s'est produit(e), ou au point où vous avez choisi de lancer le débogage dans Internet Explorer.  
  
 À ce stade, vous pouvez utiliser les fonctions normales de débogage pour commencer le débogage. Par exemple, vous pouvez utiliser les commandes **Step** pour continuer à exécuter votre code ligne par ligne. Vous pouvez utiliser la fenêtre **Pile des appels** pour afficher et contrôler le flux de script. Vous pouvez utiliser les fenêtres de variables ou la fenêtre **Immédiat** pour afficher ou modifier des variables et des propriétés.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Amélioration des messages d'erreur liés au débogage des scripts  
 Visual Studio fournit des messages d’erreur améliorés pour les problèmes courants de débogage de scripts. Ces messages n'apparaissent pas, à moins que vous n'effectuiez l'attachement manuellement à Internet Explorer. Si vous rencontrez une condition d'erreur lorsqu'Internet Explorer est ouvert automatiquement, essayez d'effectuer l'attachement manuellement afin de voir les messages d'erreur.  
  
## <a name="debugging-ajax-script-applications"></a>Débogage d'applications de script AJAX  
 Les applications Web AJAX ont un usage intensif du code de script et représentent un sérieux défi pour le débogage. Pour plus d'informations sur les techniques de débogage AJAX, consultez  
  
 [Debugging and Tracing Ajax Applications Overview](http://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage des Applications ASP.NET et AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Limitations sur le débogage de Script](../debugger/limitations-on-script-debugging.md)   
 [Fenêtres de variables](../debugger/debugger-windows.md)   
 [Fenêtre Exécution](../ide/reference/immediate-window.md)   
 [Vue d’ensemble des Applications Ajax de traçage et de débogage](http://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)