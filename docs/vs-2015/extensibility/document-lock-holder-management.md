---
title: Gestion du détenteur de verrou de document | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0cf3e532a7a20be746405a7c5f90bb2c345a36cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505635"
---
# <a name="document-lock-holder-management"></a>Gestion du détenteur de verrouillage du document
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [gestion du détenteur de verrou de Document](https://docs.microsoft.com/visualstudio/extensibility/document-lock-holder-management).  
  
La Table de Document en cours d’exécution (RDT) gère un nombre de documents ouverts et tous les verrous de modification que sont-ils. Vous pouvez placer un verrou de modification sur un document dans le RDT lorsqu’il est par programme modifié en arrière-plan sans que l’utilisateur de voir un document ouvert dans une fenêtre de document. Cette fonctionnalité est souvent utilisée par les concepteurs qui modifient plusieurs fichiers via une interface utilisateur graphique.  
  
## <a name="document-lock-holder-scenarios"></a>Scénarios de détenteur de verrouillage de document  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Fichier « a » a une dépendance sur le fichier « b »  
 Prenons le cas où vous implémentez un éditeur standard « A » pour le type de fichier « a » et chaque fichier de type « a » a une référence à (ou la dépendance sur) un fichier de type « b ». Il existe un éditeur standard « B » pour les fichiers de type « b ». Lors de l’éditeur « A » ouvre le fichier « a » il récupère la référence au fichier correspondant « b ». Fichier « b » n’est pas affiché, mais « A » de l’éditeur peut la modifier. Éditeur de « A » Obtient une référence aux données de document du fichier « b » à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> méthode et gère également un verrou de modification sur le fichier « b ». Une fois que l’éditeur « A » est terminé la modification de fichier « b », vous pouvez diminuer le verrou de modification compter sur le fichier « b » en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> (méthode). Vous pouvez omettre cette étape si vous aviez appelé le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> méthode avec le paramètre `dwRDTLockType` défini sur <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Le fichier « b » est ouvert par un autre éditeur  
 Dans le cas où le fichier « b » est déjà ouverte par éditeur « B » lors de l’éditeur « A » tente d’ouvrir, il existe deux scénarios distincts pour gérer :  
  
-   Si le fichier « b » est ouvert dans un éditeur compatible, vous devez disposer l’éditeur « A » inscrire un verrou de modification de document sur le fichier « b » à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> (méthode). Une fois que votre éditeur de « A » est terminé fichier modification « b », désinscrire le document modifier le verrou à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> (méthode).  
  
-   Si le fichier « b » est ouvert de manière incompatible, vous pouvez laisser l’ouverture de tentative de fichier « b » par « A » échouent, ou vous pouvez laisser la vue associée à l’éditeur « A » est partiellement ouvre et affiche un message d’erreur de l’éditeur. Le message d’erreur doit indiquer à l’utilisateur de fermer le fichier « b » dans l’éditeur incompatible et puis rouvrez le fichier « a » à l’aide de l’éditeur « A ». Vous pouvez également implémenter le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> pour inviter l’utilisateur pour fermer le fichier « b » est ouvert dans l’éditeur incompatible. Si l’utilisateur ferme le fichier « b », l’ouverture du fichier « a » dans « A » l’éditeur se poursuit normalement.  
  
## <a name="additional-document-edit-lock-considerations"></a>Considérations de verrou modifier Document supplémentaires  
 Vous obtenez un comportement différent si l’éditeur « A » est le seul éditeur qui a un document à modifier le verrou sur le fichier « b » que vous le feriez si l’éditeur « B » conserve également un document modifier un verrou sur le fichier « b ». Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], **Concepteur de classes** est un exemple d’un concepteur visuel qui ne contient pas d’un verrou de modification sur le fichier de code associé. Autrement dit, si l’utilisateur a un diagramme de classes ouvert en mode design et ouvrir le fichier de code associé en même temps, et si l’utilisateur modifie le fichier de code, mais ne pas enregistre les modifications, les modifications sont également perdues dans le fichier de diagramme (.cd) de classe. Si le **Concepteur de classes** a le document uniquement modifier un verrou sur le fichier de code, l’utilisateur n’est pas invité à enregistrer les modifications lors de la fermeture du fichier de code. L’IDE invite l’utilisateur à enregistrer les modifications uniquement une fois que l’utilisateur ferme le **Concepteur de classes**. Les modifications enregistrées sont répercutées dans les deux fichiers. Si les deux le **Concepteur de classes** et l’éditeur de fichier de code maintenu verrous de modification de document sur le fichier de code, puis l’utilisateur est invité à enregistrer lors de la fermeture de l’écran ou le fichier de code. À ce stade, les modifications enregistrées sont répercutées dans le formulaire et le fichier de code. Pour plus d’informations sur les diagrammes de classes, consultez [diagrammes de classes (Concepteur de classes)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Notez que si vous avez besoin de placer un verrou de modification sur un document pour un non éditeur, vous devez implémenter le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interface.  
  
 Nombre de fois où un concepteur d’interface utilisateur qui modifie par programmation des fichiers de code modifie plusieurs fichiers. Dans ce cas le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> méthode gère l’enregistrement d’un ou plusieurs documents par le biais de la **voulez-vous enregistrer les modifications apportées aux éléments suivants ?** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Table de Document en cours d’exécution](../extensibility/internals/running-document-table.md)   
 [Persistance et table de document en cours d’exécution](../extensibility/internals/persistence-and-the-running-document-table.md)

