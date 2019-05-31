---
title: 'Procédure : Mettre à jour de la barre d’état | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f1ba62fc5147eb679e6d6a64685b367aafacae4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324797"
---
# <a name="how-to-update-the-status-bar"></a>Procédure : Mettre à jour la barre d’état
Le **barre d’état** une barre de contrôle ne se trouve en bas de nombreuses fenêtres d’application qui contient un ou plusieurs lignes de texte d’état ou des indicateurs.

## <a name="to-update-the-status-bar"></a>Pour mettre à jour de la barre d’état

1. Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> sur chaque objet de vue individuelle (DocView) fournies par votre éditeur, comme une vue de formulaire et un mode code.

2. Lorsque l’IDE appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, mettre à jour les informations contenues dans le **barre d’état** en appelant les méthodes de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.

    > [!NOTE]
    > Les appels IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> uniquement lorsque votre fenêtre de document est initialement activée. Pour le reste du temps que votre fenêtre de document est actif, vous devez mettre à jour le **barre d’état** informations en tant que l’état de vos modifications de l’éditeur.

## <a name="robust-programming"></a>Programmation fiable
 Un **barre d’état** contient quatre champs distincts :

- Texte d’état

- Barre de progression

- Icône animée

- Informations d’éditeur

  Pour plus d’informations, consultez [barres d’état](/cpp/mfc/status-bars).

  L’IDE appelle automatiquement la <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> méthode de votre <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implémentation lorsque votre fenêtre de document est activée.

  L’implémenteur de VSPackage est chargé de la mise à jour le texte d’état dans la barre d’état. L’IDE réinitialise cette chaîne pour « Prêt » si le champ de texte d’état a la valeur texte vide (" ») en période d’inactivité.

## <a name="see-also"></a>Voir aussi
- [Barres d’état](/cpp/mfc/status-bars)