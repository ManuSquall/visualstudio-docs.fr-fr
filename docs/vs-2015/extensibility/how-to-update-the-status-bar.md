---
title: 'Comment : mettre à jour la barre d’État | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703144"
---
# <a name="how-to-update-the-status-bar"></a>Guide pratique pour mettre à jour la barre d’état
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La **barre d’État** est une barre de contrôle située en bas de nombreuses fenêtres d’application qui contient un ou plusieurs indicateurs ou lignes de texte d’État.  
  
### <a name="to-update-the-status-bar"></a>Pour mettre à jour la barre d’État  
  
1. Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> sur chaque objet de vue (docview) fourni par votre éditeur, par exemple en mode formulaire et en mode Code.  
  
2. Lorsque l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> , mettez à jour les informations dans la **barre d’État** en appelant les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
    > [!NOTE]
    > L’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> uniquement lorsque la fenêtre de document est initialement activée. Pour le reste du temps d’activité de la fenêtre de document, vous devez mettre à jour les informations de la **barre d’État** lorsque l’état de votre éditeur change.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Une **barre d’État** contient quatre champs distincts :  
  
- Texte d'état  
  
- Barre de progression  
  
- Icône animée  
  
- Informations sur l’éditeur  
  
  Pour plus d’informations, consultez [barres d’État](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  L’IDE appelle automatiquement la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> méthode de votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implémentation lorsque votre fenêtre de document est activée.  
  
  L’implémenteur VSPackage est chargé de mettre à jour le texte d’État dans la barre d’État. L’IDE réinitialise cette chaîne à « READY » si le champ de texte d’État est défini sur un texte vide («») au moment de l’inactivité.  
  
## <a name="see-also"></a>Voir aussi  
 [Barres d’État](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
