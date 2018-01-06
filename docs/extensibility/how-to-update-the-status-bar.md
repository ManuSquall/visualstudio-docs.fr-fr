---
title: "Comment : mettre à jour de la barre d’état | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 76801810aafa3bd4048776ca38385ad1cf508d94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-the-status-bar"></a>Comment : mettre à jour de la barre d’état
Le **barre d’état** une barre de contrôle se trouve en bas de nombreuses fenêtres d’application qui contient une ou plusieurs lignes de texte d’état ou des indicateurs.  
  
### <a name="to-update-the-status-bar"></a>Pour mettre à jour de la barre d’état  
  
1.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> sur chaque objet de vue individuelle (DocView) par votre éditeur, comme une vue de formulaire et un mode code.  
  
2.  Lorsque l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, mettre à jour les informations contenues dans le **barre d’état** en appelant les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  Les appels IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> uniquement lorsque votre fenêtre de document est initialement activée. Pour le reste de la durée pendant laquelle votre fenêtre de document est actif, vous devez mettre à jour le **barre d’état** informations en tant que l’état de vos modifications de l’éditeur.  
  
## <a name="robust-programming"></a>Programmation fiable  
 A **barre d’état** contient quatre champs distincts :  
  
-   Texte d’état  
  
-   Barre de progression  
  
-   Icône animée  
  
-   Informations de l’éditeur  
  
 Pour plus d’informations, consultez [barres d’état](/cpp/mfc/status-bars).  
  
 L’IDE appelle automatiquement la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> méthode de votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implémentation lorsque la fenêtre de document est activée.  
  
 Le responsable de l’implémentation VSPackage est responsable de la mise à jour le texte d’état dans la barre d’état. L’IDE réinitialise cette chaîne à l’état « prêt » si le champ de texte d’état a la valeur texte vide (« ») au moment de l’inactivité.  
  
## <a name="see-also"></a>Voir aussi  
 [Barres d’état](/cpp/mfc/status-bars)