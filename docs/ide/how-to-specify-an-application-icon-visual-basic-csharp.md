---
title: Guide pratique pour spécifier une icône d’application (Visual Basic, C#)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7e78bd32bf9c21829adeb04a22cd30abb47a3379
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596136"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Guide pratique pour spécifier une icône d’application (Visual Basic, C#)

La propriété `Icon` d’un projet spécifie le fichier de l’icône (*.ico*) qui est affichée pour l’application compilée dans l’**Explorateur de fichiers** et dans la barre des tâches Windows.

La propriété `Icon` est accessible dans le volet **Application** du **Concepteur de projet**. Elle contient une liste des icônes qui ont été ajoutées à un projet comme ressources ou comme fichiers de contenu.

> [!NOTE]
> Après avoir défini la propriété Icon pour une application, vous pouvez également définir la propriété `Icon` de chaque **Fenêtre** ou **Formulaire** de l’application. Pour plus d'informations sur les icônes de fenêtre pour les applications autonomes Windows Presentation Foundation (WPF), consultez la propriété <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Pour spécifier une icône d'application

1. Dans l’**Explorateur de solutions**, choisissez un nœud de projet (pas le nœud **Solution**).

1. Sur la barre de menu, choisissez **Project** > **Properties**.

1. Quand le **Concepteur de projet** apparaît, choisissez l’onglet **Application**.

1. **(Visual Basic)** &mdash;Dans la liste **Icon,** choisissez un fichier icône *(.ico).*

    **C -**&mdash;Près de la liste **Icône,** choisissez le ** \<bouton Parcourir... >,** puis naviguez à l’emplacement du fichier icône que vous voulez.

## <a name="see-also"></a>Voir aussi

- [Page d’application, Concepteur de projet (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Page d’application, Concepteur de projet (C)](../ide/reference/application-page-project-designer-csharp.md)
