---
title: Extension et personnalisation de Windows de l’outil | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 591351f41d0cd85de92836990e8d8523258f3d33
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199938"
---
# <a name="extending-and-customizing-tool-windows"></a>Extension et personnalisation des fenêtres d’outils
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio fournit plusieurs types différents de windows, par exemple les fenêtres Outil, les fenêtres de document et boîte de dialogue windows. Autres fenêtres telles que la fenêtre Propriétés, la fenêtre Sortie et la fenêtre liste des tâches, sont des types de fenêtres Outil.  
  
## <a name="tool-windows"></a>Fenêtres d'outils  
 Fenêtres Outil Visual Studio sont généralement en lecture seule windows qui ne sont pas basés sur fichier. En cela, elles diffèrent des fenêtres de document qui affichent des fichiers en mode lecture-écriture. La **Boîte à outils**, l’ **Explorateur de solutions**, la fenêtre **Propriétés** et le **Navigateur web** sont des exemples de fenêtres Outil.  
  
 Pour savoir comment créer une fenêtre outil simple, consultez [Ajout d’une fenêtre outil](../extensibility/adding-a-tool-window.md).  
  
 Pour inscrire une fenêtre outil avec Visual Studio, consultez [l’inscription d’une fenêtre outil](../extensibility/registering-a-tool-window.md).  
  
 Les fenêtres Outil sont par défaut à instance unique, ce qui signifie que seule une instance de la fenêtre Outil peut être ouverte à la fois. Quand une fenêtre Outil à instance unique est ouverte, elle le reste jusqu’à la fermeture de l’IDE. Lorsque vous fermez une fenêtre outil à instance unique, seule sa visibilité change. Vous pouvez également créer des fenêtres Outil multi-instances, ce qui vous permet d’ouvrir simultanément plusieurs instances de la fenêtre. Consultez [création d’une fenêtre d’outil multi-instance](../extensibility/creating-a-multi-instance-tool-window.md) pour plus d’informations.  
  
 Fenêtres Outil peuvent être *dynamique*, ce qui signifie qu’ils sont visibles dès que leur contexte de l’interface utilisateur associée s’applique. La visibilité automatique peut permettre de réduire l’encombrement des fenêtres dans l’IDE. Pour plus d’informations, consultez [ouvrant une fenêtre d’outil dynamique](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Dans le frame de document, les fenêtres Outils peuvent être des fenêtres ancrées,  flottantes ou avec onglets. Le frame de fenêtre Outil, fourni par l’IDE, permet de contrôler la taille, l’emplacement, l’état d’ancrage et d’autres propriétés persistantes. Le volet de la fenêtre Outil affiche le contenu. La taille et l’emplacement par défaut s’appliquent uniquement à la première ouverture de la fenêtre Outil ; après cela, l’état de la fenêtre Outil est rendu persistant.  
  
 Les volets de la fenêtre Outil peuvent héberger des contrôles utilisateur WPF et prendre en charge des barres d’outils. Vous pouvez substituer la propriété <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> pour retourner le handle du contrôle hébergé.  
  
 Vous pouvez ajouter de nombreuses fonctionnalités différentes aux fenêtres Outil. Par exemple, vous pouvez ajouter une barre d’outils : [Ajout d’une barre d’outils à une fenêtre outil](../extensibility/adding-a-toolbar-to-a-tool-window.md) ou un menu contextuel : [Ajout d’un Menu contextuel dans une fenêtre outil](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Vous pouvez ajouter un contrôle de recherche qui vous permet de rechercher des éléments à l’intérieur de votre fenêtre outil : [Ajout d’une recherche à une fenêtre outil](../extensibility/adding-search-to-a-tool-window.md).  
  
 Vous pouvez vous abonner aux événements de fenêtre d’outil : [abonnement à un événement](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Extension Windows outil existant  
 Vous pouvez ajouter des informations relatives à votre fenêtre outil vers un nouveau **Options** page et un nouveau paramètre sur le **propriétés** page, écrire dans le **liste des tâches** et **sortie**  windows. Pour plus d’informations, consultez [étendre les propriétés, liste des tâches, sortie et Options Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) et [étendre les propriétés, liste des tâches, sortie et Options Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Boîtes de dialogue modales  
 Dans une extension Visual Studio, vous devez créer des boîtes de dialogue modale en les dérivant de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, qui vous permet de contrôler les et le reste de l’interface utilisateur. Pour plus d’informations, consultez . [Créer et gérer des boîtes de dialogue modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md)

