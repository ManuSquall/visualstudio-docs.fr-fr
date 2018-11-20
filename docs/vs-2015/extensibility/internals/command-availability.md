---
title: Commande disponibilité | Microsoft Docs
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
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b822f85a0eda7952db37f1479ce6e8c536589716
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773260"
---
# <a name="command-availability"></a>Disponibilité de commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le contexte de Visual Studio détermine les commandes qui sont disponibles. Le contexte peut changer selon le projet actuel, l’éditeur actuel, les VSPackages sont chargés et autres aspects de l’environnement de développement intégré (IDE).  
  
## <a name="command-contexts"></a>Contextes de commande  
 Les contextes de commande suivants sont les plus courantes.  
  
-   **IDE** commandes fournies par l’IDE sont toujours disponibles.  
  
-   **VSPackage** VSPackages peut définir lorsque les commandes sont à être affiché ou masqué.  
  
-   **Projet** commandes de projet s’affichent uniquement pour le projet sélectionné actuellement.  
  
-   **Éditeur** qu’un seul éditeur peut être actif à la fois. Commandes à partir de l’éditeur actif sont disponibles. Un éditeur travaille en étroite collaboration avec un service de langage. Le service de langage doit traiter ses commandes dans le contexte de l’éditeur associé.  
  
-   **Type de fichier** un éditeur peut charger plusieurs types de fichier. Les commandes disponibles peuvent varier selon le type de fichier.  
  
-   **La fenêtre active** la dernière fenêtre de document actif définit le contexte d’interface (UI) utilisateur pour les combinaisons de touches. Toutefois, une fenêtre outil qui a une table de clé de liaison qui ressemble au navigateur Web interne peut également définir le contexte d’interface utilisateur. Pour les fenêtres de document à plusieurs onglets tels que l’éditeur HTML, chaque onglet possède un contexte de commande autre GUID. Après avoir enregistré une fenêtre outil, il est toujours disponible sur le **vue** menu.  
  
-   **Contexte d’interface utilisateur** contextes d’interface utilisateur sont identifiées par les valeurs de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> de classe, par exemple, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> lorsque la solution est en cours de génération, ou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> lorsque le débogueur est actif. Plusieurs contextes d’interface utilisateur peuvent être actives en même temps.  
  
## <a name="defining-custom-context-guids"></a>Définition des GUID de contexte personnalisé  
 Si un contexte de la commande appropriée que GUID n’est pas déjà défini, vous pouvez définir un dans votre package Visual Studio et programmez ensuite qu’il soit actif ou inactif, en fonction des besoins pour contrôler la visibilité de vos commandes.  
  
1.  Enregistrez le GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (méthode).  
  
2.  Obtenir l’état d’un GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> (méthode).  
  
3.  Activer et désactiver les GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (méthode).  
  
    > [!CAUTION]
    >  Assurez-vous que votre VSPackage n’affecte pas les GUID de contexte existant, car d’autres packages VS dépendent les.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)   
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

