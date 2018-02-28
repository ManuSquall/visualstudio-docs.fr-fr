---
title: "Gestion de détenteur du verrou des documents | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - document locking
ms.assetid: fa1ce513-eb7d-42bc-b6e8-cb2433d051d5
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: df782cd974adcd589824e8a47cd0249842bd8d48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="document-lock-holder-management"></a>Gestion du détenteur du verrouillage du document
Un décompte des documents ouverts et tous les verrous de modification de que disposent la Table de Document en cours d’exécution (r & DT). Vous pouvez placer un verrou de modification d’un document dans la r & DT lorsqu’il est par programme modifié en arrière-plan sans que l’utilisateur de voir un document ouvert dans une fenêtre de document. Cette fonctionnalité est souvent utilisée par les concepteurs qui modifient plusieurs fichiers via une interface utilisateur graphique.  
  
## <a name="document-lock-holder-scenarios"></a>Scénarios de support de verrouillage de document  
  
### <a name="file-a-has-a-dependence-on-file-b"></a>Fichier « a » une dépendance sur le fichier a « b »  
 Prenons le cas dans lequel vous implémentez un éditeur standard « A » pour le type de fichier « a » et chaque fichier de type « a » a une référence à (ou vis-à-vis) un fichier de type « b ». Il existe un éditeur standard « B » pour les fichiers de type « b ». Lors de l’éditeur « A » ouvre le fichier « a » il récupère la référence au fichier correspondant « b ». Le fichier « b » n’est pas affiché, mais « A » de l’éditeur peut le modifier. Éditeur de « A » Obtient une référence aux données de document du fichier « b » à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> méthode et gère également un verrou de modification sur le fichier « b ». Une fois que l’éditeur « A » est terminé la modification de fichier « b », vous pouvez décrémenter le verrou de modification compter sur le fichier « b » en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> (méthode). Vous pouvez omettre cette étape si vous aviez appelé le <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> méthode avec le paramètre `dwRDTLockType` la valeur <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.  
  
### <a name="file-b-is-opened-by-a-different-editor"></a>Le fichier « b » est ouvert par un autre éditeur  
 Dans le cas où le fichier « b » est déjà ouverte par l’éditeur « B » lorsque « A » de l’éditeur tente d’ouvrir, il existe deux scénarios distincts pour gérer :  
  
-   Si le fichier « b » est ouvert dans un éditeur compatible, l’éditeur « A » doit avoir inscrire un verrou de modification de document sur le fichier « b » à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> (méthode). Une fois que votre éditeur de « A » est terminé fichier modification « b », désinscrire le document de modifier le verrou à l’aide du <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnregisterDocumentLockHolder%2A> (méthode).  
  
-   Si le fichier « b » est ouvert de manière incompatible, vous pouvez laisser la tentative lors de l’ouverture du fichier « b » par « A » échouent, ou vous pouvez laisser la vue associée à l’éditeur « A » partiellement ouvre et affiche un message d’erreur de l’éditeur. Le message d’erreur doit indiquer à l’utilisateur de fermer le fichier « b » dans l’éditeur incompatible et puis rouvrez le fichier « a » à l’aide de l’éditeur « A ». Vous pouvez également implémenter la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable2.QueryCloseRunningDocument%2A> pour inviter l’utilisateur à fermer le fichier « b » qui est ouvert dans l’éditeur incompatible. Si l’utilisateur ferme le fichier « b », l’ouverture du fichier « a » en « A » l’éditeur se poursuit normalement.  
  
## <a name="additional-document-edit-lock-considerations"></a>Considérations de verrouillage modifier documents supplémentaires  
 Vous obtenez un comportement différent si l’éditeur « A » est le seul éditeur qui a un document à modifier le verrou sur le fichier « b » que vous le feriez si l’éditeur « B » conserve également un document de modifier un verrou sur le fichier « b ». Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], **le Concepteur de classes** est un exemple d’un concepteur visuel qui ne possède pas un verrou de modification du fichier de code associé. Autrement dit, si l’utilisateur a un diagramme de classes ouvert en mode design et ouvrir le fichier de code associé en même temps, et si l’utilisateur modifie le fichier de code, mais ne pas enregistre les modifications, les modifications sont également perdues dans le fichier de diagramme (.cd). Si le **le Concepteur de classes** est le seul document modifier un verrou sur le fichier de code, l’utilisateur n’est pas invité à enregistrer les modifications lors de la fermeture du fichier de code. L’IDE demande à l’utilisateur pour enregistrer les modifications uniquement une fois que l’utilisateur ferme le **le Concepteur de classes**. Les modifications enregistrées sont répercutées dans les deux fichiers. Si les deux le **le Concepteur de classes** et l’éditeur de fichier de code maintenu verrous de modification de document sur le fichier de code, puis l’utilisateur est invité à enregistrer lorsque vous fermez le fichier de code ou de l’écran. À ce stade, les modifications enregistrées sont répercutées dans le formulaire et le fichier de code. Pour plus d’informations sur les diagrammes de classes, consultez [utilisation des diagrammes de classes (Concepteur de classes)](../ide/working-with-class-diagrams-class-designer.md).  
  
 Notez que si vous devez placer un verrou de modification d’un document pour un éditeur-non, vous devez implémenter la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interface.  
  
 Nombre de fois où un interface utilisateur concepteur qui modifie les fichiers de code par programmation apporte des modifications à plusieurs fichiers. Dans ce cas le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell2.SaveItemsViaDlg%2A> méthode gère l’enregistrement d’un ou plusieurs documents à l’aide de la **vous souhaitez enregistrer les modifications apportées aux éléments suivants ?** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Table de Document en cours d’exécution](../extensibility/internals/running-document-table.md)   
 [Persistance et table de document en cours d’exécution](../extensibility/internals/persistence-and-the-running-document-table.md)