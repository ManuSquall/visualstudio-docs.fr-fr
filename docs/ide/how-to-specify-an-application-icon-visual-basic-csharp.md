---
title: 'Procédure : Spécifier une icône d’application (Visual Basic, C#)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f2903821c0e0843de43f68d67cc64c344ab95e02
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62547778"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Procédure : Spécifier une icône d’application (Visual Basic, C#)

La propriété `Icon` d’un projet spécifie le fichier de l’icône (*.ico*) qui est affichée pour l’application compilée dans l’**Explorateur de fichiers** et dans la barre des tâches Windows.

La propriété `Icon` est accessible dans le volet **Application** du **Concepteur de projet**. Elle contient une liste des icônes qui ont été ajoutées à un projet comme ressources ou comme fichiers de contenu.

> [!NOTE]
> Après avoir défini la propriété Icon pour une application, vous pouvez également définir la propriété `Icon` de chaque **Fenêtre** ou **Formulaire** de l’application. Pour plus d'informations sur les icônes de fenêtre pour les applications autonomes Windows Presentation Foundation (WPF), consultez la propriété <xref:System.Windows.Window.Icon%2A>.

## <a name="to-specify-an-application-icon"></a>Pour spécifier une icône d'application

1. Dans l’**Explorateur de solutions**, choisissez un nœud de projet (pas le nœud **Solution**).

1. Dans la barre de menus, choisissez **Projet** > **Propriétés**.

1. Quand le **Concepteur de projet** apparaît, choisissez l’onglet **Application**.

1. **(Visual Basic)**&mdash;Dans la liste **Icône**, choisissez un fichier d’icône (*.ico*).

    **C#**&mdash;À côté de la liste **Icône**, choisissez le bouton **\<Parcourir...>**, puis accédez à l’emplacement du fichier icône souhaité.

## <a name="see-also"></a>Voir aussi

- [Application, page du Concepteur de projet (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Application, page du Concepteur de projet (C#)](../ide/reference/application-page-project-designer-csharp.md)