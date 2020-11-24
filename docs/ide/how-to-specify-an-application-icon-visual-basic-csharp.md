---
title: Guide pratique pour spécifier une icône d’application (Visual Basic, C#)
description: Découvrez comment utiliser la propriété Icon pour spécifier l’icône que l’Explorateur de fichiers et la barre des tâches Windows affichent pour l’application compilée.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 34405fd52b49e89c2fa0fc95ec1268448bad3061
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596909"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Guide pratique pour spécifier une icône d’application (Visual Basic, C#)

La propriété `Icon` d’un projet spécifie le fichier de l’icône (*.ico*) qui est affichée pour l’application compilée dans l’**Explorateur de fichiers** et dans la barre des tâches Windows.

La propriété `Icon` est accessible dans le volet **Application** du **Concepteur de projet**. Elle contient une liste des icônes qui ont été ajoutées à un projet comme ressources ou comme fichiers de contenu.

> [!NOTE]
> Après avoir défini la propriété Icon pour une application, vous pouvez également définir la propriété `Icon` de chaque **Fenêtre** ou **Formulaire** de l’application. Pour plus d'informations sur les icônes de fenêtre pour les applications autonomes Windows Presentation Foundation (WPF), consultez la propriété <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Pour spécifier une icône d'application

1. Dans l’**Explorateur de solutions**, choisissez un nœud de projet (pas le nœud **Solution**).

1. Dans la barre de menus, choisissez Propriétés du **projet**  >  **Properties**.

1. Quand le **Concepteur de projet** apparaît, choisissez l’onglet **Application**.

1. **(Visual Basic)** &mdash; Dans la liste **icône** , choisissez un fichier icône (*. ico*).

    **C#** &mdash; Près de la liste **icône** , choisissez le **\<Browse...>** bouton, puis accédez à l’emplacement du fichier icône souhaité.

## <a name="see-also"></a>Voir aussi

- [Page application, concepteur de projets (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Page application, concepteur de projets (C#)](../ide/reference/application-page-project-designer-csharp.md)
