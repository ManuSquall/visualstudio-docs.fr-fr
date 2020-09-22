---
title: Disponibilité des commandes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f060f6c49fc02c75b3fe9f792133c9ee88c6d56c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839313"
---
# <a name="command-availability"></a>Disponibilité de commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le contexte de Visual Studio détermine les commandes qui sont disponibles. Le contexte peut changer en fonction du projet actuel, de l’éditeur actuel, des VSPackages chargés et d’autres aspects de l’environnement de développement intégré (IDE).  
  
## <a name="command-contexts"></a>Contextes de commande  
 Les contextes de commande suivants sont les plus courants.  
  
- **IDE** Les commandes fournies par l’IDE sont toujours disponibles.  
  
- **VSPackage** Les VSPackages peuvent définir le moment où les commandes doivent être affichées ou masquées.  
  
- **Projet** Les commandes de projet s’affichent uniquement pour le projet actuellement sélectionné.  
  
- **Éditeur** Un seul éditeur peut être actif à la fois. Les commandes de l’éditeur actif sont disponibles. Un éditeur travaille en étroite collaboration avec un service de langage. Le service de langage doit traiter ses commandes dans le contexte de l’éditeur associé.  
  
- **Type de fichier** Un éditeur peut charger plusieurs types de fichiers. Les commandes disponibles peuvent changer en fonction du type de fichier.  
  
- **Fenêtre active** La dernière fenêtre de document active définit le contexte de l’interface utilisateur (IU) pour les combinaisons de touches. Toutefois, une fenêtre outil qui a une table de liaison de clés qui ressemble au navigateur Web interne peut également définir le contexte de l’interface utilisateur. Pour les fenêtres de document à plusieurs onglets telles que l’éditeur HTML, chaque onglet possède un GUID de contexte de commande différent. Une fois qu’une fenêtre outil est inscrite, elle est toujours disponible dans le menu **affichage** .  
  
- **Contexte de l’interface utilisateur** Les contextes d’interface utilisateur sont identifiés par les valeurs de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> classe, par exemple, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> lorsque la solution est en cours de génération, ou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> lorsque le débogueur est actif. Plusieurs contextes d’interface utilisateur peuvent être actifs en même temps.  
  
## <a name="defining-custom-context-guids"></a>Définition de GUID de contexte personnalisés  
 Si aucun GUID de contexte de commande approprié n’est déjà défini, vous pouvez en définir un dans votre VSPackage, puis le programmer pour qu’il soit actif ou inactif en fonction des besoins afin de contrôler la visibilité de vos commandes.  
  
1. Enregistrez les GUID de contexte en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> méthode.  
  
2. Obtenir l’état d’un GUID de contexte en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> méthode.  
  
3. Activez et désactivez les GUID de contexte en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> méthode.  
  
    > [!CAUTION]
    > Assurez-vous que votre VSPackage n’affecte pas les GUID de contexte existants, car d’autres VSPackages peuvent en dépendre.  
  
## <a name="see-also"></a>Voir aussi  
 [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)   
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
