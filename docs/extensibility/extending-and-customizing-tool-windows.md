---
title: Extension et personnalisation des fenêtres outil | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711817"
---
# <a name="extend-and-customize-tool-windows"></a>Étendre et personnaliser les fenêtres outil
Visual Studio fournit différents types de fenêtres, par exemple des fenêtres outil, des fenêtres de document et des fenêtres de dialogue. D’autres fenêtres, telles que la fenêtre **Propriétés** , la fenêtre **sortie** et la fenêtre de **liste des tâches** , sont des types de fenêtres outil.

## <a name="tool-windows"></a>Fenêtres d’outil
 Les fenêtres Outil Visual Studio sont généralement des fenêtres en lecture seule qui ne sont pas basées sur des fichiers. En cela, elles diffèrent des fenêtres de document qui affichent des fichiers en mode lecture-écriture. La **Boîte à outils**, l’ **Explorateur de solutions**, la fenêtre **Propriétés** et le **Navigateur web** sont des exemples de fenêtres Outil.

 Pour savoir comment créer une fenêtre outil simple, consultez [Ajouter une fenêtre outil](../extensibility/adding-a-tool-window.md).

 Pour inscrire une fenêtre outil dans Visual Studio, consultez [inscrire une fenêtre outil](../extensibility/registering-a-tool-window.md).

 Les fenêtres Outil sont par défaut à instance unique, ce qui signifie que seule une instance de la fenêtre Outil peut être ouverte à la fois. Quand une fenêtre Outil à instance unique est ouverte, elle le reste jusqu’à la fermeture de l’IDE. Lorsque vous fermez une fenêtre outil à instance unique, seule sa visibilité change. Vous pouvez également créer des fenêtres Outil multi-instances, ce qui vous permet d’ouvrir simultanément plusieurs instances de la fenêtre. Pour plus d’informations, consultez [créer une fenêtre outil à instances multiples](../extensibility/creating-a-multi-instance-tool-window.md) .

 Les fenêtres Outil peuvent être *dynamiques*, ce qui signifie qu’elles sont visibles chaque fois que leur contexte d’interface utilisateur associé s’applique. La visibilité automatique peut permettre de réduire l’encombrement des fenêtres dans l’IDE. Pour plus d’informations, consultez [ouvrir une fenêtre outil dynamique](../extensibility/opening-a-dynamic-tool-window.md).

 Dans le frame de document, les fenêtres Outils peuvent être des fenêtres ancrées,  flottantes ou avec onglets. Le frame de fenêtre Outil, fourni par l’IDE, permet de contrôler la taille, l’emplacement, l’état d’ancrage et d’autres propriétés persistantes. Le volet de la fenêtre Outil affiche le contenu. La taille et l’emplacement par défaut s’appliquent uniquement à la première ouverture de la fenêtre Outil ; après cela, l’état de la fenêtre Outil est rendu persistant.

 Les volets de la fenêtre Outil peuvent héberger des contrôles utilisateur WPF et prendre en charge des barres d’outils. Vous pouvez substituer la propriété <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> pour retourner le handle du contrôle hébergé.

 Vous pouvez ajouter de nombreuses fonctionnalités différentes aux fenêtres outil. Par exemple, vous pouvez ajouter une barre d’outils : [Ajouter une barre d’outils à une fenêtre outil ou à](../extensibility/adding-a-toolbar-to-a-tool-window.md) un menu contextuel : [Ajouter un menu contextuel dans une fenêtre outil](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Vous pouvez ajouter un contrôle de recherche qui vous permet de rechercher des éléments dans la fenêtre outil : [Ajouter une recherche à une fenêtre outil](../extensibility/adding-search-to-a-tool-window.md).

 Vous pouvez vous abonner aux événements de la fenêtre outil : [s’abonner à un événement](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Étendre les fenêtres outil existantes
 Vous pouvez ajouter des informations sur la fenêtre outil à une nouvelle page d' **options** et un nouveau paramètre dans la page **Propriétés** , écrire dans les fenêtres de **liste des tâches** et de **sortie** . Pour plus d’informations, consultez [étendre les fenêtres propriétés, liste des tâches, sortie et options](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Boîtes de dialogue modales
 Dans une extension Visual Studio, vous devez créer des boîtes de dialogue modales en les dérivant de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> , ce qui vous permet de les contrôler et le reste de l’interface utilisateur. Pour plus d’informations, consultez [créer et gérer des boîtes de dialogue modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Voir aussi
- [Créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Étendre des projets](../extensibility/extending-projects.md)
- [Étendre les solutions](../extensibility/extending-solutions.md)
