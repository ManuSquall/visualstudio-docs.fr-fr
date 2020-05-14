---
title: Extension et personnalisation des fenêtres d’outils (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76c094ec73a69baa46a5e8313dd26febd57e5887
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711817"
---
# <a name="extend-and-customize-tool-windows"></a>Étendre et personnaliser les fenêtres d’outils
Visual Studio fournit plusieurs types de fenêtres, par exemple des fenêtres d’outils, des fenêtres de documents et des fenêtres de dialogue. D’autres fenêtres telles que la fenêtre **propriétés,** la fenêtre **de sortie,** et la fenêtre **task List,** sont des types de fenêtres d’outils.

## <a name="tool-windows"></a>Fenêtres d’outil
 Les fenêtres d’outils Visual Studio sont généralement des fenêtres de lecture seulement qui ne sont pas basées sur des fichiers. En cela, elles diffèrent des fenêtres de document qui affichent des fichiers en mode lecture-écriture. La **Boîte à outils**, l’ **Explorateur de solutions**, la fenêtre **Propriétés** et le **Navigateur web** sont des exemples de fenêtres Outil.

 Pour savoir comment créer une fenêtre d’outil simple, voir [Ajouter une fenêtre d’outil](../extensibility/adding-a-tool-window.md).

 Pour enregistrer une fenêtre d’outil avec Visual Studio, consultez [enregistrez une fenêtre d’outil](../extensibility/registering-a-tool-window.md).

 Les fenêtres Outil sont par défaut à instance unique, ce qui signifie que seule une instance de la fenêtre Outil peut être ouverte à la fois. Quand une fenêtre Outil à instance unique est ouverte, elle le reste jusqu’à la fermeture de l’IDE. Lorsque vous fermez une fenêtre d’outil à instance unique, seule sa visibilité change. Vous pouvez également créer des fenêtres Outil multi-instances, ce qui vous permet d’ouvrir simultanément plusieurs instances de la fenêtre. Voir [Créer une fenêtre d’outil multi-instances](../extensibility/creating-a-multi-instance-tool-window.md) pour plus d’informations.

 Les fenêtres d’outils peuvent être *dynamiques,* ce qui signifie qu’elles sont visibles chaque fois que leur contexte d’interface utilisateur connexe s’applique. La visibilité automatique peut permettre de réduire l’encombrement des fenêtres dans l’IDE. Pour plus d’informations, voir [Ouvrez une fenêtre d’outil dynamique](../extensibility/opening-a-dynamic-tool-window.md).

 Dans le frame de document, les fenêtres Outils peuvent être des fenêtres ancrées,  flottantes ou avec onglets. Le frame de fenêtre Outil, fourni par l’IDE, permet de contrôler la taille, l’emplacement, l’état d’ancrage et d’autres propriétés persistantes. Le volet de la fenêtre Outil affiche le contenu. La taille et l’emplacement par défaut s’appliquent uniquement à la première ouverture de la fenêtre Outil ; après cela, l’état de la fenêtre Outil est rendu persistant.

 Les volets de la fenêtre Outil peuvent héberger des contrôles utilisateur WPF et prendre en charge des barres d’outils. Vous pouvez substituer la propriété <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> pour retourner le handle du contrôle hébergé.

 Vous pouvez ajouter de nombreuses fonctionnalités différentes aux fenêtres d’outils. Par exemple, vous pouvez ajouter une barre d’outils : [Ajoutez une barre d’outils à une fenêtre d’outil](../extensibility/adding-a-toolbar-to-a-tool-window.md) ou à un menu raccourci : [Ajoutez un menu raccourci dans une fenêtre d’outil.](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md) Vous pouvez ajouter un contrôle de recherche qui vous permet de rechercher des éléments à l’intérieur de votre fenêtre d’outil : [Ajoutez une recherche à une fenêtre d’outil.](../extensibility/adding-search-to-a-tool-window.md)

 Vous pouvez vous abonner à des événements de fenêtre d’outil : [Abonnez-vous à un événement](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Étendre les fenêtres d’outils existantes
 Vous pouvez ajouter des informations sur votre fenêtre d’outil à une nouvelle page **Options** et un nouveau paramètre sur la page **Propriétés,** écrire à la **liste de tâches** et aux fenêtres de **sortie.** Pour plus d’informations, consultez [les fenêtres Extend the Properties, Task List, Output et Options](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Boîtes de dialogue modal
 Dans une extension Visual Studio, vous devez créer des <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>boîtes de dialogue modal en les dérivant de , ce qui vous permet de les contrôler et le reste de l’interface utilisateur. Pour plus d’informations, voir [Créer et gérer les boîtes de dialogue modal](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Voir aussi
- [Créer une extension avec une fenêtre d’outils](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Étendre les projets](../extensibility/extending-projects.md)
- [Étendre les solutions](../extensibility/extending-solutions.md)
