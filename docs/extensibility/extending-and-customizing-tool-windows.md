---
title: Étendre et de personnaliser des fenêtres Outil | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ef4f656ed7b7ab7facbcfb470fca98327276cce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129233"
---
# <a name="extending-and-customizing-tool-windows"></a>Étendre et personnaliser des fenêtres Outil
Visual Studio fournit plusieurs types différents de windows, par exemple les fenêtres d’outil, les fenêtres de document et les boîtes de dialogue. Autres fenêtres telles que la fenêtre Propriétés, la fenêtre Sortie et la fenêtre liste des tâches, sont des types de fenêtres Outil.  
  
## <a name="tool-windows"></a>Fenêtres d'outils  
 Fenêtres Outil Visual Studio sont des fenêtres généralement en lecture seule qui ne sont pas basées sur le fichier. En cela, elles diffèrent des fenêtres de document qui affichent des fichiers en mode lecture-écriture. La **Boîte à outils**, l’ **Explorateur de solutions**, la fenêtre **Propriétés** et le **Navigateur web** sont des exemples de fenêtres Outil.  
  
 Pour savoir comment créer une fenêtre outil simple, consultez [Ajout d’une fenêtre outil](../extensibility/adding-a-tool-window.md).  
  
 Pour inscrire une fenêtre outil avec Visual Studio, consultez [l’inscription d’une fenêtre outil](../extensibility/registering-a-tool-window.md).  
  
 Les fenêtres Outil sont par défaut à instance unique, ce qui signifie que seule une instance de la fenêtre Outil peut être ouverte à la fois. Quand une fenêtre Outil à instance unique est ouverte, elle le reste jusqu’à la fermeture de l’IDE. Lorsque vous fermez une fenêtre outil à instance unique, seule sa visibilité change. Vous pouvez également créer des fenêtres Outil multi-instances, ce qui vous permet d’ouvrir simultanément plusieurs instances de la fenêtre. Consultez [création d’une fenêtre d’outil multi-instance](../extensibility/creating-a-multi-instance-tool-window.md) pour plus d’informations.  
  
 Les fenêtres Outil peuvent être *dynamique*, ce qui signifie qu’ils sont visibles chaque fois que leur contexte de l’interface utilisateur associée s’applique. La visibilité automatique peut permettre de réduire l’encombrement des fenêtres dans l’IDE. Pour plus d’informations, consultez [ouverture d’une fenêtre outil dynamique](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Dans le frame de document, les fenêtres Outils peuvent être des fenêtres ancrées,  flottantes ou avec onglets. Le frame de fenêtre Outil, fourni par l’IDE, permet de contrôler la taille, l’emplacement, l’état d’ancrage et d’autres propriétés persistantes. Le volet de la fenêtre Outil affiche le contenu. La taille et l’emplacement par défaut s’appliquent uniquement à la première ouverture de la fenêtre Outil ; après cela, l’état de la fenêtre Outil est rendu persistant.  
  
 Les volets de la fenêtre Outil peuvent héberger des contrôles utilisateur WPF et prendre en charge des barres d’outils. Vous pouvez remplacer le <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> propriété à retourner le handle du contrôle hébergé.  
  
 Vous pouvez ajouter de nombreuses fonctionnalités différentes pour les fenêtres Outil. Par exemple, vous pouvez ajouter une barre d’outils : [Ajout d’une barre d’outils à une fenêtre outil](../extensibility/adding-a-toolbar-to-a-tool-window.md) ou un menu contextuel : [Ajout d’un Menu contextuel dans une fenêtre outil](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Vous pouvez ajouter un contrôle de recherche qui vous permet de rechercher des éléments à l’intérieur de votre fenêtre outil : [Ajout d’une recherche dans une fenêtre outil](../extensibility/adding-search-to-a-tool-window.md).  
  
 Vous pouvez vous abonner aux événements de fenêtre outil : [s’abonner à un événement](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Extension des fenêtres Outil existantes  
 Vous pouvez ajouter des informations à propos de votre fenêtre outil vers un nouveau **Options** page et un nouveau paramètre sur le **propriétés** page, écrire dans le **liste des tâches** et **sortie**  windows. Pour plus d’informations, consultez [étendre les Options de Windows, liste des tâches, de sortie et propriétés](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) et [extension de propriétés, de liste des tâches, de sortie et d’Options Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Boîtes de dialogue modales  
 Dans une extension Visual Studio vous devez créer des boîtes de dialogue modales en les dérivant de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, qui vous permet de contrôler les et le reste de l’interface utilisateur. Pour plus d’informations, consultez . [Créer et gérer des boîtes de dialogue modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md)